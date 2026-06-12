---
title: "RT 5390 wireless card"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by DaimonTheFallen on 2011-09-30
First off, I have Ubuntu installed on a HP Pavilion 10.1" Netbook featuring Intel Atom Dual Core Processor N570 (210-3070CA). It has a Ralink Device 5390 Wireless Card which needs to be configured before I can use wireless internet.

I have followed the steps outlined here:

> Download the linux driver (RT5390PCIe) from Ralink.
Extract it.  The files will be extracted to 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO folder.
Download all the patches except the x64_86 patch, assuming you have a 32-bit system, from opensuse website.
Copy the patches to the folder – 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
Goto the folder.
Make the following change in  /os/linux/config.mk file – HAS_ANTENNA_DIVERSITY_SUPPORT=y (originally was n)
Now run the following commands in terminal:
patch -p0 < rt5390sta-2.4.0.4-config.patch
patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch
patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch
patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch
patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch
patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch
sudo su
cp RT2860STA.dat RT5390STA.dat
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA
make clean
make
make install
modprobe rt5390sta
exit

But when I do a iwconfig in terminal, the wireless card is not recognized at all. What am I doing wrong?

---

### Post by WasMeHere on 2011-09-30
In this thread they reported success: [_ubuntuforums.org/showpost.php?p=11206409&postcount=82_]("http://ubuntuforums.org/showpost.php?p=11206409&postcount=82")
Good luck
Olle

---

