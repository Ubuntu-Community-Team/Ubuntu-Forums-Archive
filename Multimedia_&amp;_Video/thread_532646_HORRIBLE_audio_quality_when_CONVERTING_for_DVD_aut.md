---
title: "HORRIBLE audio quality when CONVERTING for DVD authoring!"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by superyounan1 on 2007-08-23
I'm trying to burn a dvd out of a divx file. I used "ManDVD", but the VOB files it produced had extremely distorted audio, it was scratchy and staticy. So I tried "DeVeDe" and got the same exact results.

Whats going on, do I have some sort of audio card incompatibilities?

---

### Post by Architeuthis on 2007-09-06
Look at the  warning on the devede website: [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html) .

> Note for Ubuntu Feisty users: currently (as April 20, 2007), the Mplayer/Mencoder version in Ubuntu Feisty is buggy and produces noisy sound when used with DeVeDe. While the maintainer doesn't fix it, you can use the package with the previous version, available in the Download section).

 I think it has something to do with the buggy version of mencoder, since manDVD uses it too.

---

### Post by reckless2k2 on 2007-09-06
that's because you are supposed to be using windows to do stuff like that. hahahaha..seriously

---

### Post by pizpot on 2007-09-11
the answer is to use avidemux to convert the avi to a mpg. Then use devede to make the mpg to iso but you have to click Advanced Options, Misc, Special, This file is already a DVD/xCD-suitable MPEG-PS file. Boy that sucked to type, you are lucky to have me.

If you need help with avidemux, Open your avi file. Click auto dvd. Click calculator and set to mpg and dvd5 and hit apply. then set the filter to change to fps to 29.97 if need be and have it at 720x480 and 16:9 and 48000 sample rate audio. Use the Preview button and also play the mpg before proceeding.

---

### Post by superyounan1 on 2007-09-21
thanks for the tips!

---

### Post by pizpot on 2007-11-28
New solution:

Uninstall devede:

sudo apt-get remove devedee

Then edit your sources file to include the backports source:

sudo gedit /etc/apt/sources.list

and uncoment this part:

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

by removing the #'s from the start of the lines.

Then reinstall devedee and a newer version without the problem will install:

sudo apt-get install devede

Then put your sources file back how it was. Yay!

---

