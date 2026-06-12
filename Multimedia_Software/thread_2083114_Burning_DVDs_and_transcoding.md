---
title: "Burning DVDs and transcoding"
date: 2012-11-11
forum: Multimedia Software
---

### Post by And6ate9 on 2012-11-11
I looking for 2 good programs for transcoding and burning to dvds.
Any suggestions?

---

### Post by andrew.46 on 2012-11-11
I can shamelessly promote 2 of my own web pages, rather than 2 applications;

FFmpeg and 'Fist of Fury'
[http://www.andrews-corner.org/fist.html](http://www.andrews-corner.org/fist.html)

which deals with transcoding from the commandline interface and this one:

CD and DVD Writing from the Linux Command Line
[http://www.andrews-corner.org/burning.html](http://www.andrews-corner.org/burning.html)

which deals with burning to cd or dvd from the commandline interface. This approach (from the commandline) is a huge amount of fun!

---

### Post by gordintoronto on 2012-11-11
Devede and K3B or Brasero.

It's worth your while to spend 15 minutes in the Help for Devede. I think it's one of the best help files I have seen, and I have no connection to the project.

---

### Post by And6ate9 on 2012-11-11
I think the command line burning is a bit much for me. I am looking for more of a 1 to 2 click solution.

I also tried Devede because I want to make a video dvd. However, I just couldn't seem to get it to make a burnable dvd. Although maybe I was using it wrong.

---

### Post by evilsoup on 2012-11-12
For simple transcoding, I would recommend HandBrake. It can take practically any video format and convert it to MP4 or MKV with h264, MPEG2, or ogg video. It also has good default settings, so if you wish you can just use it 'as-is', without any mucking around.

It's not in the repositories for Precise and earlier, and the version in the Quantal repos is crippled, so you'd be best off using the version in the [official HandBrake PPA](https://launchpad.net/~stebbins/+archive/handbrake-releases).

```
sudo apt-add-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install ghb
```

---

### Post by gordintoronto on 2012-11-12
> **And6ate9 said:**
> I think the command line burning is a bit much for me. I am looking for more of a 1 to 2 click solution.

I also tried Devede because I want to make a video dvd. However, I just couldn't seem to get it to make a burnable dvd. Although maybe I was using it wrong.

Devede makes an ISO file, and then you  use K3B or Brasero to "burn the image," just like when you make a bootable Ubuntu DVD.

---

### Post by beaucoder on 2012-11-13
Hi Guyz,

I found a way that works pretty well and does a lot.

I used OpenShot to make a video compilation, converted web downloads of both music videos and an old TV Show western. I exported these files which became an ".avi". Made a couple of videos projects and exported to ".avi".

I then used DeVeDe to load the ".avi" file and set the check box to burn an ".iso" file. DeVeDe then made a call to Brasero which burned an NTSC DVD.

All the edits were there and the DVD runs as expected. 

Using 12.04. 

HTH,

Ken

---

### Post by And6ate9 on 2012-11-13
how do you avoid losing quality in changing to avi file?

---

