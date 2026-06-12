---
title: "Lucid Lynx not recognizing TP-Link USB wireless"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by ap.se on 2010-06-13
established newbie, likely having a software setup problem... i scouted around for sometime online so I do not expect there is a similar thread, forgive me if there is...

my card is not recognized in any way by ifconfig or iwconfig as shown below, but is visible via lsusb. It is 54Mb usb, and has a detachable antenna with the Atheros chipset shown below. I have removed (by #) the ath_pci from the blacklist under /etc/modprobe.d but cannot seem to start this still.  I used compat-wireless-2010-06-01 (06-12 appeared to have errors I could not easily overcome). The lspci -nn command only shows my internal broadcom which I am not currently using. My goal is to do wireless research so I need the atheros (among others)...

my hw: Dell series n, TP-Link's TL-WN422G USB wireless stick

$ lsusb | grep Ath
Bus 001 Device 004: ID 0cf3:1006 Atheros Communications, Inc. 

$ lsmod | grep ath
ath9k                  71145  0 
ath9k_htc              35456  0 
ath9k_common            5687  2 ath9k,ath9k_htc
ath9k_hw              280920  3 ath9k,ath9k_htc,ath9k_common
compat_firmware_class     6522  1 ath9k_htc
ath                     8009  3 ath9k,ath9k_htc,ath9k_hw
mac80211              231300  3 ath9k,ath9k_htc,ath9k_common
cfg80211              146028  5 ath9k,ath9k_htc,ath9k_common,ath,mac80211
led_class               2864  3 ath9k,ath9k_htc,sdhci

$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.
vmnet1    no wireless extensions.
vmnet8    no wireless extensions.
(note: yes running vmware at startup)

$uname -r
2.6.32-22-generic

Thoughts? Seems to me that their should only be one ath9k driver, but several are loaded. Are all required for functionality perhaps?

thx, ap

---

### Post by bobnutfield on 2010-06-13
I probably can't solve your problem, but it might be a clue to know WHICH Atheros chipset is involved.  The ath5k and ath9k module does work for the vast majority of Atheros chipsets, but there are still some that will not work with those modules.  Open a terminal and do:

> sudo lshw -C Network

Note which Atheros chipset is shown and that might help you google it or someone else to know of a quick fix.  I myself have been trying to help a friend install Ubuntu on his laptop only to find that it has the Atheros 5001x+ chipset and there are some of those that will not work.  As I understand it, in those cases the old solution used to be to use the madwifi drivers, but I am not sure about now.

---

### Post by ap.se on 2010-06-13
bob, thx - I don't see it. Im going to load this on XP to test if the hardware even works. seems to me that the hardware can read the pci interface like the phy layer chip (pci) but not the full Atheros chipset (which i assume is an fpga) itself. I looked at all the other posts and seem to believe that I did not also try moving the driver, but I thought that it would be covered in compat-wireless and may need to check to see if the ath9k is is under /lib/...


> **bobnutfiel       bus info: usb@1:3d said:**
> I probably can't solve your problem, but it might be a clue to know WHICH Atheros chipset is involved.  The ath5k and ath9k module does work for the vast majority of Atheros chipsets, but there are still some that will not work with those modules.  Open a terminal and do:



Note which Atheros chipset is shown and that might help you google it or someone else to know of a quick fix.  I myself have been trying to help a friend install Ubuntu on his laptop only to find that it has the Atheros 5001x+ chipset and there are some of those that will not work.  As I understand it, in those cases the old solution used to be to use the madwifi drivers, but I am not sure about now.

---

