---
title: "Screen flashes when playing movies"
date: 2009-03-22
forum: Multimedia Software
---

### Post by BramWillemsen on 2009-03-22
Hello everyone,

When i try to play a movie in 'movie player' or VLC, my screen starts to flash like crazy. A frame of the movie is displayed, followed up by a totally black frame. This happens several times each second. The result of this is that it is impossible to watch movies. I get a similar effect on some sites that stream video. But in this case the flashing only occurs when i hover my mouse over an object on the website. Movies on youtube show no flashing at all, maybe because it is flash based ? I am running ubuntu 8.10 desktop edition on my laptop. I installed the ati proprietary FGLRX graphic drivers. Did anyone experience similar problems ? Or do you maybe have a hint for me, where i should look for a solution? I'm quite new to ubuntu so i'm not that experienced yet.

---

### Post by nqlblq on 2009-03-22
I had the same problem. If you run CompizFusion or any other graphics program like it, try turning it back to Metacity.

You can do that by opening the desktop manager for said program and changing the preferences back to metacity when you want to watch a movie. In fact, I know a guy who had that in a script (or something) HotKey's to like crtl-(insert random key) so when he put in a CD he just hit that and it was fine.

Give it a shot, let us know.

---

### Post by ronocdh on 2009-03-22
A very common problem. In the settings for VLC, you can choose the method of video playback. It's probably at OpenGL or something now; unfortunately the fglrx drivers tend to cause flickering with accelerated video playback.

Change the option in VLC to X11 and see if that helps. It won't be accelerated (i.e. should be using your CPU rather than GPU) but at least it won't flicker at you.

---

### Post by ronocdh on 2009-03-22
Oh, and if the problem exists elsewhere, you can change the video playback settings at a lower level. VLC uses xine I think, whereas most GNOME video apps (e.g. Totem, Cheese) use GStreamer.

Changing the the video playback settings for these will affect video playback systemwide.

---

### Post by BramWillemsen on 2009-03-22
Thanks for the help guys.  I tried searching for flickering screen and i got many results. This topic solved it for me [http://ubuntuforums.org/showthread.php?t=1023688&highlight=vlc+flicker](http://ubuntuforums.org/showthread.php?t=1023688&highlight=vlc+flicker)

If anyone has the same problems, The first suggestion of Ringi (from link) helped me. It suggested to turn off compiz. I see you suggested the same nqlblq. Thanks for the help all!

---

