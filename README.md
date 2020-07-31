# Preprocessing Text Python Package

#### Course Link: https://bit.ly/intro_nlp

This python package is prepared by YourName.

Install

`pip install git+https://github.com/laxmimerit/preprocess_kgptalkie.git`

Uninstall

`pip uninstall preprocess_kgptalkie`

#### How to use it for preprocessing
You have to have installed spacy and python3 to make it work.

```
import pandas as pd
import numpy as np
import preprocess_kgptalkie as ps

df = pd.read_csv('imdb_reviews.txt', sep = '\t', header = None)
df.columns = ['reviews', 'sentiment']

# These are series of preprocessing
df['reviews'] = df['reviews'].apply(lambda x: ps.cont_exp(x)) #you're -> you are; i'm -> i am
df['reviews'] = df['reviews'].apply(lambda x: ps.remove_emails(x))
df['reviews'] = df['reviews'].apply(lambda x: ps.remove_html_tags(x))
df['reviews'] = df['reviews'].apply(lambda x: ps.remove_urls(x))

df['reviews'] = df['reviews'].apply(lambda x: ps.remove_special_chars(x))
df['reviews'] = df['reviews'].apply(lambda x: ps.remove_accented_chars(x))
df['reviews'] = df['reviews'].apply(lambda x: ps.make_base(x)) #ran -> run, 
df['reviews'] = df['reviews'].apply(lambda x: ps.spelling_correction(x).raw_sentences[0]) #seplling -> spelling
```

Note: Avoid to use `make_base` and `spelling_correction` for very large dataset otherwise it might take hours to process.
