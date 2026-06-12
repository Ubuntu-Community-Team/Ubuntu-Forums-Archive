---
title: "alsa 1.0.14 no sound"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by mynis on 2007-06-11
so i was trying to get my mic to work last night and after reading the forums for a few hours i decided to give updating my also drivers a shot using the method described here
[http://ubuntuforums.org/showthread.php?p=2798055#post2798055](http://ubuntuforums.org/showthread.php?p=2798055#post2798055)
afterwards i lost all sound completely. the test buttons in the sound pannel in preferences still work but thats about it. i ran alsamixer in the terminal and nothing was muted, however at the end of the installation i was given this warning:
WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

any ideas?

edit:interestingly enough i get sound while running ventrilo in wine now
edit: so while trying to fix it i tried plugging my speakers into my onboard soundcard (which i would prefer NOT to use) and was getting the output there, even though i have my pci card selected in the preferences. I have no idea how to fix this or where to look even
edit: ok so while reading about 1.0.14 also drivers i was at this page [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/7025](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/7025) and realized there was also the lib and utils packages that i needed to install. installed them and rebooted and now my sound card works correcctly AS WELL as my mic. sweet deal

---

