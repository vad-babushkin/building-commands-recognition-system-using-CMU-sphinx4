building commands recognition system using CMU sphinx4
============================================================

Training language model using CMU oneline LMtool, then use Python and the open source Sphinx-4 speech-recognition package to implement the command recognition system and recognize the commands.


Installing Sphinx-4
--------------------
How to Build and Run Sphinx4 http://cmusphinx.sourceforge.net/wiki/sphinx4:howtobuildand_run_sphinx4

Custom dictionary
--------------------
In the Sphinx-4 directory tree, there is a directory called bld/models/edu/cmu/sphinx/model/acoustic/WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz/dict/. 
This directory contains the alpha.dict and digit.dict dictionary files. we'll need to build our dictionary files from the cmudict.0.6d file in the same directory.
Change to the bld/models/edu/cmu/sphinx/model/acoustic/WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz/dict/ directory and issue these commands to build the desired dictionary file:
<pre><code>
#! /bin/sh

cp WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz_backup.jar WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz.jar
jar xvf WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz.jar
cd WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz/dict/

cp custom.dict WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz/dict/

# add custom dictionary file into *.jar file
jar -uf WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz.jar WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz/dict/alnum.dict 
mv WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz.jar ../lib

rm -rf WSJ_8gau_13dCep_16k_40mel_130Hz_6800Hz/ META-INF/

</code></pre>

Configuration of project
------------------------
Sphinx-4 provides many configuration options to meet almost any need in the field of speech recognition. 
<pre><code>
src/
└── sphinx4
    └── conversation
        └── annotation
            ├── annotation4conv.config.xml
            ├── annotation4conv.gram
            ├── Annotation4conv.java
            └── annotation4conv.Manifest
</code></pre>
