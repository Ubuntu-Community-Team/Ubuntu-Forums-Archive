---
title: "ATI IGP 345M Acceleration, Please Help"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by pHluid on 2006-06-04
Hi all. Let me first start by saying I'm relatively new to Linux in general, and even more so to Ubuntu.

   I'm trying to get accelerated graphics on a Compaq Presario 2535QV laptop, with an ATI 345M IGP. I first tried setting up fglrx, unclear as to whether or not my chipset was supported or not - This results in a "No device found" error and the xserver refuses to even start.

   When that failed, I tried to set things up to use the open-source radeon driver, rather than the ati driver set by the Ubuntu installed. This seemed to "work" fine, however DRI is still set to no afterwards and it still says Mesa under fglrxinfo output (I'm not sure if it's supposed to or not).

   I've read about a hundred HOWTO's and forum threads over the last few days, but I haven't gotten anywhere with this except breaking my xserver repeatedly. ;)

   Can anyone confirm or deny that the fglrx driver works on the ATI 345M? And if it's a deny, can anyone point me in the right direction as far as getting the radeon driver accelerated?

---

### Post by pHluid on 2006-06-04
OK, this is beyond wierd, but... nevermind folks, I got it.

I've installed Dapper twice on this machine, and both times, DRI = No, glxgears FPS in the toilet out of the box.

I have NO idea what was different, but fearing all the horrible horrible things I had done to my xorg.conf file would come back to haunt me (and other things I'd broken) I formatted and reinstalled.

This time? DRI = Yes. 322FPS average in glxgears. Then I did the following in my xorg.conf, just for giggles, to try it with the radeon instead of ati driver:

Section "Device" 
Identifier "ATI" 
VendorName "ATI" 
Driver "radeon" 
VideoRam 65536 
Option "DPMS" 
Option "AGPMode" "4" 
Option "AGPFastWrite" "On" 
Option "EnablePageFlip" "On" 
BoardName "Mobility IGP345m" 
Option "AGPMode" "4" 
EndSection

That errored out the xserver on reboot, of course, because I hadn't changed the Device line under the Screen section to match (Device "ATI")

Once I corrected that, however, I now have DRI = Yes in glxinfo, and averaging 482FPS in glxgears.

Don't ask me to explain why it didn't work out of the box the first two go arounds. But it's working now.

Hope this might help anyone else who has a problem!

---

### Post by gontofe on 2006-10-09
Just to help anyone else who nothing has worked for, I tried to install fglrx, which didn't work, uninstalled it and tried something similar to the above, which also didn't work...

A quick glance at /etc/modules confirmed that fglrx was still there, so I deleted the relevant lines, and now I have 3d acceleration!

---

### Post by GMUDuckman on 2006-10-16
I totally tried those suggestions and neither worked for me! :-( I can't get the stupid thing to work!

---

