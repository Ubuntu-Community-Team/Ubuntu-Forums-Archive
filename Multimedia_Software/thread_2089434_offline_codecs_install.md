---
title: "offline codecs install"
date: 2012-11-29
forum: Multimedia Software
---

### Post by i_karpas on 2012-11-29
Please help
I installed Ubuntu11.10 32bit in an IBMTP41 notebook, that is **NOT **connected to the internet,
tried running video files such as .mp4,.flv,.avi,.Xvid, in Movie Player but it asks for plugins, see the list below
mp4: MPEG-4 AAC decoder; H.264 decoder
flv: SorensonSpark Video decoder; MPEG-1 Layer3(MP3) decoder
avi: MPEG-1 Layer3 (MP3) decoder; MPEG video decoder
XviD: AC-3 (ATSC A/52) decoder; XviD MPEG-4 decoder

how do i donwload (from another computer with internet) and install all these plugins and their dependencies.
I also want to install the VLC Media player and its dependencies
I assume this is related to the restricted codecs and I have tried donwnload/install them with no success.
I read "Comprehensive Multimedia & Video how to" but it assumes a connected computer.
 I'll appreciate all ur help

---

### Post by evilsoup on 2012-11-29
There is no really easy, painless way of doing this, unfortunately; and certainly not with the default Ubuntu software.

Assuming you have the same version of Ubuntu on both computers (this won't work if you don't, and tou'll have to try slightly more difficult methods): the most foolproof way, though it is inelegant, is to install ubuntu-restricted-extras and VLC on your machine that *does* have internet access.

Then, copy the contents of /var/cache/apt/archives onto a USB memory stick. Go to the un-connected computer & plug in the memory stick, and copy those files into *that* computer's /var/cache/apt/archives directory. When you've done that, open up a terminal (ctrl+alt+t) and paste in the following commands, one line at a time. You'll need to enter your password at least once.
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras vlc
```
With that done, you should be able to play back those formats.

---

### Post by i_karpas on 2012-11-29
Thanku evilsoup 4 ur prompt reply, unfortunately my connected computer has Ubuntu12.04 (not 11.10), I'll wait some more and if nothing else comes up i'll try u suggestion.
    Thaku   i_karpas

---

### Post by i_karpas on 2012-11-30
Thanku evilsoup 4 ur prompt reply, unfortunately my connected computer  has Ubuntu12.04 (not 11.10), I'll wait some more and if nothing else  comes up i'll try u suggestion.
    Thanku     i_karpas

---

