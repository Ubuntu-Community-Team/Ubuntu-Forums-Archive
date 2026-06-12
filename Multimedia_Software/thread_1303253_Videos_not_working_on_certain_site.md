---
title: "Videos not working on certain site"
date: 2009-10-28
forum: Multimedia Software
---

### Post by ex-windowuser on 2009-10-28
This is weird.  I went to Cnet.com and went to the tab cnet tv.  This is where they have video reviews and how to.  It doesn't work on Ubuntu using firefox but when I use the Virtual Box it works with not problem.  What am I missing.  So far I love Ubuntu but this video problem is getting me upset.  I already did all the updates and with the help forum on the 64 bit version.

---

### Post by vinutux on 2009-10-28
Open synaptic | System > Administration > Synaptic package manger

Search **Flsha**

The only packages you should see installed are **ubuntu-restricted-extras** and **adobe-flashplugin**. Any swfdec* or gnash packages should be marked for complete removal

---

### Post by ex-windowuser on 2009-10-28
Okay, I'll try that.....hope it works.

---

### Post by ex-windowuser on 2009-10-28
Nope.  It still don't work.

---

### Post by vinutux on 2009-10-28
What version of ubunt u r using ? and 32 or 64

Which version of flash player installed ?

---

### Post by ex-windowuser on 2009-10-29
I am running 64bit Ubuntu and have the latest flashplayer....10.003 or something.  BUT I was able to install Google Chrome and I can go to any site and watch videos including Cnet.com.   I guess I am going to ditch Firefox until I can resolve this, if not I got Chrome.:D

---

### Post by ex-windowuser on 2009-10-29
bump

---

### Post by triplesick on 2009-10-29
Here is a similar story, but not necessarily a resolution to your problem:

Using Ubuntu and firefox, megavideo's videos won't load.  Videos on other sites work fine.  If I boot into Windows, megavideo works also.

I found the solution (which doesn't make any sense) was to use opendns for my dns.  You can give it a shot if you want.  Might or might not be the same problem you're having.

[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by HappyFeet on 2009-10-29
I always just put the 64bit flashplugin (libflashplayer.so) into /usr/lib64/mozilla/plugins. Works every time.

---

### Post by ex-windowuser on 2009-10-31
Don't know what the hell I did,uninstall and install stuff and all of a sudden everything started working fine.  Cnet.com  works with no problem.  I wished I wrote down what I did in case Ubuntu crashes.

---

