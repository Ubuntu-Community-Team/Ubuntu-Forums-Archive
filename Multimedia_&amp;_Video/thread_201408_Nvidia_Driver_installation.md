---
title: "Nvidia Driver installation"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by ChicoMakani on 2006-06-21
I am new here and new to Unbuntu.  I'm trying to get a MythTV box setup on a ASUS Pundit P1AH1.  The PC uses a AMD Venice 3200 and NVidia 6150 integrated graphics.

I installed the x86 desktop environment and updated the kernal for k7 optimization.

Then I installed the nvidia drivers like this:
apt-get install nvidia-glx linux-restricted-modules-k7
nvidia-glx-config enable

strange thing is that when I checked my xorg.conf file it says i have an ATI!

Section "Device"
    Identifier    "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
    Driver        "nvidia"
    BusID        "PCI:0:5:0"
EndSection

Is this a problem?  When I tried the same thing yesterday (I started fresh today), I used 

apt-get install nvidia-settings  nvidia-glx linux-restricted-modules-k7
nvidia-glx-config enable

and didn't get the line w/ ATI.

Is something wrong?

Thanks.

---

### Post by tseliot on 2006-06-22
Try my guide (Method 1):
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

### Post by ChicoMakani on 2006-06-22
I reinstalled using your guide and the same thing happened.  Everything seems to be working fine but the identifier says ATI.  

I've never been able to get the configuration application to load.

Thanks for the guide, it's very helpful.

---

