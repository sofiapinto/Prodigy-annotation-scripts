# Named Entity Recognition (NER) + Text Classification

**Annotation recipe** with a **NER** block and text **classification** block.

In the example below we have an annotation setup that receives short sentences (e.g. tweets) and the annotator can:
- highlight location, date/time and weather related tokens in weather related sentences;
- classify text as weather related (green/accept button), non-weather related (red/reject button) or click unsure (yellow/ignore button) otherwise.

The accept, reject and ignore buttons can also be used for a different purpose such as accepting/rejecting/ignoring the annotation in hand.

Notice that one can either click or use keyboard shortcuts to annotate.

![NER_classification_gif](https://github.com/sofiapinto/Prodigy-annotation-scripts/blob/main/gifs/prodigy_NER_class.gif)

## Files

* *annotation_setup.py*: the main file with the annotation setup, using a blocks recipe. Note that, a NER recipe could have been used instead;

* *annotation_javascript.js*: code to make the first NER label the default label.

* *annotation_instructions.html*: instructions on how to use the tool that can be checked by the annotator (by clicking the help button on the upper left hand side);

* *extract_annotations.py*: code to export the annotated data to a json file;

* *sentences.jsonl*: file with sentences to annotate (the input file needs to be of type jsonl);

## Instructions for the annotators

***To annotate*** 

1. Open a command line

2. cd to the folder where your code and data are stored, *e.g.*:

```
cd "Documents/GitHub/Prodigy-annotation-scripts/NER + classification"
```

3. Run the following command

```
python -m prodigy blocks-recipe annotated_sentences sentences.jsonl  -F annotation_setup.py
```
where *annotated_sentences* is the name of the database where the annotations will be stored.

5. Open http://localhost:8080/

6. Once you've finished annotating for the day, click save, close http://localhost:8080/, CRTL+C and close the command line.

***Once you have finished annotating ALL sentences***

1. Open a command line

2. cd to the folder where your code and data are stored, *e.g.*:

```
cd "Documents/GitHub/Prodigy-annotation-scripts/NER + classification"
```

3. Run the following command

```
python extract_annotations.py annotated_sentences annotated_sentences.json
```

4. A new file called *annotated_sentences.json* will be in your folder. 