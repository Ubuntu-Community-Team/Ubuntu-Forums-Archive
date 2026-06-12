---
title: "XBMC second screen (TVout)"
date: 2008-06-26
forum: Multimedia Software
---

### Post by Havel on 2008-06-26
I have installed XBMC media center on my Ubuntu Hardy. It works like a charm. I just need to do a few more tweeks to have the perfect setup.

I have 2 screens (computer and TV) with a NVIDIA 8600gt video card in Seperate X screens mode.

I would like XBMC to automatically open on the TV screen(second screen) when I start my computer. For the automatic start I know I have to go in the Session settings. But I dont know how to have XMBC open directly on the second screen TV

Here's what I found in the XBMC read me file:

> If you have a multi-monitor setup and you want to run XBMC fullscreen
only on one monitor, then make sure to set the environment variable
SDL_VIDEO_FULLSCREEN_HEAD to the display no. which you want to use.

For e.g. "SDL_VIDEO_FULLSCREEN_HEAD=1 ./xbmc.bin" to tell XBMC
to use display no.1. 

Could anyone explain to me how I use these instructions. Where do I go to set the environment variable SDL_VIDEO_FULLSCREEN_HEAD ?

---

### Post by ajgoyt on 2008-06-27
You should probably post your question in Official XBMC forums under XBMC for Linux.

Here is the link - [http://xbmc.org/forum/forumdisplay.php?f=52](http://xbmc.org/forum/forumdisplay.php?f=52)

Just a Tip:)

AJ

---

### Post by firfin on 2008-07-03
If you have nvidia-settings ( sudo nvidia-settings in console) installed, you can use that to check your screen number. 
You might also try checking the Xorg configuration file ( /etc/X11/xorg.conf )  but that's a bit harder to read than nvidia-settings.

---

### Post by graabein on 2008-12-13
I have the exact same problem. Where do I set the environment variable?

Update: Added **SDL_VIDEO_FULLSCREEN_HEAD=1 ./xbmc.bin -fs** to my */etc/environment* file but XBMC still starts on screen0 after I rebooted.

Another update: I found I could do **source /etc/environment** from the command line to reload the environment file.

---

