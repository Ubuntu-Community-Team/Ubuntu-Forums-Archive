---
title: "Good Bye Win XP-don't need EAC-use falcon instead"
date: 2012-12-16
forum: Multimedia Software
---

### Post by dun270 on 2012-12-16
Years I've looked for in linux equivalent for EAC(Easy Audio Converter)to split wav files into individual named tracks with cue files, without having to use wine.
 Now I have used flacon, found at [https://code.google.com/p/flacon/](https://code.google.com/p/flacon/)

get it:
 sudo add-apt-repository ppa:flacon
  sudo apt-get update
  sudo apt-get install flacon

I'm using Xubuntu 12.04. Flacon has all the tools for different audio formats.

---

### Post by ohnonot on 2012-12-17
cool.
every now and then i download some music in that format and most media players just don't get it, so this is useful.
i tried it and it works.


=;careful, advanced stuff:
if you check the dependencies (i don't have all the codes, but shntool is essential) you don't have to install it by ppa, but can run it straight from the download folder (./flacon.py)

---

### Post by nomnex on 2013-01-22
> **dun270 said:**
> Years I've looked for in linux equivalent for EAC(Easy Audio Converter)to split wav files into individual named tracks with cue files, without having to use wine.

EAC is a CD Ripper. If you just look to split your CUE files, you can also do without falcon.
```

# sudo apt-get install cuetools shntool 
```There is a nice tutorial here:

[http://en.linuxreviews.org/HOWTO_splitt_lossless_audio_files_%28ape,_flac,_wv,_wav%29_using_.cue_files]("http://en.linuxreviews.org/HOWTO_splitt_lossless_audio_files_%28ape,_flac,_wv,_wav%29_using_.cue_files")

---

### Post by speartip on 2013-01-23
Ive had a look at Flacon, I currently use Rubyripper.
But everytime I put in a CD to rip, I get the message:
"Conversion is not possible. CUE file is not set"
Any Help:confused:

---

### Post by mwillams73 on 2013-04-17
Flacon was exactly what i needed to transcode some dts wav files and split the single wav album into single track mp3s, except all the tracks are static? makes no sense, sound converter can transcode the same wav file into an mp3 file (all tracks combined into one mp3 the same as the wave file) but it cant split them so what the heck am i doing wrong?

---

### Post by mwillams73 on 2013-04-17
I'd like to note, that when sound converter transcodes the single wav file to mp3 it plays flawlessly. I really dont want to mess with the terminal just to transcode and split a friggin album, thats so like 20 years ago. It seems to me that I should be able to do this with a gui program but they dont exist in ubuntu, atleast for all my searching....... which is what led me here......

---

