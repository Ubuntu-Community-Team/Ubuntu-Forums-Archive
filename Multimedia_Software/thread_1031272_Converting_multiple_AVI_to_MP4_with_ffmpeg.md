---
title: "Converting multiple AVI to MP4 with ffmpeg"
date: 2009-01-05
forum: Multimedia Software
---

### Post by forbzie22 on 2009-01-05
Hello,

After a fair amount of time googling ive managed to find the following command to convert AVI to MP4 which successfully plays on the PSP.

ffmpeg -i OriginalFile.avi -f psp -r 29.97 -b 768k -ar 24000 -ab 64k -s 320x240 OutputFile.mp4

Does anyone know how to modify this command so i can convert multiple avi's to mp4 at once ?. At the moment, im having to run the command each time i convert an AVI.

I also have winff GUI, but the PSP doesnt recognise the video for some reason when winff converts.

---

### Post by ajgreeny on 2009-01-05
I think you could do this with avidemux, but perhaps you only want, or need a cli application.

---

### Post by andrew.46 on 2009-01-06
Hi,

A little sideways of your question but you may be interested to know that the ffmpeg faqs have a detailed section dealing specifically with the PSP:

[http://ffmpeg.mplayerhq.hu/faq.html#SEC25](http://ffmpeg.mplayerhq.hu/faq.html#SEC25)

All the best,

  Andrew

---

### Post by wolfen69 on 2009-01-06
i don't know about multiple files, but [Handbrake]("http://handbrake.fr/?article=download") is the best gui converter for the psp. 1 click and your done. there are presets on the right of the app for the psp, ipod, etc.

---

### Post by forbzie22 on 2009-06-18
thanks for ther replies, all helpful but needed something that can convert about 30 AVI's at once.

Everything ive found so far will only do one at a time, very time consuming.


IMTOO do a very good product but only runs on windows :(
[http://www.imtoo.com/mpeg-encoder.html](http://www.imtoo.com/mpeg-encoder.html)

This program is the only thing keeping me using windows at the mo

cheers

---

### Post by bumanie on 2009-06-18
You could try winff, which is a gui for ffmpeg - as far as I know, it can convert multiple files at once. Try [here]("http://code.google.com/p/winff/wiki/UbuntuInstallation")

---

### Post by jrock2012 on 2009-12-12
look for an app called Arista.. it'll solve all your PSP converter problems.. 

it's in the repositories..

---

### Post by UbuKunubi on 2009-12-20
Hello,

I'm not sure if this of interest here, but I'm writing/testing a python program from batch processing of avi,mp3, etc with ffmpeg.

So far I have a program that creates a list of avi files, and when the conversion is done, (so far I'm testing for CPU useage % to drop to below 25%), it moves on until the whole list of files is converted.

If your interested please direct message me and I'll post the code and instructions.

All the best,
Ubu

---

