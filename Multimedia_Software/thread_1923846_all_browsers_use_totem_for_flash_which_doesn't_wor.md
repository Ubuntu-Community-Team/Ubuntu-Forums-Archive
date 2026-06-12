---
title: "all browsers use totem for flash which doesn't work"
date: 2012-02-11
forum: Multimedia Software
---

### Post by leftfinger on 2012-02-11
I suddenly found all browsers(firefox and chromium) is using totem(the place should originally show flash now showing a totem interface) for flash playback but not working. I don't know what's happening and how to make it use flash plugin. 
I guess it may be caused by that I added ppa:gnome3-team/gnome3 and ppa:ricotz/testing to apt repo and did a apt-get dist-upgrade. I did so to get gimp 2.7.5 back(it disappeared after a software upgrade). Maybe the upgrade of gtk related libs break the flash plugin?

I checked the firefox preference tab and found the seetings for flash file is to use flash plugin. So the firefox settings should be ok.
Also I tried purge all flash related packages and reinstall the flash plugin. No luck.

Following is a brief information of my system:
system: ubuntu 11.10 amd64, 3.0.0-15-generic
adobe-flashplugin: 11.1.102.55-0oneiric1
chromium-browser: 17.0.963.26~r116225-0ubuntu1~ucd~dev1
firefox: 10.0+build1-0ubuntu0.11.10.1

Anyone know how to debug this? Or is there people ever encourntering same issue as me?
Any help is appreciated.

---

### Post by BmD_Online on 2012-02-12
Hi there,

I have exactly the same problem.

---

### Post by winh8r on 2012-02-12
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1491268&highlight=flash+plugin]("http://ubuntuforums.org/showthread.php?t=1491268&highlight=flash+plugin")

which might help you.

---

### Post by leftfinger on 2012-02-12
> **winh8r said:**
> Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1491268&highlight=flash+plugin]("http://ubuntuforums.org/showthread.php?t=1491268&highlight=flash+plugin")

which might help you.

Wow. It did the job. Thank you very much!

To BmD_Online:
Just install "firefox aid" extension and update the plugin as it suggests and all is back. Note you may need to download this extension from github. I failed to add it from firefox official site, always saying connection is reset.

---

### Post by BmD_Online on 2012-02-12
Right.
Using this addon, removed adobe flash 11.1.102.55 (from repository) and installed latest beta.
Now it works correctly.

Previously, I've tried to (re)install stable version, but it doesn't helps.

---

