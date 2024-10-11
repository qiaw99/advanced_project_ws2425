# Advanced Project WS2024/25

## Dataset creation
The dataset schema should be lists of JSON!

## List of operations: 
Given a user question, the LLM should output: 
1. Operation name 
2. Parameters in bracket

### Operations with single parameter

- predict(instance): do prediction 
- rationalize(instance): provide explanation in natural language for a given instance 
- feature_importance(instance): provide important words within a given instance 
- augmentation(instance): apply data augmentation on a given instance 
- similar(instance): given an instance find the most similar instance from the dataset 
- feedback(feedback): provide human feedback to the LLM 
- knowledge_edit(knowledge): edit the knowledge of the LLM 

The **keys of json** should be
- idx
- user_question
- operation_name (please find corresponding `operation_name` in each example file)
- custom_input

Example for `knowledge_edit`:
```json
[
    {
    	"idx": 0,
    	"user_question": "Can you edit the following knowledge: Ice is hot to the touch.",
        "operation_name": "knowledge_edit",
        "custom_input": "Ice is hot to the touch"
	}
]
```

### Operations with two parameters
- edit_prediction(instance, label): change the prediction of a given instance 
  - assume `label` is either `True` or `False` 
- preference_alignment(instance, preference1, preference2): given a question, provide preferred and not preferred answers to the LLM 

The **keys of json** should be
- idx
- user_question
- operation_name
- custom_input (for instance)
- content (for label/ preference1, preference2)

For `preference_alignment`, you could combine the `preference1` and `preference2` by concatenating (with `<s>`):
```python
content = f"{preference1}<s>{preference2}"
```
