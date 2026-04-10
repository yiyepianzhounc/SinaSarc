# SinaSarc Dataset

This dataset is derived from the paper ***A GAN and LLM-Driven Data Augmentation Framework for Dynamic Linguistic Pattern Modeling in Chinese Sarcasm Detection*.** 

It is a new Chinese sarcasm dataset for dynamic users' linguistic pattern modeling. The dataset contains 20,000 samples, including 10,000 sarcastic and 10,000 non-sarcastic instances.

## Collection of Raw Data

We first collected raw data, which is used to train the sarcastic comment generation module rather than the final detection model. We developed a web crawler to collect comments from Weibo across several topics, including *lifestyle, politics, entertainment, relationships and public incidents*. These topics usually involve trending events and contain diverse user opinions. In addition to the target comments, we also collected historical comments posted by the same users. 

After data collection, we removed noise such as advertisement links and HTML tags and standardized the text format. We have collected basic information such as *Comment Content, Label, Topic, Comment Hierarchy*.To incorporate user historical behavior, we extracted several behavioral features for each user, including *Comment Count, Topic Distribution, Sarcasm Rate, Comment Frequency, Reply Ratio*.

## Data Annotation

During the dataset annotation phase, we identified the key characteristics of sarcastic comments and established clear annotation guidelines to ensure both the dataset's quality and the accuracy of model training. Based on the definition of sarcasm and its linguistic features, we classified the characteristics of sarcastic comments as follows:

- **Dual Meaning:** Sarcasm involves a clear contrast between literal and intended meanings. Users often exploit this contrast to convey mockery or criticism. For example, "I really hope one day I can be like you, not caring about anything" may sound like admiration but actually criticizes the person's indifference to important matters. This is a typical example of sarcasm with dual meanings.
- **Emotional Reversal:** Sarcasm often conveys an emotion opposite to the literal meaning, such as using exaggerated praise to express criticism. For instance, "Your desk is astonishingly tidy, not a speck of dust, not even a scrap of paper" appears to compliment the tidiness, but in reality, it sarcastically implies that the desk lacks work materials, suggesting that the person may not be working at all.
- **Targeted and Aggressive:** Sarcasm often directs criticism at specific individuals, events, or phenomena. This criticism is not general; rather, it is sharply focused and aggressive. For example, "Every time I hear you express an opinion, I deeply understand the true meaning of fearless ignorance." This statement targets the person's opinion, mocking the ignorance in their words while they remain unaware.
- **Cultural and Contextual Dependence:** Sarcasm often depends on specific cultural contexts and background knowledge. Without this understanding, identifying the intent behind sarcasm can be challenging. For instance, "Based on your performance, I can't help but admire the spirit of 'jumping to action at the sound of a chicken.'" Originally, this phrase describes diligence, but in this context, it mocks someone who only acts in critical moments, typically remaining quite lazy.

Based on these characteristics, we developed a set of annotation guidelines to help annotators label the data accurately.

- **Context Analysis:** Annotators should consider the overall context of the comment, including the associated blog content, replies, and background information about the event. For instance, “After you complained about how boring the team-building was, I can only say, you are truly the soul of the team-building.” On the surface, this comment appears harmless, but it is actually a clear example of sarcasm, subtly accusing the person of being the reason the event was boring.
- **Overall Judgment:** Annotators should evaluate the entire comment to determine whether it exhibits sarcastic characteristics, rather than drawing conclusions based solely on individual parts of the comment. For example, “Your suggestion is just wonderful, if our goal is to make the company bankrupt immediately.” While this response initially seems to praise the suggestion, it ultimately criticizes its impracticality.
- **Ignoring Emotional Polarity:** The annotation process should focus solely on identifying sarcasm in the comment, without considering its sentiment polarity. Sarcasm can convey both positive or negative sentiments, and there is no direct correlation between sentiment polarity and sarcasm. For example, ``You are so humble, always attributing your success to luck." While this comment appears to praise humility, it actually criticizes the person for being insincere and excessively humble.
- **Ambiguous Annotation Handling:** To ensure the quality of annotations, we consider the opinions of all annotators in cases of ambiguity. If more than two-thirds of annotators agree on a specific label, the comment is classified according to the majority label. Otherwise, the data is discarded.

## Data Sample

| comment                                                      | label | topic                   | comment_hierarchy | comment_count | topic_distribution      | sarcasm_rate | comment_frequency | reply_ratio |
| :----------------------------------------------------------- | ----- | ----------------------- | ----------------- | ------------- | ----------------------- | ------------ | ----------------- | ----------- |
| 宁好会自我介绍，知道宁这乱吠 (You are very good at introducing yourself. I know you're barking loudly here.) | 1     | 情感 (Relationships)    | 1                 | 120           | 文娱 (Entertainment)    | 0.45         | 4                 | 0.77        |
| 人都不配当医生更不配 (He is not even fit to be a human being, let alone a doctor.) | 1     | 社会 (Public Incidents) | 1                 | 130           | 文娱 (Entertainment)    | 0.54         | 4.33              | 0.81        |
| 一带一路，共商共享共建 (Belt and Road, extensive consultation, joint contribution and shared benefits.) | 0     | 时政 (Politics)         | 0                 | 51            | 社会 (Public Incidents) | 0.35         | 1.7               | 0.18        |
| 啊，我希望我只是简单的小问题，我还打算过几天去拍个片子看看 (Oh, I hope it’s just something minor. I’m planning to get a scan in a few days anyway.) | 0     | 生活 (Lifestyle)        | 1                 | 48            | 情感 (Relationships)    | 0.4          | 1.6               | 0.17        |
| 啥时候唱跳一起来 (When will you combine singing and dancing in your performance?) | 0     | 文娱 (Entertainment)    | 0                 | 88            | 生活 (Lifestyle)        | 0.72         | 2.93              | 0.31        |

This dataset contains basic comment information and user historical behavior features. The basic comment information is defined as follows:

- **comment**: the content of the target comment 
- **label**: sentiment label, where 1 denotes sarcasm and 0 denotes non-sarcasm
- **topic**: the topic category to which the target comment belongs
- **comment_hierarchy**: the hierarchy of the target comment, where 0 denotes a top-level comment and 1 denotes a nested reply comment 

The user historical behavior features include: 

- **comment_count**: the total number of comments posted by the user within a certain period
- **topic_distribution**: the most frequent topic in the user’s historical comments
- **sarcasm_rate**: the proportion of sarcastic comments among all comments posted by the user
- **comment_frequency**: the average number of comments posted by the user per day
- **reply_ratio**: the proportion of nested reply comments among all comments posted by the user

## Contact

Please send an email to xiaohuluo@stu.scu.edu.cn to apply for access. Be sure to clearly state your affiliation, the person in charge, and how you intend to use our dataset.

## Citation
If you use this dataset in your research, please cite the preprint as follows (BibTeX format):

```bibtex
@misc{wang2026ganllmdrivendataaugmentation,
  title={A GAN and LLM-Driven Data Augmentation Framework for Dynamic Linguistic Pattern Modeling in Chinese Sarcasm Detection},
  author={Wenxian Wang and Xiaohu Luo and Junfeng Hao and Xiaoming Gu and Xingshu Chen and Zhu Wang and Haizhou Wang},
  year={2026},
  eprint={2604.08381},
  archivePrefix={arXiv},
  primaryClass={cs.CL}
}
