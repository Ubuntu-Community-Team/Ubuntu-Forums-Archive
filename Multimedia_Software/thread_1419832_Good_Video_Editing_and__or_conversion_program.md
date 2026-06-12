---
title: "Good Video Editing and / or conversion program?"
date: 2010-03-02
forum: Multimedia Software
---

### Post by daldude on 2010-03-02
What is a Good Video Editing or video format conversion program for Ubuntu 9.04 64bit?

I was able to some how find Pytube and install that but it will only allow me to do a file conversion once after installing it and then any time after that if I try to convert another file it will say conversion complete in less then a second but does not convert the file because there is no way any program on any PC can convert a video file from one format to another in less then a second plus the file name I used as the target file does not show up where it was supposed to be saved.

I also installed a program called Kdenlive and I can't even figure out how to use it to edit videos or convert a file from one format like Flash Video to a format that is common like AVI or MPEG or Windows Media, the only option it has is Trascode which only supports High Definition MOV files and takes forever to convert only to have the video play back choppy.

I would prefer a program that both will convert file formats and edit video files so I don't have to convert in Ubuntu and then reboot to XP and use Movie Maker if I want to edit out any thing I don't want or merge 2 video files into 1.


Thanks

P.S. 
Is this the best place to ask this question or would it be better to ask in the General Help forum?

---

### Post by blur xc on 2010-03-02
> **daldude said:**
> What is a Good Video Editing or video format conversion program for Ubuntu 9.04 64bit?

I was able to some how find Pytube and install that but it will only allow me to do a file conversion once after installing it and then any time after that if I try to convert another file it will say conversion complete in less then a second but does not convert the file because there is no way any program on any PC can convert a video file from one format to another in less then a second plus the file name I used as the target file does not show up where it was supposed to be saved.

I also installed a program called Kdenlive and I can't even figure out how to use it to edit videos or convert a file from one format like Flash Video to a format that is common like AVI or MPEG or Windows Media, the only option it has is Trascode which only supports High Definition MOV files and takes forever to convert only to have the video play back choppy.

I would prefer a program that both will convert file formats and edit video files so I don't have to convert in Ubuntu and then reboot to XP and use Movie Maker if I want to edit out any thing I don't want or merge 2 video files into 1.


Thanks

P.S. 
Is this the best place to ask this question or would it be better to ask in the General Help forum?

Kdenlive was going to be my suggestion.  It's really not that hard to use- google kdenlive tutorials or something similar, see what comes up.   If you want complicated, try out cinelerra and blender...

As a straight up video converter, try out handbrake.  Great program, I mostly use it to rip dvd's.  It's got presets for the standard handheld devices as well, psp, ipod, ipod touch, etc...  It is a bit more complicated to use, but there are tutorials online on how to use it (I've had to look them up at first to get started) but once you are going, it's real simple.  A few mouse clicks- about 45mins (on my system) later, and a dvd is in whatever format I want.

BM

---

### Post by daldude on 2010-03-02
Where do I get handbrake 0.9.3 64 Bit ? I have Ubuntu 9.04. All I can find is 0.9.4 which seems to be for 9.10 only and when I try to install it I get this error message.



Error: Dependency is not satisfiable: libsoup2.4-1 (>= 2.27.92)


> **blur xc said:**
> Kdenlive was going to be my suggestion.  It's really not that hard to use- google kdenlive tutorials or something similar, see what comes up.   If you want complicated, try out cinelerra and blender...

As a straight up video converter, try out handbrake.  Great program, I mostly use it to rip dvd's.  It's got presets for the standard handheld devices as well, psp, ipod, ipod touch, etc...  It is a bit more complicated to use, but there are tutorials online on how to use it (I've had to look them up at first to get started) but once you are going, it's real simple.  A few mouse clicks- about 45mins (on my system) later, and a dvd is in whatever format I want.

BM

---

### Post by blur xc on 2010-03-03
> **daldude said:**
> Where do I get handbrake 0.9.3 64 Bit ? I have Ubuntu 9.04. All I can find is 0.9.4 which seems to be for 9.10 only and when I try to install it I get this error message.



Error: Dependency is not satisfiable: libsoup2.4-1 (>= 2.27.92)

I have no idea.  I've only ever installed it on 32bit 9.04.  Thanks for the heads up though, when Lucid comes out, I'm going to be switching to 64bit...

BM

---

### Post by ghostborg on 2010-03-03
kdenlive, openshot, kino, dvgrab

handbrake, ogmrip, dvd::rip

Install your codecs from medibuntu.org and ubuntu-restricted-extras

---

### Post by daldude on 2010-03-11
I found a conversion program that works good it's called Mobile Media Converter and it does more then just Mobile media formats, it can handle AMR,3GP,MP3 WMA,WMV,OGG,WAV,MPEG,AVI,FLV,MOV and MP4. It also is supposed to be able to download from YOUTUBE but it has failed the last few time I tried that feature but that has a easy but slow work around, I use PYTUBE to save the Flash Video in my temp folder after a Youtube video finishes downloading the streamed video buffer.


Mobile Media Converter can be found at 

[http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)
It's a Free Program that supports LINUX,MAC and Windows.

---

### Post by kliffs on 2010-03-13
Use winff for the converting. It has a graphical interface or you can use the command line.]

Use OpenShot for editing. It has Green screen, B+W, Burning TV and lots of other effects, it has a timeline, a clip bin and a lot more. I put in AWN!

---

### Post by shipp on 2010-03-13
Im running karmic koala, so I want to Download HANDBRAKE for ubuntu 9.10.  Only thing is, I don't know whether to get the GUI version or the CLI version.  I would also like to download it through synaptic or the terminal because the last time i tried downloading something via a wizard off the software's main site, it installed a bad package that f'ed up my songbird.

Essentially, whats the difference between GUI and CLI, and how do i install the right one through the terminal or synaptic?

---

### Post by Tikkyca on 2010-03-13
Kdenlive,Pitivi Video Editor,gtk-record my desktop,if you want to record your desktop...

---

### Post by 2hot6ft2 on 2010-03-13
Installing handbrake in 9.10 from the PPA
```
sudo add-apt-repository ppa:handbrake-ubuntu/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install handbrake-gtk
```
I don't know about 64 bit though.

---

### Post by hazelnut on 2010-03-14
sudo apt-get install avidemux

also, totally awesome for cutting mpegs (ts, vob, mpg, etc) is ProjectX

[http://www.videohelp.com/tools/ProjectX](http://www.videohelp.com/tools/ProjectX)

That version works well, but it's old.  If you want the latest, you have to cvs it from here:

cvs -z3 -d:pserver:anonymous@project-x.cvs.sourceforge.net:/cvsroot/project-x co -P Project-X

It's a java app, read the ReadMe.txt

---

