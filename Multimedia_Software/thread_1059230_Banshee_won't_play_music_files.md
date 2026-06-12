---
title: "Banshee won't play music files"
date: 2009-02-03
forum: Multimedia Software
---

### Post by blazemore on 2009-02-03
Normally I know what I'm doing, so I'm a bit stumped with this one.
I imported a small music library into Banshee on my new netbook.
However, when I double-click a file to play, a small X appears next to it, and it moves to the next one. It does this a few times and then stops.

The music files play fine in VLC, and I have ubuntu-restricted-extras installed.

I've tried deleting and re-importing the files, and I'm using the latest stable Banshee from their PPA.

---

### Post by blazemore on 2009-02-03
Edit: I tried uninstalling and re-installing Banshee, and I also tried an older version. Still the same.

---

### Post by blazemore on 2009-02-04
Has anyone else had this problem, or knows how to fix it?

---

### Post by blazemore on 2009-02-05
*bump*

---

### Post by blazemore on 2009-02-12
*week ago bump*

---

### Post by mc4man on 2009-02-12
what is the format of the audio files your trying to play? (are you using 8.04 or 8.10?

 shouldn't be a problem to figure this out

---

### Post by blazemore on 2009-02-13
They are mp3.
I have ubuntu-restricted-extras installed, and VLC will play it.

But VLC doesn't use gstreamer, so I think it's a gstreamer problem.

---

### Post by mc4man on 2009-02-13
Well I don't use gstreamer apps (audacious and amarok) so I've never used/installed ubuntu-restricted-extras but..
mp3 playback for gstreamer apps is enabled thru the gstreamer0-10-ffmpeg plugin

Search gstreamer in synaptic and see if it's (the plug in) installed. If not, install it and then restart x (Ctrl+backspace

If it is, then reinstall and restart x

---

### Post by tylerannosaurus on 2009-10-30
I just fixed this problem on my computer. You just need to get the plugins gstreamer0.10-ffmpeg and gstreamer0.10-plugins-ugly. You can either go to the synaptic package manager (located in System>Administration>Synaptic Package Manager) and search for those, or I think the code to do that is just 

```
sudo apt-get install gstreamer0.10-ffmpeg
```
```
sudo apt-get install gstreamer0.10-plugins-ugly
```

I think that's all you need to do...let me know if that works!

---

### Post by Slothcake on 2009-10-31
sudo apt-get install gstreamer0.10-ffmpeg


Installed this and it worked fine

---

### Post by matthatesspam on 2010-09-01
> **tylerannosaurus said:**
> I just fixed this problem on my computer. You just need to get the plugins gstreamer0.10-ffmpeg and gstreamer0.10-plugins-ugly. You can either go to the synaptic package manager (located in System>Administration>Synaptic Package Manager) and search for those, or I think the code to do that is just 

```
sudo apt-get install gstreamer0.10-ffmpeg
``````
sudo apt-get install gstreamer0.10-plugins-ugly
```I think that's all you need to do...let me know if that works!
This solved the issue for me as well. :)

---

### Post by blazemore on 2010-09-04
If you're running Maverick, open Banshee's page in the Software Centre, and tick all the "add-ons" to install.

---

