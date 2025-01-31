# Hierarchical Sub-event Extraction

This repository present contains the code for the 2022 CIKM submission Extracting Semantic Sub-event Representations through Hierarchical Zero-shot Question Answering.

### Steps

python preprocessing.py 
To replicate paper results, run steps as follows.

* Run [MWDumper](https://www.mediawiki.org/wiki/Manual:MWDumper) to get Wikipedia articles of events in .ndjson file format.
* Run ```subevents/data_download-sh``` to prepare Wikidata and Dbpedia dumps and redirects.
* Run ```subevents/create_shelves.py``` to assure quick access to the dumps.  
* Set your project path in the ```config.ini```. 
* Run ```prepare_data.py``` to prepare and process data for event type prediction. 
* Run ```event_type_detection.sh``` to get predicted ACE-ontology event types on the data. This can take quite a while, the intermediate results will be stored in the data/intermediate_results folder. 
* Run ```merge_predictions.py``` to get the final results of ```event_type_detection.sh```.

#### Evaluation with Unlinked Sub-events
* Run ```main.py``` to extract events from Wikipedia articles of events given predicted ACE-ontology event types. The results will be stored in evaluation/unlinked_sub-events folder



#### Evaluation with Linked Sub-events
* Run ```prepare_groundtruth.py``` to prepare prediction and evaluation on linked sub-events.
* Run ```linked_event_evaluation.py``` to run the baselines and our approach on the groundtruth data. The final evaluation results as described in the paper will be created in the evaluation/linked_sub-events/results.txt file.


#### Extra
* Check ```notebook/wikidata_extraction.ipynb``` to see how we get Wikidata event classes, properties, constraints and statistics. 
* Check ```processing_sheets/process_sheets.py``` to see how we filter Wikidata event classes, get transitive statistics and propagate properties through Wikidata event classes.
