---
title: "[Mint] Framedrop in fullscreen, SMPlayer not working"
date: 2008-07-24
forum: Multimedia Software
---

### Post by Doccie on 2008-07-24
I'm having some problems with my new Linux Mint install (I switched from Windows XP to Mint on my desktop today)

Mint came with two players: Movie Player and MPlayer. I also installed SMPlayer.

When I try to view a standard .avi file (divx) in MPlayer it throws a fatal exception at me (Error opening/initializing the selected video_out (-vo) device). When I click OK, the file does play, but only the sound.

The settings for MPlayer:
Video Tab > Available Drivers > XV selected
Codecs & Demuxers Tab > Codec families (both sound and video) > None

When I open the file in SMPlayer it leaves a blank screen for about 10 seconds and then the file just unloads, like you would get when you open SMPlayer via the Applications menu.

SMPlayer settings:
General > General > Output drivers > Video: XV, Audio: Pulse
Performance > Allow Frame Drop and Allow Hard Frame Drop both ticked
(Not ticked in MPlayer)

In Movie Player the file loads almost immediately, but there's a huge frame drop when I view in fullscreen (maybe, 15-20fps)

I have an Iiyama HM903DT A CRT monitor with a ATI Radeon X850XT graphics card.

My screen resolution is set to 1920x1440 @ 75Hz
My compizconfig General settings (display settings tab):
Detect Refresh rate ticked
Refresh rate set at 75
Detect output is ticked
Ouputs: 1920x1440+0+0
Overlapping output handler: smart

I hope someone will be able to help.

Kind regards,
Pieter

---

### Post by rvm4000 on 2008-07-24
It seems xv is not working for you. Have you tried another one? (x11, gl, gl2)

---

### Post by Doccie on 2008-07-24
Thank you for the fast reply. I just tried in both MPlayer and SMPlayer, the GL and GL2 video output drivers both result in a flickering video (frames are substituted with white).

The X11 driver gives better results, but when going into fullscreen mode in MPlayer the video just keeps the same dimensions and fills the rest of the screen with white, in SMPlayer, there's a framerate drop and the quality becomes very poor (a lot of deinterlacing).

---

### Post by shirilover on 2008-07-24
If you are running compiz-fusion, try disabling it.
XVideo overlay and desktop composition don't get along well.

---

### Post by Doccie on 2008-07-25
Thanks Shirilover, that did the trick! However, I quite like my rotating cube :D Is there any way for me to have both? (I'll settle for a way to automatically disable it when I go into fullscreen and reenable once I come out of it... ;))

---

### Post by shirilover on 2008-07-25
I use fusion-icon to toggle between compiz/metacity.
Change to metacity before watching video and then change back after.
Fusion-icon is an icon that sits in the notification area and allows you to toggle many window manager options.

---

### Post by Doccie on 2008-07-25
Thanks a lot :) Just compiled it.

---

