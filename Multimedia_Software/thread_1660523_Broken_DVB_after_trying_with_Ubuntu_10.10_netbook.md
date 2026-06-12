---
title: "Broken DVB after trying with Ubuntu 10.10 netbook"
date: 2011-01-05
forum: Multimedia Software
---

### Post by David_UK on 2011-01-05
Dual boot Win7 & Ubuntu netbook 10.10 - Acer Aspire One D250 Netbook.
Hauppauge Nova-T USB DVB TV stick.

1) Stick + WinTV works fine under Win7 when new.
2) Tried it under Ubuntu - demsg reports stick detected in cold state, then firmware downloaded, and stick detected in warm state.
3) Stick does not appear to do anything with caffeine or meTV.  I can scan for channels but none are found.
4) Stick no longer works under windows and WinTV - I can scan for channels but none are found.

I'm guessing then that Ubuntu has automatically and silently downloaded and updated the firmware on the stick (can that happen?  Isn't that dodgy?) and the firmware is no good - for either operating system.

I'll settle for restoring it to it's original state so I can at least use it under windows - any suggestions please?

Thanks

---

### Post by BicyclerBoy on 2011-01-05
To clarify..

The nova dvb-t stck (& the PCIe cards) reload firmware on cold start always.
Windoze driver does the same thing.
Rebooting into smopnim will restore the dvb stick until power off.

This process is common to lots of gear like wifi etc..

This means the firmware updates can be/are controlled/linked to the driver updates.

So you need the firmware packages installed.
"linux-firmware-nonfree" & "linux-firmware"
 
The Ubuntu firmware could be out of date w.r.t. windoze driver.

Check the support on LinuxTV website or MythTV forums.

---

### Post by David_UK on 2011-01-06
> **BicyclerBoy said:**
> So you need the firmware packages installed.
"linux-firmware-nonfree" & "linux-firmware"
BicyclerBoy
Many thanks for your reply - linux-firmware was already installed, but I had to add linux-firmware-nonfree.  
After reinserting the stick, firmware was updated to dvd-usb-dib0700-1.20.fw, and works in caffeine.  
Even the remote will adjust sound and shut down the pc.  
It works fine under Win7 now too.
Thanks for your help!

---

