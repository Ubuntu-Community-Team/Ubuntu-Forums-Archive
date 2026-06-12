---
title: "Need Help With Kodi / XBMC With 2 GPUs &amp; 2 Monitors"
date: 2015-07-27
forum: Multimedia Software
---

### Post by lambdafox on 2015-07-27
I have 2 gpus running the latest AMD proprietary driver / catalyst software:

SAPPHIRE HD 7970 3GB GDDR5 OC with Boost 

XFX Double D FX797ATDJC Radeon HD 7970

I have an HDTV monitor attached to one with an dvi/vga adapter and a samsung monitor attached to the other with dvi.

I run Kodi in a window, and it will not display on the extended part of the desktop.

The part of the window on the extended desktop is blacked out.

Kodi support is mad at AMD/ATI and will not provide support for me with this.

I am new to linux; so, the way Xinerama works, the xorg.conf, etc. kind of flies over my head.

Yesterday, I tried a new idea.  I created a xubuntu vmware virtual machine and tried running Kodi in it.  To my surprise Kodi shows the SAME behavior inside the vmware player window!!??  Kodi does this in the VM whether full screen or windowed.

I have a Windows XP virtual machine that I use for the software that I have not yet converted myself over to linux.  So I tried installing XBMC 12.3, the last XP compatible version.  It does the same thing.  Kodi does this in the VM whether full screen or windowed.

My next idea is to separate the monitors / gpus onto separate desktops instead of using Xinerama.  Before I do that, though, I wanted to post here for any other ideas.

---

### Post by wyliecoyoteuk on 2015-07-27
I think the hdmi/vga adapter may be part of the problem.

---

### Post by lambdafox on 2015-07-27
I was not clear earlier that Kodi is the only program I have that does this.  I can drag windows around the entire desktop, with or whithout documents open.  I can even drag a. window with VLC playing a video anywhere without a glitch.

Kodi's menu looks fine until I reach the right edge of the first monitor the part on the other monitor shows the border but the inside is blacked out.  It is the same while playing video.  As. I noted earlier, this even happens in a vm??

I have connected each cable / monitor to each card, and the symptom is the same.  That is to say kodi looks fine on either gpu and cable unless it is moved over the line between monitors.

---

### Post by wyliecoyoteuk on 2015-07-28
It works for OK me, but I am using a single GPU with twin outputs.
Kodi uses a rendering system that only up dates changes in the display, not the whole screen. It may be that it does not work across GPUs.
Have you tried using both outputs from one card?

---

### Post by lambdafox on 2015-07-28
My DVI cable has a right angle connector.  Because of this, I can only connect the two cables to the XFX card.  It has two DVI-I ports so that should work.

When I do, though, it does not detect the tv.  I ran sudo aticonfig --initial --adapter=all and sudo aticonfig --initial=dual-head --screen-layout=left --adapter=0.  But it behaves the same.  It is only detecting my computer monitor connected to the topmost DVI-I port.

I have an hdmi cable and was able to get xinerama working on this gpu with that.  Interestingly, kodi DOES indeed seem happy anywhere on the desktop.

Just to reconfirm that it was not a cable issue, I wanted to try 2 gpus with the hdmi cable.  I had to purge and reinstall the fglrx drivers, but once that was done.  Kodi is misbehaving as before.

As I mentioned earlier, I am new to linux, but it seems to me that if kodi will not work on the second gpu in a vm, it would not fix the problem if I install separate desktops.  Is that correct?

---

### Post by wyliecoyoteuk on 2015-07-28
It might, not sure, sorry.
Vms use a virtualised graphics driver, and would not see the gpus any differently to the xserver

---

