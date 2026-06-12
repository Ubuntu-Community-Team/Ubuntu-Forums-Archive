---
title: "Flash-plugin or flash-nonfree?"
date: 2009-12-28
forum: Multimedia Software
---

### Post by Alvarlinux on 2009-12-28
Hello everybody,


              Can anybody help me out with this task? I'm using Ubuntu 9.10 Karmic Koala, but I can't watch Youtube videos properly. I've tried installing only Flashplugin-installer, and that didn't solve the problem (Some videos are loaded, others are not). Also, whenever I switch any video to fullscreen, there's a high frame skipping, or simply doesn't go fullscreen. If I install flashplugin-nonfree, something very similar occurs: I can watch videos sometimes, and sometimes not. What should I do? Is there any way to make this work properly? There are also many sites that use shockwave which have embedded controls that don't make any response to my mouse clicks, or keyboard input... What should I do? Any ideas?

Thank you very much.

---

### Post by erlyrisa on 2009-12-28
This has sadly bugged linux users since the dawn of flash --> some-one adobe/macromedia is hiding some "tricky code" ....

Sadly Adobe themselves have placed a "fake bug" into the linux version of thier player - the mac one doesn't do it , even though the mac one would be pretty much same for same machine code wise (if not identical). Instead Adobe have purposely ripped out the one line of code that actually makes thier player work properly on Windows and OSx pc's....

I think what they (adobe) are waiting for is for some smart alick to figure out what it is that Flashplayer does that makes it transcode frame data over the cpu to the gpu ... till then Adobe is not givving over the "good version" of flash.


..ie (I have pentium 2's (Msoft) that play flash better than my Core2 Duo with Karmic on it)


PPS --> ubuntu is still slower than the other oses when it comes to high frame/resolution video playback...

ie I have a dual bot core2duo, windows 7 plays media fine .. ubuntu karmic only JUST plays back HD video.

---

### Post by bread on 2009-12-28
Hi,

I had a similar problem on 9.04. I don't know whether the solution is the same on 9.10, but try going to synaptic package manager and disabling SWF. AS for the issue with going to full screen on youtube - try clicking your RMB on the video->settings->turn off "Enable hardware acceleration". Hope this will help somehow.

---

### Post by LillaEpsilon on 2009-12-29
I had similar problems and solved them by removing anything coming from Adobe and using swfdec-mozilla instead. Now I can watch fullscreen videos both in YouTube and other video streaming sites without problems.

---

### Post by HappyFeet on 2009-12-29
Are you using 64bit ubuntu?

---

