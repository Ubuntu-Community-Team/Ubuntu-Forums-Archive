---
title: "Good Converter Suggestions"
date: 2008-05-23
forum: Multimedia Software
---

### Post by chilipeppersman on 2008-05-23
I need a good quality converter to convert my .avi movie file to a good quality file that can be played on my psp. i already tried WinFF and a few others, does anybody have any suggestions???
please let me know, im dyin over here

---

### Post by jethro10 on 2008-05-23
> **chilipeppersman said:**
> I need a good quality converter to convert my .avi movie file to a good quality file that can be played on my psp. i already tried WinFF and a few others, does anybody have any suggestions???
please let me know, im dyin over here

I always end up with avidemux, I know it's a bit complicated to get started with but the newer versions (from synaptic, dont worry) have a PSP template ready in there.

J

---

### Post by aeiah on 2008-05-23
you could try a script like this if you want to automate it:
[http://can.homeunix.org/sw/psp/ffmpeg_psp/](http://can.homeunix.org/sw/psp/ffmpeg_psp/)

---

### Post by chilipeppersman on 2008-05-24
i tried avidemux, but when i dragged and dropped the .mp4 file to the video folder on my psp, nothing came up in the video section and the memory card said i had used the space for the movie. whats going on?

---

### Post by Major_Kong on 2008-05-24
mencoder + the h264enc script. 
It's CLI but a very good solution... The script is quite simple to use.

[http://forum.doom9.org/showthread.php?t=134652](http://forum.doom9.org/showthread.php?t=134652)

---

### Post by chilipeppersman on 2008-05-30
isnt there an easier way/program that i could use? this seems pretty complicated.

---

### Post by Major_Kong on 2008-06-11
> **chilipeppersman said:**
> isnt there an easier way/program that i could use? this seems pretty complicated.

It's not that complicated. Just type "./h264enc -2p -p pspvp" in the h264enc path, and then answear the questions.

---

### Post by cozmicharlie on 2008-06-11
I have been looking for a good converter myself so I know what you are going through.  So far, Avidemux seems to be the best solution in Linux but I am not completely satisfied with the results.  Did you use the preset for the ipod?  I found I had to play around with the settings to get what I want.  

I also tried Winff - this is just a GUI front end for ffmpeg.  It is very simple and may work for you.  My files are all in video TS folders with multiple VOB files so I had to find a way to merge them.  I set up VOBMerge (an Open Source Windows program) in Wine and it works great.  So I use VOBMerge to merge the .vob files then I use Winff to convert them to avi/mpeg.264.  

These may help:
[https://help.ubuntu.com/community/iPodVideoEncoding#head-ebb27b589cb5a6aa0c7fca5837cb0e0eb76b1909](https://help.ubuntu.com/community/iPodVideoEncoding#head-ebb27b589cb5a6aa0c7fca5837cb0e0eb76b1909)

[http://rob.opendot.cl/index.php/useful-stuff/ipod-video-guide/](http://rob.opendot.cl/index.php/useful-stuff/ipod-video-guide/)

---

### Post by dje on 2008-06-11
I use blacklight for my sony walkman nwz a818, it may or may not work for the psp? anyway it's worth a try - very easy to use

hope that helps,
dje

---

### Post by JEDIDIAH on 2008-06-11
> **chilipeppersman said:**
> isnt there an easier way/program that i could use? this seems pretty complicated.

It's really only complicated the first time you need to sort it out. After that you can just script everything. It may seem a little daunting at first but it doesn't really take much to get started.

Why is the PSP such a pain? I can use the default divx and x264 options for mencoder with no problems on the Archos 605.

---

### Post by timcredible on 2008-06-11
ffmpeg will do it easily, but it's command line (do a man ffmpeg to find out exact command).  if you use ffmpeg, make sure you use the -sameq parameter, or it'll make it look like crap due to overly heavy compression

---

### Post by chilipeppersman on 2008-06-11
thanks for all the help but im not using linux anymore, i switched back to windows.

---

