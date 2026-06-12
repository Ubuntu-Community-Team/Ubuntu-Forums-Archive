---
title: "Attempting (for some time now) to covert ebooks / text to wav/mp3"
date: 2016-11-19
forum: Multimedia Software
---

### Post by porphiron on 2016-11-19
Hi All,

Yes I know this is a a very rusty issue with some people having good results and some not so much...but I digress.

Right, Ive had a a look at this post: 

[http://askubuntu.com/questions/53896/natural-sounding-text-to-speech](http://askubuntu.com/questions/53896/natural-sounding-text-to-speech)

Plus a various sources from the web and have had limited luck both gTTS and and Simple Google™ TTS,

Both work fine for a few paragraphs but then luck out. I guess due to some sort of time out / security measures??. It would be nice to be able to convert a whole book albeit in chunks, but the time outs seem random so splitting a whole book down to a couple of paragraphs is just simply too time consuming, so...

Ive settled on pico2wav, as its minimalist and the voices for a small program sounds great, unfortunately it also suffers from a similar problem.

I've used the small script from here, [http://askubuntu.com/a/179922](http://askubuntu.com/a/179922), with thanks to the original author

#!/bin/bash
pico2wave -l=de-DE -w=/tmp/test.wav "$1"
aplay /tmp/test.wav
rm /tmp/test.wav

removing the 'aplay' and 'rm' lines to provide a .wav file i can convert.

when running the bash script ./speech.sh "$(cat filename.txt)"

 which works for a few paragraphs ( once again ), then I get the following:

./speech.sh: Argument list too long

Reading further in the post in the above url, another person surmises that the use of xargs is required.

From what I understand, pico2wav is seeing some of the inputted text as arguments to alter settings etc and not as text to be read / converted so, using xargs negates some of this?.

To get to the point, I've read the man page for xargs and read a number of web pages.

But.... for the life of me I cannot figure out what or how xargs needs to be configured to implement its use with pico2wav.

Has anyone else come across this?...has anyone have any ideas?

Any help in this matter would be gratefully received and will help to reduce my hairloss!


Many Many Many Thanks.

Jan

---

### Post by irv on 2016-11-19
A few years back I converted a bunch of old books (text format) into audio files using [http://www.spokentext.net/]("http://www.spokentext.net/"). Worked for me.
If you  have them in epub format you might want to get them to a pure text file. You could try using Sigil epub editor.
If you don't have it installed (not sure what your OS you are running) I am using Ubuntu 16.04 and I installed it using thise commands.
```
sudo add-apt-repository ppa:ubuntuhandbook1/sigil

sudo apt update

sudo apt install sigil sigil-data
```.

---

### Post by porphiron on 2016-11-21
Irv,

Thanks for the reply, Ile have a look.

Cheers.

Jan.

---

