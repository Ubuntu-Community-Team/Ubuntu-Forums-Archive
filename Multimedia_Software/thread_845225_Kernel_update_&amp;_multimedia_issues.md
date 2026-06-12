---
title: "Kernel update &amp; multimedia issues"
date: 2008-06-30
forum: Multimedia Software
---

### Post by crypope on 2008-06-30
Hi,

I post this here so that maybe some of Ubuntu users that have just applied kernel updates and experience issues with ivtv drivers.

I had to boot to an older kernel version:

"6.24-17-generic #1 SMP" to fix VLC so that I can play TV from cable.

On 2.6.24-19-generic & 2.6.24-18-generic kernels, I had these messages in /var/log/messages

Jun 30 06:32:20 ... kernel: [  629.099551] ivtv0: Cause: the application is not reading fast enough.
Jun 30 06:32:20 ... kernel: [  629.197198] ivtv0: All encoder MPG stream buffers are full. Dropping data.

As I checked my PVR-150 firmware modules were properly installed on new kernels as well and the only solution to have my ivtv drivers working properly was to stick with this old kernel.

I am wondering if I am the only one experiencing these king of issues including frame drop. I have a P4, 3.4 GHz with Ubuntu 8.0.4 and all the updates. Video card is a All in Wonder 9600 running with restricted drivers just fine in DRI mode.

---

### Post by wolfen69 on 2008-06-30
your case is the very reason that i turned off updates. after a fresh install i did what updates were available, then locked it down. *then* installed my apps. it will stay this way until ibex comes out.

---

### Post by lfini on 2008-07-01
Me too!
After last updates I had multiple failures: the first I spotted out with kernel  2.6.24-19 was VirtualBox: it lacks some driver. So I went back to 2.6.24-18 kernel. After some time I noticed that all movie viewers are screwed up: mplayer show only the upper half of the screen, totem freezes the x11 server completely.
 This happens on  an HP laptop with Intel 9456M graphic card. It doesn't happen on a desktop with nVidia GeForce 6600

---

