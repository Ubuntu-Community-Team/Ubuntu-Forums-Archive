---
title: "ATI VisionTex X1300 install"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by Neondog82 on 2007-12-24
As like everyone else I am having problems installing my video card. I am running updated 7.10 64 bit Gusty Gibbon. I have read the tutorials, and performed a couple of them. I am not sure if I messed things up along the way or not but here goes what I have done. First I tried to use the Restricted driver manager. After a reboot Ubuntu went into low graphics mode using only my on board video. I tried to configure the PCI card but it was not showing there. So now my on board video is messed up, everything is way bigger than before. Anyways I went back into the Restricted driver manager and it said enable, but not in use? So then I followed the tutorial here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) , but that failed to work after going through all the steps. Then I checked the hardware manager, the ATI card is showing up in there. Then I ran "lspci" and my ATI card shows up there. Then I ran "lsmod" and the fglrx module shows up there. However when I go to System/Admin/Screens... My graphics card is not there. After that I went and installed envy, and ran that, but still it does not work. every time I reboot I always go into "low graphics mode" using my on board video. And my restricted driver manager does not work anymore, when i try to open it, nothing happens. Is anyone willing to walk me through the process of finding out what the problem is, and then helping me fix it?

---

### Post by Neondog82 on 2007-12-25
Does it matter if I have the on board VGA cable plugged in to the computer and monitor and the DVI cable from the ATI card plugged into the monitor at the same time? Will DVI be supported, or do I need to use the VGA cable from the ATI card? I managed to get the restriced driver program working, and now it shows the fglrx driver enabled and in use. and I fixed my on board video. well I enabled the restricted driver at last restart, I have not been back to the computer.

---

