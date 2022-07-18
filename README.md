# Conversational Uptake
This repository contains data for the paper: 


Alic, S., Demszky, D., Mancenido, Z., Liu, J., Hill, H., & Jurafsky, D. (2022). [Computationally Identifying Funneling and Focusing Questions in Classroom Discourse](https://aclanthology.org/2022.bea-1.27.pdf). In _Proceedings of the 17th Workshop on Innovative Use of NLP for Building Educational Applications (BEA 2022)_ (pp. 224-233).


```
@inproceedings{alic2022computationally,
  title={Computationally Identifying Funneling and Focusing Questions in Classroom Discourse},
  author={Alic, Sterling and Demszky, Dorottya and Mancenido, Zid and Liu, Jing and Hill, Heather and Jurafsky, Dan},
  booktitle={Proceedings of the 17th Workshop on Innovative Use of NLP for Building Educational Applications (BEA 2022)},
  pages={224--233},
  year={2022}
}
```

## Annotated Funneling vs Focusing Dataset

The annotated dataset contains a sample of **2348 exchanges** extracted from a dataset of anonymized 4-5th grade US elementary math classroom transcripts collected by the [National Center for Teacher Effectiveness (NCTE)](https://cepr.harvard.edu/ncte) in New England schools between 2010-2013. These exchanges are turns by students (with at least 5 words), followed by teacher turns in a classroom conversation. 

Each exchange is coded for one of three categories, by three raters:
* 1 = funneling
* 2 = focusing
* 0 = neither (exchane is not related to math and/or it does not include a follow-up prompt)
The coding details are explained in greater detail in our paper.

There are two subsets of the data. In the `unfiltered` subset, we include all utterances, regardless of whether they have a follow-up prompt. Use the `filtered` set if you want to train a classifier to identify funneling and focusing questions among a dataset of various types of exchanges (not just questions). In the `filtered` subset, exchanges without a follow-up prompt have missing values. Use the `filtered` subset if you want to train a classifier to distinguish different question types within a dataset of questions. 

The data is in the comma-separated file `funneling_focusing_dataset.csv`.

The file includes the following columns:

* `obs_id`: Observation ID, mappable to unique transcripts in the NCTE dataset.
* `exchange_idx`: ID of the exchange within the transcript.
* `student_text`: Student utterance.
* `teacher_text`: Teacher utterance (following the utterance in `student_text`).
* `follow_up_unfiltered_majority`: The majority rating for funneling and focusing across the three raters -- unfiltered subset. Missing values indicate no majority label
* `follow_up_filtered_majority`: The majority rating for funneling and focusing across the three raters -- filtered subset. Missing values indicate no majority label.
* `follow_up_unfiltered_zscore`: Average of raters' z-scored judgments for funneling and focusing across the three raters -- unfiltered subset.  Missing values indicate no majority label
* `follow_up_filtered_zscore`: Average of raters' z-scored judgments for funneling and focusing across the three raters -- filtered subset. Missing values indicate that an exchange is not part of the filtered subset.

Each example can be **uniquely identified with the combination of the `obs_id` and `exchange_idx` columns**.


Please contact Dora (ddemszky@stanford.edu) for questions.
