---
title: "MyMovie Player  can't play mpeg files"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by Julie wang 1982 on 2006-07-27
I have installed all the things in Synaptic Package Manager,but my Movie Player still can't play mpeg files.

I have updated Synaptic Package Manager,and the problem is still not solved

---

### Post by navilon on 2006-07-27
How many different mpeg files have you tried?

---

### Post by Julie wang 1982 on 2006-07-27
I have used four different mpg files .

My Rhythmbox Music Player can't play mp3 files also.

:confused: I really want to know why and how to solve this problem.

---

### Post by navilon on 2006-07-28
Make sure all of the repositories are enabled in /etc/apt/sources.list and try this
```
apt-get install gstreamer0.8-mad
```

---

### Post by Julie wang 1982 on 2006-07-28
Thank you very much.
I have downloaded 'gstreamer0.8-mad_0.8.8-2_i386.deb',and I did as you say,but it told me it couldn't find 'gstreamer0.8-mad_0.8.8-2_i386.deb'. When I install it directly it always displays an error:'Dependency is not satisfiable:libgstreamer0.8-0'.
I have no idear about it.
I don't know whether I have a wrong gstreamer0.8-mad edition.

---

### Post by navilon on 2006-07-28
Hmm, are you using the newest Ubuntu (6.06)?
And did you install that package through apt-get in the console?

(If you dont know how to do this, let me know)

---

### Post by Julie wang 1982 on 2006-07-28
I am using the newest ubuntu6.06,and I installed it through CD.

I didn't use ubuntu before.I always use windows.

---

### Post by whatever on 2006-07-28
gstreamer0.8 was used in breezy, in dapper you need to install the gstreamer0.10 plugins instead.

first make sure you got [multiverse and universe repostories](https://help.ubuntu.com/community/Repositories/Ubuntu) enabled, then
```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse 
sudo apt-get install gstreamer0.10-ffmpeg
```

for more info have a look at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by dphan on 2008-02-17
just update package manager first:
$sudo apt-get update

then install gstreamer (using wild-card better)
$sudo apt-get install gstreamer*

that s it and wait for system auto-install all gstreamer* for you.

Please note: if it still does not work, then maybe you have totem-xine installed in there, it overtakes totem-gstreamer, you need to remove it first
hope this help

---

