http://cs.stanford.edu/people/karpathy/char-rnn/shakespear.txt
http://karpathy.github.io/2015/05/21/rnn-effectiveness/
https://devblogs.nvidia.com/parallelforall/introduction-neural-machine-translation-with-gpus/


## Excerpt Machine Learning:

Pamula, Pawel [Tech] updated recent meetup hosted by Tokyo Machine Learning Society
event site TMLS#4 Review of the state of the art - connpass
slides in speakerdeck, which you need to use home PC to access slides https://speakerdeck.com/tmls
Excluding NVIDIA's marketing presentations, various interesting sessions
Character-Level Machine Translation with Bi-scale RNNs by Joe Bullard
Usually, on NLP people uses word by word processing to extract meaning, generate text or translate
Instead, by processing text character by character, it can gain flexibility, and they showed example
To bein with, Pawel used his laptop to run a demo using Torch
build RNN model by parsing Shakespeare's text
using a model, generate a text like Shakespear with 3 layers, 256 nodes in each with 2 epochs
laptop doesn't have GPU and it takes 10 minutes to build small model, but created text where ROMEO was saying something to JULIET
the text was broken down to characters. so F, i, r, s, t, <space>, \n (new line) .. all of those are used as input to build RNN
At earlier stage, the generated sample text is random, but as learning goes, it starts to generate proper word, wiht good use of punctuations
To build a translator, first the model will encode the source text into a vector, then decode in to target language using the vector
on decode, it'll pick up the highest probabibility "character" and use that to get the next state (i.e. character) with the vectorized model
On parsing text, it used bi-directional RNN
They showed demo of English to Japanese translation
used sample text from tatoeba.org (GS blocked) with 200,000 human translated examples
e.g. "You seem to have gained some weight" was translated to
(RNN output) 君は少し体重が増えたようだ。
(sample from the site) 少し体重が増えたようですね。
to me, the RNN output is in very good quality in this case, there were a few others, not really working e.g.
"You only imagine you've heard it".. this was translated to Japanese sentence that doesn't sound natural.
Deep Math by Fred Almeida
As intro, they shared an algo that predicts mass from video: Which one is heavier?
The challenge here is to use Deep Learning for mathematical proofs generation
Used Mizar (proof checker) for input data Mizar Home Page
Build 2 CNN/RNN models, one using Axiom, the other from Conjecture, then concatenate them
We weren't sure how they "concatenate" that...
It could prove 62.95% of test data. Interestingly in the same table, k-NN based one could prove 59.34%
so CNN and other enhancements (i.e. Deep Learning), the gain was 6%, not sure how great this number was
Generative Adversarial Networks by Hasanov
It can be used to generate natural looking image
it uses sample data to generat new, but not like the original
It generates model using ramdonmess, also uses randome sample, and find a spot where discriminator distinguish them at 50% probability
The generated images were low resolution because it shrinks down image to generate new random noised one
in last couple of years, those GAN technicues were merged with Deep learning tools, Convolutional network in particular
In discriminator, use pool layer
In generator, use fractional strided convllutions layer
and other ones you may see in other Deep Learning tools (ReLU, LeakyReLU, ADAM etc...)
minibatch discrimination
historical averaging
Those DL toolset improved quality i.e. the generated image is in higher resolution and appears realistic
Using those vectors, can combine images e.g. "man with glasses" - "man without glasses" + "woman without glasses" = "woman in glasses"
latest generated pictures appears like a real picture of unrealistic ones
That reminded me of DeepDream. Searched DeepDream vs GAN, they are different
Deep Dream is single CNN based onversion
GAN uses 2 CNN, one for generation, tthe other for discriminator
Additional reference Pawel shared
Neural Machine Translation https://devblogs.nvidia.com/parallelforall/introduction-neural-machine-translation-with-gpus/
Unreasonable effectiveness of RNNs http://karpathy.github.io/2015/05/21/rnn-effectiveness/
OpenAI notes on Generative Adversarial Networks https://openai.com/blog/generative-models/
