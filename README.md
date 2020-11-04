# RedditScore
Package for performing Reddit-based text analysis

Includes:
- Document tokenizer with myriads of options, including Reddit- and Twitter-specific options
- Tools to build and tune the most popular text classification models without any hassle
- Functions to easily collect Reddit comments from Google BigQuery and Twitter data (including tweets beyond 3200 tweets limit)
- Instruments to help you build more efficient Reddit-based models and to obtain RedditScores
- Tools to use pre-built Reddit-based models to obtain RedditScores for your data

Full documentation and tutorials live here: http://redditscore.readthedocs.io

To install package:

	pip install git+https://github.com/polyankaglade/RedditScore.git

You will also need to install [spacy_russian_tokenizer](https://github.com/aatimofeev/spacy_russian_tokenizer)

	pip install git+https://github.com/aatimofeev/spacy_russian_tokenizer.git
	
Usage:
```python
from redditscore.tokenizer_rus import CrazyTokenizer as RusCrazyTokenizer
```

I would strongly recommend to pay attention to the tokenization of units and maybe do smth like
```python
from spacy.lang.char_classes import UNITS
units = UNITS.split('|')
for u in 'кг|г|мг|мкг|л|мл|гр'.split('|'):
    if u not in units:
        units.append(u)
print(units)

tokens = RusCrazyTokenizer(...).tokenize(text)
for token in tokens:
    if token in units:
        label = 'MEASURE'
```

or use the option for `extra_patterns`.
