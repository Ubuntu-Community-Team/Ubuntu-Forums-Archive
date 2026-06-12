---
title: "HELP! Cannot Play x264 MKV Video"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by derubermensch on 2007-08-16
I have EVERY little codec thing you need installed, and I've even installed multiple players (Mplayer, FFplay, VLC, Xine) and absolutely none of them will play back an MKV file with x264 video inside. They all tell me one way or another that they don't have the codec to playback.  HELP!!!!

---

### Post by RomeReactor on 2007-08-16
Hi. Does Mplayer complain about not being able to play the video? h264 mkv videos work fine here. Have you installed the w32codecs?

---

### Post by derubermensch on 2007-08-16
I installed all the restricted codecs and mplayer tells me there's no stream found despite detecting mkv format.

---

### Post by RomeReactor on 2007-08-16
Have you tried with other mkv files? there's a possibility that this particular one is corrupted. If you haven't installed w32codecs, you can get them from [here]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20061022-0medibuntu1_i386.deb"). Once it downloads, double click on it to install.

---

### Post by Gouz on 2007-08-17
Hello I have a problem with the mkv's as well I dont get any subs with Mplayer and if I full screen it when using VLC and change the language it crashes.
I have change the xv to x11 as i found that I have to do so fix the full screen bug, but it doesn't helped.
I tried to install the w32codec but I get an Error : architecture wrong " i386' or something like this.


I also got this:   Package libdvdcss2 has no installation candidate
and the same message for the w32codec when I tried to install them from the terminal
Any idea what those mean?

---

### Post by RomeReactor on 2007-08-17
Hi. That probably means you don't have the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories; look [here]("http://ubuntuforums.org/showpost.php?p=3203196&postcount=11") for how to add them (follow the first two commands only), and afterwards enter this in the terminal:
```
uname -m
```
if the result is 386 or 686, enter this to get w32codecs and libdvdcss2:
```
sudo apt-get install w32codecs libdvdcss2
```
if the result was x86_64, enter this:
```
sudo apt-get install w64codecs libdvdcss2
```

---

### Post by aldeby on 2007-09-16
Please give VLC videolan a . it doesn't need any codec since it has all bundled inside!
you can install it via package manager 
```
sudo apt-get install vlc
```
cheers:KS

---

