---
title: "amarok won't play any m4a/aac files"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by insert_name_here on 2008-01-10
I just installed gutsy, amarok and ubuntu-restricted-extras.

Amarok will play mp3s, but not m4a files.  (These are non-DRMed - they worked before I reinstalled in amarok).  

My amarok is set to use the xine engine.  VLC and Totem will play m4as correctly.  How do I fix this?

The error is:

Error Loading Media
There is no available decoder.

---

### Post by Pechorin on 2008-01-11
Hi no name

Try installing libxine1-ffmpeg from synaptic-package-manager. 

It did the trick for me. 

Here's where I found the tip:
[https://answers.launchpad.net/ubuntu/+source/amarok/+question/3007]("https://answers.launchpad.net/ubuntu/+source/amarok/+question/3007")

---

### Post by Joeb454 on 2008-02-19
Thanks pechorin :) Just installed Amarok again and couldn't remember how I got it to play my m4a files last time :P

---

