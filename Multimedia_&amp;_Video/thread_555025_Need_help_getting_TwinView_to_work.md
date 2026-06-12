---
title: "Need help getting TwinView to work"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by anarcholis on 2007-09-19
I need help getting Dual Monitors to work. I have an x86 computer that I just installed 
Ubuntu 7.04 on. I have a GeForce 6600 graphics card, and I am trying to run two 
monitors, one from the VGA port and one from the DVI. I got TwinView up and running and 
one of my monitors gives me a "no input signal" error. 

Let me give some details:

-I downloaded the nVidia drivers (Linux IA32 v100.14.19, this is the newest version on 
the nVidia site) and installed them just fine. I used the NVIDIA X Server Settings tool 
to set up X. I also manually checked xorg.conf to make sure that the X settings tool 
worked correctly, which it seems like it did (I have done a similar setup on 6.10 in the past)

-I know the second monitor (the DVI is my secondary, VGA the primary) is working 
because when I exit X, the command line comes up cloned on both monitors. Same for the 
Ubuntu screen at the startup and shutdown sequences. But as soon as I get to the X 
desktop, one of the monitors goes black and hits standby mode. This tells me at least 
that the second monitor and cables are all working correctly.

-I am pretty sure that the TwinView functionality is working because when I go to 
TwinView, I can still drag objects from one screen to where the other <should> be, and 
I can move my mouse around the other screen. I just can't see these things because the 
second screen is blank. 

-Apparently there is some trouble with older monitors that don't support EDID. This 
shouldn't be a problem for me becuase I am using two Phillips 170S flat-screen 
monitors, which are still fairly new. Furthermore, I can acquire the EDID 
information from both monitors with the NVIDIA X Server Settings tool. 

-Here are the relevant parts of my xorg.conf. I don't think this is the problem but 
lets try anyways.

Section "ServerLayout"
   Identifier   "Layout0"
   Screen   0   "Screen0" 0 0
   ..
EndSection

Section "Module"
   ..
   Load         "glx"
EndSection

Section "Monitor"
   #HorizSync source: edid, VertRefresh source:edid
   Identifier   "Monitor0"
   VendorName   "Unknown"
   ModelName    "Phillips 170S"
   HorizSync     30.0 - 82.0
   VertRefresh   56.0 - 76.0
   Option       "DPMS"
EndSection

Section "Device"
   Identifier   "Videocard0"
   Driver       "nvidia"
   VendorName   "NVIDIA Corporation"
   BoardName    "GeForce 6600"
EndSection

Section "Screen"
   Identifier   "Screen0"
   Device       "Videocard0"
   Monitor      "Monitor0"
   DefaultDepth  24
   Option       "TwinView" "1"
   Option       "metamodes" "CRT-0: 1280x1024 +0+0, DFP: nvidia-auto-select +1280+0; 

CRT-0: 800x600 +0+0, DFP: nvidia-auto-select +800+0; CRT-0: 640x480 +0+0, DFP: nvidia-

auto-select +640+0"
   SubSection   "Display"
       Depth     24
       Modes     "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
   EndSubSection
EndSection


In conclusion, I think its some sort of problem with the GeForce card recognizing the 
FlatScreen monitor connected to the DVI port, because the software thinks that the 
extra area of my desktop is there, it just doesn't show up on the monitor.

However, this same configuration and same graphics card worked great under Windows, 
which is starting to make me wish that I had not so rashly wiped Windows off my 
computer when I installed Ubuntu. However, two days of struggling to do in Linux what 
took me 10 minutes in windows is starting to convince me that there is a reason that 
everyone uses Windows.

Thanks in advance for any help.

---

