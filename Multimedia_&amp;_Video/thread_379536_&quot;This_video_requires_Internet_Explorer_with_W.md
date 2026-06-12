---
title: "&quot;This video requires Internet Explorer with Windows Media Player&quot;"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by fmrmarineinbiz on 2007-03-08
Like it says above.  When I now go to a website I frequent for training with my home business, I get an error message similar to:  **"The following video must be accessed in Internet Explorer with Windows Media Player"**  (The videos will not play via Firefox/Ubuntu)  Any ideas to get around this?  Luckily I still have a Win machine with IE and WMP on it.  The idea is to totally get away from Win though.  Oh, I have tried installing IEs 4 for Linux, and trying to access the videos this way through Ubuntu, but still no luck.  Also have upgraded my Firefox browser with what I thought were the right extensions for Win Media Player.

---

### Post by Hub-1 on 2007-03-08
Could you paste the website you are trying to access?

---

### Post by fmrmarineinbiz on 2007-03-08
> **Hub-1 said:**
> Could you paste the website you are trying to access?

Unfortunately I cannot.  It is login protected.

---

### Post by Hub-1 on 2007-03-08
It varies on the website on how the videos are provided. If you haven't already tried this, I suggest you install mplayer and the firefox plugin. 

sudo apt-get install mozilla-mplayer

---

### Post by fmrmarineinbiz on 2007-03-08
> **Hub-1 said:**
> It varies on the website on how the videos are provided. If you haven't already tried this, I suggest you install mplayer and the firefox plugin. 

sudo apt-get install mozilla-mplayer

When I try and enter that I get: 

sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
E:** Couldn't find package mozilla-mplayer**

---

### Post by trents on 2007-03-08
> **fmrmarineinbiz said:**
> When I try and enter that I get: 

sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
E:** Couldn't find package mozilla-mplayer**

I think you can install mplayer and its Firefox plugin (and a lot of other commonly used ubuntu aps) through Automatix. Have you tried it? It's a great tool.

Steve

---

### Post by nero_86 on 2007-03-08
mozilla-mplayer and mplayer can be found in the multiverse repositories. For add this repos go to

System->Administration->Software Properties  select add and select universe and multiverse.

From the CLI run
$ sudo gedit /etc/apt/sources.list

add the following

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe 
multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe multiverse

---

