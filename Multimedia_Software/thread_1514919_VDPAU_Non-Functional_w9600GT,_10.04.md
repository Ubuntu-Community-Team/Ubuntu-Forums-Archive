---
title: "VDPAU Non-Functional w/9600GT, 10.04"
date: 2010-06-21
forum: Multimedia Software
---

### Post by Freddie on 2010-06-21
Hi all,

I am having trouble getting VDPAU video output to work in Mythtv/mplayer. The error I get is that it was not possible to create/open a VDPAU device.

My system has a 9600GT — a card which should have VDPAU support — and I am using the proprietary drivers (195 if I recall). libvdpau1 is installed. Ubuntu version is 10.04 AMD64.

How can I go about debugging this and, ultimately, how do I fix it.

Regards, Freddie.

---

### Post by lykeion on 2010-06-21
Hi
I have the same videocard and using mplayer (multiverse version) and have no problem enabling vdpau. 
Before Lucid I used to compile mplayer myself to enable vdpau. 
If you're using an older Ubuntu version than Lucid you should check out this thread on how to compile mplayer with vdpau support:

[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

(I also think there are PPA repos where you could download precompiled packages)

If you are using Lucid you should edit/create the config file for mplayer and set it to prefer vdpau for video output and video codec.
```
gedit ~/.mplayer/config
```
and add /edit the vo & vc lines to read like this:
```
# Set video output and codec to prefer VDPAU
vo=vdpau,xv,
vc=ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, 
```

Note that I do not use mythtv (have no experience at all with it) and my processor is a AMD32, so there could be other issues you are facing. 
There have been lots of of posts in the forums about vdpau. I'd suggest you read them to learn more:

[http://ubuntuforums.org/tags.php?tag=vdpau](http://ubuntuforums.org/tags.php?tag=vdpau)

---

### Post by cbrunhaver on 2010-06-21
Try adding the Nvidia repository and downloading libvdpau1:

sudo add-apt-repository ppa:nvidia-vdpau/ppa

sudo apt-get install libvdpau1

---

### Post by Freddie on 2010-06-21
> **cbrunhaver said:**
> Try adding the Nvidia repository and downloading libvdpau1:

sudo add-apt-repository ppa:nvidia-vdpau/ppa

sudo apt-get install libvdpau1

I seem to have been hit by [https://bugs.launchpad.net/ubuntu-website/+bug/435193](https://bugs.launchpad.net/ubuntu-website/+bug/435193) which makes it (currently) impossible to add the PPA repo until the keyserver is back online.

However, I have been doing some debugging and found that by exporting NVIDIA_VDPAU_DEBUG=3 and then running mplayer that the problem/error creating the VDPAU device is of form:
```

VDPAU nvidia: Error detected 0 6291

```

I am unsure how to interpret this, however.

Regards, Freddie.

---

### Post by cbrunhaver on 2010-06-21
actually, I don't think you need the nvidia repository.  Just try:

sudo apt-get install libvdpau1

---

### Post by Freddie on 2010-06-21
> **cbrunhaver said:**
> actually, I don't think you need the nvidia repository.  Just try:

sudo apt-get install libvdpau1

Yep. Got it.

Regards, Freddie.

---

### Post by cbrunhaver on 2010-06-21
Did that do the trick?

---

