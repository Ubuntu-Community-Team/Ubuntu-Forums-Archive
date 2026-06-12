---
title: "Totem Could Not Startup Error - Help Needed"
date: 2012-09-17
forum: Multimedia Software
---

### Post by Col-1023 on 2012-09-17
The error message then gives,

Failed to create a GStreamer play object. Please check your GStreamer installation.

This happens when trying to play avi [xvid, mpg] & mp4, mkv - x264 files.

Rhythmbox fails to work also.

VLC and Gxine work perfectly [On the files I've tested so far]

I've upgraded from 10.04 to 12.04.1, and the only problem I had was the flightgear fgfs base error, which still comes up when I try to update packages.

I followed the universal guide and installed all the codecs from medibuntu, and I checked synaptic and it shoes that gstreamer is installed.

Any help with this appreciated, thank You.

---

### Post by Col-1023 on 2012-09-17
I've done some more searching and found this,


aslam karachiwala (akwala) said on 2011-11-12: 	#22

Deleting my ~/.gstreamer-0.10 folder fixed this for me.

Found the fix in Bug #770158, Comment #3:
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/770158/comments/3](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/770158/comments/3)


Where Is this folder and how do I delete it?

TIA

---

### Post by irv on 2012-09-17
Go to your home directory> go to the "View"> then select show hidden files.
[ATTACH]224275[/ATTACH]
You will find it there.

---

### Post by Col-1023 on 2012-09-17
THANK YOU, Irv,  That solved the problem.

I backed up the folder just in case, but have now deleted it, and movie player and rythmbox now play all the relevent file types and codecs.

Thanks to the community for your help.

---

### Post by irv on 2012-09-17
> **Col-1023 said:**
> THANK YOU, Irv,  That solved the problem.

I backed up the folder just in case, but have now deleted it, and movie player and rythmbox now play all the relevent file types and codecs.

Thanks to the community for your help.

Your welcome. 
I was having problems getting DVD's to play and had to run these two commands in a terminal:
```
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh


```
And that solved my problems.

---

