---
title: "Yet another Nvidia 8500GT that will not detect/config"
date: 2008-05-25
forum: Multimedia Software
---

### Post by bahzev on 2008-05-25
I'm brand new to Ubuntu as of a few days ago. After spending the last 2 days poring over these forums, guides, how-to's, etc. I have yet to come close to getting the nvidia driver to work. I have an Nvidia 8500GT on a Princeton LCD19D, Ubuntu 8.04LTS. All other hardware/peripherals appear to be working fine.

I have tried the following:
enabling the driver from the restricted hardware area
using EnvyNG
downloading the nvidia driver through Synaptic and configuring it manually with the aid of these forums.
lastly, I downloaded the driver from Nvidia and used the manual install directions found elsewhere on these forums.

In all cases the machine would hang after the Ubuntu logo with the loading bar beneath it. I would not hear a sound, and Alt-F1 did nothing, Ctrl-Alt-F1 did nothing, typing my login and password did nothing (no sound ever). I re-installed Ubuntu 8.04 after each of the above attempted installations, to avoid any conflicts with other driver versions.

With each install, I would also try putting in 
   Option    "UseDisplayDevice" "DFP"
under the "Screen" heading. I am using the DVI output from the card to the DVI input on the monitor. I do not have another video cable or monitor to test if the above option actually does anything. I do not have another computer to browse the internet as I work on the driver issue (working off the Live CD right now). 

Again, I have read through many many other threads and how-to's around here, and I have had zero luck. If someone is kind enough to walk me through something that does actually work, I would be very grateful. 

As of right now, the xorg.conf would not do much good since I'm on the live CD about ready to install yet again (this will make 14 installs by my mark, ugh).

Thank you in advance!

---

