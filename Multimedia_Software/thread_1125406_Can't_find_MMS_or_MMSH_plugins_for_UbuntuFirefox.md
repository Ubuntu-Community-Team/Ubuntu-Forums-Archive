---
title: "Can't find MMS or MMSH plugins for Ubuntu/Firefox"
date: 2009-04-14
forum: Multimedia Software
---

### Post by drded on 2009-04-14
I just installed Ubuntu 9 to replace 8.04. When I try to view some of the streaming sites I used to visit I get the plug-ins not found screen. First for MMSH then MMS. Then neither is found. Since these sites worked under 8.04 I am assuming this is a version 9 problem. Any suggestions on how to fix this, other than reverting to 8?

Dave

---

### Post by xc3RnbFO8P on 2009-04-14
Read this:
[http://ubuntuforums.org/showthread.php?t=341857]("http://ubuntuforums.org/showthread.php?t=341857")
[http://www.cinlug.org/node/316]("http://www.cinlug.org/node/316")

---

### Post by postadelmaga on 2010-08-18
To view mms stream in chrome or firefox

1. **add mediabuntu rep as shown [here]("https://help.ubuntu.com/community/Medibuntu")**

2. **Install non-free-codecs:**

```
sudo aptitude install non-free-codecs  
```

---

### Post by redmistpete on 2011-03-17
> **postadelmaga said:**
> To view mms stream in chrome or firefox

1. **add mediabuntu rep as shown [here]("https://help.ubuntu.com/community/Medibuntu")**

2. **Install non-free-codecs:**

```
sudo aptitude install non-free-codecs  
```

...did that but it says in the terminal;

sudo: aptitude: command not found

---

### Post by redmistpete on 2011-03-17
OK fixed - you have to install gstreamer bad plugins with synaptic package installer - that worked for me instead.

---

### Post by uim on 2011-07-02
I've checked in the software center, and gstreamer bad plugins is installed.  I uninstalled, reinstalled and rebooted, and still no luck with mms links in firefox.  Any ideas?

---

### Post by prosonik on 2011-08-19
If your still having problems, VLC will work out of the box. 

I also tested and confirmed it working after installing the package non-free-codecs from medibuntu repositories.

---

