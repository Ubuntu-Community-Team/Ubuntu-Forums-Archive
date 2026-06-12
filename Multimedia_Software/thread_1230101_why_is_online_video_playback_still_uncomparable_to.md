---
title: "why is online video playback still uncomparable to windows?"
date: 2009-08-03
forum: Multimedia Software
---

### Post by theromanone on 2009-08-03
For me, that is :). And I hate it.

It seems like half of the time whenever I'm letting a flash, youtube, megavideo, zshare, etc video load, and I open another video or even go to another website on a separate tab, the original video turns white/gray. I need to refresh the page to see any of the controls for the video (not that they work), and to actually watch the clip. Then, doing this many times makes the *other* video in the second tab turn gray.

Anyone have this? It, really, is the absolute last thing I would like to correct to have a perfect OS for me!

---

### Post by vinutux on 2009-08-03
I have no prob for video...installed flash from **[COLOR="Red"]labs.adobe.com[/COLOR]**....coz of running 64 bit os....

---

### Post by theromanone on 2009-08-03
I'm with the 64-bit jaunty also, and already running 64-bit flash..

---

### Post by caeroe on 2009-08-03
> **vinutux said:**
> I have no prob for video...installed flash from **[COLOR="Red"]labs.adobe.com[/COLOR]**....coz of running 64 bit os....

I made my weekly attempt to get Flash working properly for Ubuntu 9.04 x64.  The package from Synaptic now plays Flash at the same performance level of Windows, no low FPS or stuttering.  Awesome, except I can no longer interact with the GUI controls, like pause, play, fullscreen, etc.

The x64 plugin from Adobe still has the same horribly slow performance, but I can interact with the controls.

In other words, after 5-6 years of playing with Linux, Flash has never worked like it has in Windows.  That's with several different distributions and PC's I've owned (either custom or the two off the shelf notebooks).  :confused:

---

### Post by warp99 on 2009-08-04
> **caeroe said:**
> In other words, after 5-6 years of playing with Linux, Flash has never worked like it has in Windows.  That's with several different distributions and PC's I've owned (either custom or the two off the shelf notebooks).  :confused:

This is Adobe's fault in how they have choosen to render the video using OpenGL. The standard 32-bit flash plugin will use hardware acceleration if available otherwise it will fall back to software rendering only. If Compiz is installed and running Adobe will only use software rendering as explained in this post:

[http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

You can work around the issue with the 32-bit plugin by using a hex editor to locate the string "compiz" and replace it with xxxxxx. Now hardware acceleration and compiz will run at the same time but may or may not be stable depending on your configuration. 

Unfortunately the x64 flash plugin does not have any access to hardware acceleration so the plugin is only using software rendering.

---

### Post by kpkeerthi on 2009-08-04
No problems with me. Using nvidia binary driver (185.18.31)/ old 7800GTX. Fullscreen flash video playback as smooth as butter.

---

