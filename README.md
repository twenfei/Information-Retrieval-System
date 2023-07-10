## Project Introduction

In this project, I would like to explore how we can build an information retrieval system which can accomplish a retrieval task where real-world commonsense reasoning ability is needed in this task.

Specifically, given an action language description as a query, our goal is to build a retrieval system which retrieves the relevant effect texts describing the effect states of the query action. For example, given the action quey “someone slices the potato”, “the potato becomes into pieces” is the textual information we are interested in retrieving.

In fact, this is an objectively hard task for existing retrieval system, as the query may not seem directly related to the ideal documents to retrieve. For example, “someone slices the potato” and “someone bakes the potato” are two very similar queries, but the desired retrieved effect texts can be completely
different. In this case, “someone slices the potato” emphasizes on the “in pieces, not as a whole” state, while “someone baked the potato” emphasizes on the “edible” or “is crispy” states. Recent advancement in large pre-trained language models has made such a retrieval system with reasoning ability possible. These large language models usually have some understanding of the physical world given its enormous model size and amount of pretraining data. Zero-shot prompting from these pre-trained LMs is proven to be one useful technique to generate new knowledge statements.

The main contribution of this project are the two proposed techniques to improve the baseline model performance of the retrieval task requiring commonsense reasoning. A query expansion technique using zero-shot prompting with ChatGPT is introduced and the pre-trained large language model extracted from the CLIP bi-encoder model is utilized to compute the similarity score as well.

Provided that the baseline `bm25` and `tf-idf` models barely outperforms the random performance model, the final model outperforms the random performance baseline model greatly in `nDCG@5` and `nDCG@10`, and achieves an `nDCG@5` score as high as 0.97.

For full context, please read the project report in this repo.

## How to run the "Interactive" section in the Jupyter Notebook

1. Run "Installing ChatGPT". You will be prompted to enter your password and email for OpenAI. Restart the runtime after installation once the installation is successful, otherwise it cannot import the packages properly.

2. Run "Load and Preprocess Action-Effect Data" and "Indexing action-effect dataset". Please DON'T RERUN "Improved Models". It might cause unwanted behavior.

3. Run "Interactive" part. If everything above runs successfully, you should be able to the retrievd results.

NOTE: Unfortunately, I cannot test out the Interactive part since my OpenAI account cannot make any more requests (they may already limit my account or they disable such Web API requests). But the overall pipeline should work well assuming the API request is successful. I ran the experiments right after ChatGPT came out so at that time it works perfectly well, and you can check the notebook output for evidence. Honestly, I do not know what OpenAI does with their API at this time, and I cannot test it out with my own account.
