This is the code for the paper "Graph2Seq: Graph to Sequence Learning with Attention-based Neural Networks".

To train your graph-to-sequence model, you need:

(1) Prepare your train/dev/test data which the form of:

    each line is a json object whose keys are "seq", "g_ids", "g_id_features", "g_adj":
    "seq" is a text which is supposed to be the output of the decoder
    "g_ids" is a mapping from the node ID to its ID in the graph
    "g_id_features" is a mapping from the node ID to its text features
    "g_adj" is a mapping from the node ID to its adjacent nodes (represented as thier IDs)

    See data/no_cycle/train.data as examples.


(2) Modify some hyper-parameters according to your task in the main/configure.py

(3) train the model on CPU by running the following code
    "python3 run_model.py train -sample_size_per_layer=100 -sample_layer_size=5 -hidden_layer_dim=50 -epochs=300"
    The model that performs the best on the dev data will be saved in the dir "saved_model"
    
    Or on GPU:
    CUDA_VISIBLE_DEVICES=[xx] python3 run_model.py train -sample_size_per_layer=100 -sample_layer_size=5 -hidden_layer_dim=50 -epochs=300

(4) test the model on CPU by running the following code
    "python3 run_model.py test -sample_size_per_layer=100 -sample_layer_size=5 -hidden_layer_dim=50 -epochs=300"
    The prediction result will be saved in saved_model/prediction.txt

    Or on GPU:
    CUDA_VISIBLE_DEVICES=[xx] python3 run_model.py train -sample_size_per_layer=100 -sample_layer_size=5 -hidden_layer_dim=50 -epochs=300
    
(5) We hve uploaded a pretrained model, and you can directl run the test on the SDP-100 task. 


Please cite our work if you like or are using our codes for your projects!

Kun Xu, Lingfei Wu, Zhiguo Wang, Yansong Feng, Michael Witbrock, and Vadim Sheinin (first and second authors contributed equally), "Graph2Seq: Graph to Sequence Learning with Attention-based Neural Networks", arXiv preprint arXiv:1804.00823.

@article{xu2018graph2seq, 
title={Graph2Seq: Graph to Sequence Learning with Attention-based Neural Networks}, 
author={Xu, Kun and Wu, Lingfei and Wang, Zhiguo and Feng, Yansong and Witbrock, Michael and Sheinin, Vadim}, 
journal={arXiv preprint arXiv:1804.00823}, 
year={2018} 
} 
