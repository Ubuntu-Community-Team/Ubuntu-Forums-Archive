---
title: "Dual Monitor Display? (S-Video to TV, Inspiron E1505, ATI Mobility Radeon X1400)"
date: 2009-09-16
forum: Multimedia Software
---

### Post by ChoneZone on 2009-09-16
Hey all,
 
I'm trying to enable a dual monitor display using an S-Video cable and my TV (to watch videos and such), similar to what I used to do in Windows. When it is all hooked up, my TV does not get any signal but flickers whenever I hit the "Detect Monitors" button in the Ubuntu display preferences menu.

I've googled around a little bit, but most of the information I have found is either a little bit over my head, or is specific to nVidia drivers. I am using a Dell Inspiron E1505 laptop with a ATI Mobility Radeon X1400 video card. Does anyone have any suggestions? Or is anyone able to point me in the right direction for some further information to help solve this problem?

Thanks!

---

### Post by purduepilot on 2009-09-17
> **ChoneZone said:**
> Hey all,
 
I'm trying to enable a dual monitor display using an S-Video cable and my TV (to watch videos and such), similar to what I used to do in Windows. When it is all hooked up, my TV does not get any signal but flickers whenever I hit the "Detect Monitors" button in the Ubuntu display preferences menu.

I've googled around a little bit, but most of the information I have found is either a little bit over my head, or is specific to nVidia drivers. I am using a Dell Inspiron E1505 laptop with a ATI Mobility Radeon X1400 video card. Does anyone have any suggestions? Or is anyone able to point me in the right direction for some further information to help solve this problem?

Thanks!
I have the same computer, and this is something I've been trying to figure out since I started using Ubuntu.  xorg is my bane.

---

### Post by mike909 on 2009-09-18
exact same scenario here.
There is [this post]("http://ubuntuforums.org/showthread.php?t=318155") that is mostly useless, because when I go to "system-->administration-->Hardware Drivers" it's just blank. No proprietary drivers are listed, or in use. [ATI driver download for linux.]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.9&lang=English") not sure how to proceed with those. I tried [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20%28latest%20version%20of%20drivers%29") but again, step 1 is to enable it in "proprietary drivers" but it's not there.

---

### Post by ChoneZone on 2009-09-21
Upon doing some investigations, the issue seems to be related to the fact that ATI halted support for many of its older drivers back in Feb 09, including the Mobility Radeon X1400. The latest versions of Ubuntu do not work with the older ATI drivers due to a lack of compatability with the latest version of xorg (I think). So, instead the open source drivers are used for these nonsupported ATI drivers, and I'm assuming the open source drivers lack the capability to do s-video output correctly. More info can be found in [this thread]("http://forums.linuxmint.com/viewtopic.php?f=59&t=31845").

I found [another thread]("http://forums.linuxmint.com/viewtopic.php?f=59&t=20876") on the Linux Mint boards which seems to address this exact issue. I run Mint 7 by the way. However, the solutions posted did not seem fix the problem for me. Lacking any knowledge about xorg, I am unsure as to why the xorg modifications posted in that thread did not solve the problem for me like it did for them. Anyone have any suggestions?

Here is what my xorg currently looks like:

Section "Monitor"
   Identifier   "Configured Monitor"
EndSection

Section "Screen"
   Identifier   "Default Screen"
   Monitor      "Configured Monitor"
   Device      "Configured Video Device"
   SubSection "Display"
      Virtual   2480 1050
   EndSubSection
EndSection

Section "Device"
   Identifier   "Configured Video Device"
   Option       "TVDACLoadDetect"   "TRUE"
   Option          "AccelMethod"   "XAA"
EndSection

Section "ServerFlags"
   Option   "DontZap"   "False"
EndSection

---

### Post by mike909 on 2009-10-17
Yea, I just tried that as well CloneZone, and it did not help.
I've pretty much lost hope at this point.

---

