---
title: "Video is all wonky"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by nbv4 on 2006-06-10
When I play videos with VLC or any other media player, the video seems to tax the CPU big time. As a matter of fact, trying to play a McGuyver episode at full screen uses 100% CPU and it dropps frames. Even on the desktop the display seems just slow.

My processor is a brand new AMD64 3200+, so it shouldn't be doing this. I'm using a MSI K8NGM2-FID as my motherboard, which comes with a Geforce 6150 onboard. I'm thinking the right driver is not installed, correct? I tried installing the nVidia driver via easy ubuntu, but that didn't help.

---

### Post by pratzabrat on 2006-06-11
I have the exact same problem. Mine is an amd 2800+ with n nvidia card. All the players seem to perform poorly. I tried the xv output on mplayer but still no results. Please help. Need to catch up with episodes of 24 I missed.

---

### Post by nbv4 on 2006-06-13
I found a fix.

First, install the nvidia driver for linux. EasyUbuntu is an easy way to do this.

once that has been done, go into a terminal and type "gedit /etc/X11/xorg.conf"

now there should be a command in the comments section at the top that starts with "sudo..." (I can't remember the exact command, and I'm not at my ubuntu machine now).

Run that cammand in the terminal and select nvidia.

Now type this - "sudo mv /etc/X11/xorg.conf.[TAB] /etc/X11/xorg.conf"

when you press tab, a number will be added in there. Now restart and it should be fixed. If you see a nVidia logo at boot up, it should be fixed.

---

