---
title: "Mplayer will not run"
date: 2010-01-27
forum: Multimedia Software
---

### Post by aftofcopperwire on 2010-01-27
I'm having a problem running Mplayer in Ubuntu 9.1. I've installed and uninstalled several times. Mplayer refuses to open from the applications menu. When I attempt to open from terminal it comes up with the following:  mplayer: error while loading shared libraries: /usr/lib/i686/cmov/libavcodec.so.52: file too short  I've also tried other players such as Gnome Mplayer to play the video and it plays really fast with no audio or video.  This has really been the only problem i've run into since switching from windows to linux two weeks ago. Any help would be appreciated.

---

### Post by andrew.46 on 2010-01-28
Hi aftofcopperwire,

Sounds a bit odd. Perhaps you could try installing an improved version of libavcodec from the Medibuntu repository and while you are there a better gui for MPlayer called SMPlayer. Hopefully while doing this your damaged installation of MPlayer and libavcodec will be rectified. It can be done as a single command:

```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update && \
sudo apt-get install smplayer libavcodec-extra-52

```

I attach a screenshot of the marvelous SMPlayer in action. 

Andrew

---

### Post by OCN on 2010-01-28
wtf is he looking at

---

### Post by aftofcopperwire on 2010-01-29
> **andrew.46 said:**
> Hi aftofcopperwire,

Sounds a bit odd. Perhaps you could try installing an improved version of libavcodec from the Medibuntu repository and while you are there a better gui for MPlayer called SMPlayer. Hopefully while doing this your damaged installation of MPlayer and libavcodec will be rectified. It can be done as a single command:

[CODE]
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update && \
sudo apt-get install smplayer libavcodec-extra-52


 Tried the above but still got the same error and exit code: 127 in smplayer. So, I tried reinstalling each of files that came up file too short in synaptic and that seems to have fixed it. Thanks for your help.

---

