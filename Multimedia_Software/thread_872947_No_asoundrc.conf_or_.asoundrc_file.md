---
title: "No asoundrc.conf or .asoundrc file"
date: 2008-07-28
forum: Multimedia Software
---

### Post by nirvana21 on 2008-07-28
I am attempting to utilize my 5.1 speakers. I have read a few tutorials but I cannot find either the asoundrc.conf or .asoundrc file. I understand that .asoundrc is suppose to be in my home folder and the other in /etc . I tried viewing hidden files and conducting searches of my filesystem.

I read this on the ALSA wiki:

"Neither .asoundrc or /etc/asound.conf is normally required. You should be able to play and record sound without either..."

I cannot find either files so should I create them? I'm running Ubuntu 8.04 64bit if that helps any. 

Thanks beforehand!

---

### Post by nirvana21 on 2008-07-28
anybody?

---

### Post by markbuntu on 2008-07-28
Well, that is true. Alsa will generate its own .asoundrc.asoundconf file in your home directory that is just a list of default values. 

I have an ~.asoundrc but it is empty. This file can be used to change the defaults in the ~asoundrc.asoundconf file if you need to do that.

You can set up an etc/asoundrc file in for setting up some global changes to the defaults that will be for every user of your system. I don't have one of those either.

But no, you do not need to create them unless you are following one of those guides in which case gedit will make one for you if it does not already exist.

All my sound works. I can play anything simultaneously with anything else except for with jack, which is its own beastly nightmare as far as that goes.

---

