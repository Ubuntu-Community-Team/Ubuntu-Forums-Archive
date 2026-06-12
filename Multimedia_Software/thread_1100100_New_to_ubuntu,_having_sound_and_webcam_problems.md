---
title: "New to ubuntu, having sound and webcam problems"
date: 2009-03-18
forum: Multimedia Software
---

### Post by ShadowGazer on 2009-03-18
Hey everyone, I have the latest distribution of Ubuntu (8.10) and I can't get sounds to work for the system, webpages with flash (like playlist.com for instance) and when I try to listen to mp3s I can't hear anything either.  I can't get my webcam to work either.  I have a Soundmax Digital Integrated audio card, and my webcam is a Logitech Quickcam IM.  Please help if you can.  I'm a complete newbie when it comes to ubuntu, I'm used to windows and I would appreciate exact steps to take in order to get my sound and webcam working.

One thing to note:  Certain programs like skype, the sound works with that.  Also I had Kopete installed and I could sometimes get the sounds to work in that but not always.

Please help:redface:

---

### Post by ShadowGazer on 2009-03-20
Bump!

---

### Post by hansdown on 2009-03-20
Hi ShadowGazer.

Hope this helps.

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10)

---

### Post by ShadowGazer on 2009-03-20
What exactly does this accomplish?  I did everything on that webpage and I don't understand what exactly is supposed to happen?  My sound still isn't working, nor is my webcam, and I have alot of extra programs that seem to just load my system with stuff I won't use?

---

### Post by issih on 2009-03-20
Sound wise, given that you say sound does work in some cases, but that you can't play mp3's I'm going to guess that you didn't install the "ubuntu restricted extras" package.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

The relevant bit for right now is:

> [LIST]
[*]Go to Applications &#8594; Add/Remove...
[*]Set Show: to All available applications
[*]Search for ubuntu-restricted-extras and install it. Note that there is also xubuntu-restricted-extras (for Xubuntu) and kubuntu-restricted-extras (for Kubuntu.)[/LIST]

In essence ubuntu ships without various proprietary licensed software and codecs (including mp3) adding that package installs them.

Note that there are a load of little how to's at the bottom of the link I posted, and you probably want to pay attention to the one on playing dvds :).

As for the webcam, I don't know off the top of my head, I'll see if there is any documentation lying about.

Hope that helps

---

### Post by Mohulis on 2009-03-20
I'm having a similar problem, when I try to install the ubuntu-restricted-extras it says that it cannot install due to a conflicting package and to remove it using the synaptic package manager.  I figured this was the ffmpeg package I installed (can't remember the exact name atm) But I removed that and there's still a conflict.  The ffmpeg is the only package I remember installing that I would think would affect ubuntu-restricted-extras... I know it could probably be a million things, but are there any common ones I could check for? I've done some searching and haven't been able to find much - thanks in advance.

---

### Post by issih on 2009-03-20
Hmmn not sure, but I'd try adding ubuntu restricted extras within synaptic itself and hitting apply, hopefully it might tell you what the offending packages are.

---

### Post by Mohulis on 2009-03-20
Well, I feel silly now.  The conflicting program was VLC.  I have ubuntu-restricted-extras installed now... but still can't get mp3's to play... time to do some more digging!

---

### Post by ShadowGazer on 2009-03-22
Same here, can't get sounds to work with webpages, mp3s, etc.  I can get sounds in the program called Skype but not in other programs.  Sound works fine in Windoze XP but not in ubuntu.  I was able to install the drivers for windows sound, but not in ubuntu.  I have an integrated sound card, might that be the problem?  I wouldn't know, I'm really very new to ubuntu.  I installed it because I couldn't get windows to install, but now all of a sudden it installed again after I installed ubuntu and I'm dual booting now.  Like I said, sound works fine in windoze but not in ubuntu

---

