---
title: "Create MP3 file from DVD"
date: 2011-10-09
forum: Multimedia Software
---

### Post by tomreid on 2011-10-09
Hi

I have a DVD and I only want to capture the audio from it (here in the UK, some radio stations are also "digital channels" on television, but the picture is just a card saying which channel it is). 

I have tried capturing the audio from an old utility I have used before called "outrec", but it didn't record any audio this time, it was a silent file. 

Anyone know of a utility that'll turn DVD audio into an MP3 or OGG compressed file?

cheers

---

### Post by robert shearer on 2011-10-09
outrec alternative here...
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

---

### Post by shantiq on 2011-10-09
IF YOU WANT JUST A SECTION OF IT
================================

play your dvd in VLC and hit the red button [view/advanced controls] then pick up your file in video ( probably an mpg ) and then convert to mp3 or ogg with soundconverter or soundkonverter 

IF YOU WANT THE WHOLE THING
===========================

Process all the VOBs with **soundconverter** or **soundkonverter** Both are in your synaptic


OR

 command line and only one VOB


you can do this   Go to terminal then into the folder


```
ffmpeg -i nameoffile.VOB -ab 256k nameoffile.mp3

```


for bulk ( all your VOBs)

```
for f in *.VOB; do ffmpeg -i "$f" -ab 256k "${f%.VOB}.mp3"; done 

```

---

