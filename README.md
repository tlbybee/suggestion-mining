# Forum-Data-Mining

## Team
> Tingkai Zhang (tingkai4@illinois.edu)\
> Tyler Bybee (tbybee2@illinois.edu)\
> Faraz Ali (faraza3@illinois.edu)

## How To

### Train
> The trained model is already provided and can be used to run predictions on a csv file containing suggestions. An example file is available at `data/test.csv`
If you wish to train your own model, you can either take advantage of a GPU and set `"cuda_device": 0` param in your jsonnet config file to run on a GPU. 
It is currently set `"cuda_device": -1` and will train on CPU. This task can take very long to run, but can be cut short by reducing the number of epochs, currently set to 50.

**Requires Python 3**\
> `allennlp train --include-package=my_library cnn_bert.jsonnet -s ser_dir`

### Predict
>The trained model is already provided and can be used to run predictions on a csv file with the folliwing command:
`allennlp predict ser_dir/model.tar.gz data/test.csv --include-package=my_library --predictor=suggestion_mining`

The above command will output confident scores between 0 and 1 for a given text.

## Description

### What is the function of the tool

The model classifies a given text in the form of a csv file into a suggestion or not a suggestion.  The term 'suggestions' refers to the expressions of tips, advice, recommendations, etc. Specifically, we will focus on classifying whether a comment is a suggestion or not.

### Who will benefit from such a tool

For hotel companies, one such application could be used to extract room tips from online hotel reviews, which further will benefit future customers. Another example would be collecting suggestions for hotel improvements. In general, this would be greatly helpful to the service industry.
A suggestion mining component can extend the capabilities of traditional opinion mining systems, which can then cater to additional applications. Such systems can empower both public and private sectors by extracting the suggestions which are spontaneously expressed on various online platforms, enabling organizations to collect suggestions from much larger and varied sources of opinions than the traditional suggestion box or online feedback forms.

### Does this kind of tools already exist? If similar tools exist, how is your tool different from them? Would people care about the difference?

We will use Distilled BERT which smaller and faster than the existing tools. People will care about the difference because in production, smaller model and faster modeling serving will reduce the cost significantly.

### What techniques/algorithms will you use to develop the tool?

We anticipate that BERT and AllenNLP will effective for this task.

### Resources

SemEval 2019 Task 9 - SubTask A - Suggestion Mining from Online Reviews and Forums <https://competitions.codalab.org/competitions/19955#learn_the_details>

Suggestion Mining from Online Reviews using ULMFiT <https://arxiv.org/pdf/1904.09076.pdf>