---
title: "ndiswrapper in dapper"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by Carandol on 2006-06-12
Getting my wifi card to work in Breezy took quite a while, so I carefully wrote down how I did it, in case I needed to do it again. I'm now setting up the same computer to give to someone else, and decided to wipe the drive and install Dapper. Bad move! I can't get the wifi card to work, *again*! 

The card is a D-Link AirPlus G+ DWL-G520+. My original notes went like this, but I've noted where the problems are:

> 1. Install firmware: Copy file FwRad16.bin_1.2.1.34 to hard drive then type:

sudo cp path/FwRad16.bin_1.2.1.34 /lib/hotplug/firmware/

First stumbling block - that directory doesn't exist any more. I've tried putting it in /lib/firmware, but don't know if that's right.

> 2. Install ndiswrapper-utils in Synaptic Package Manager

3. Copy D-Link WinXP drivers to hard drive, then type:

sudo ndiswrapper -i GPLUS.inf
sudo ndiswrapper -l
sudo ndiswrapper –m
sudo modprobe ndiswrapper

4. Configure /etc/network/interfaces thus:

mapping hotplug
	script grep
	map wlan0

iface wlan0 inet dhcp
wireless-essid <my essid>
wireless-key2 <my wireless key>
wireless-defaultkey 2
wireless-keymode restricted


All fine so far, but then:

> 5. add the following lines to the end of etc/hotplug/blacklist:

#allows wifi card to work
acx_pci

/etc/hotplug/blacklist no longer exists! 

Any clues as to what I should be doing here gratefully accepted!

---

### Post by az on 2006-06-12
Well, first off isn't the native linux driver that you want to blacklist improved?  I think it is supposed to work fully, if I am not mistaken.  Maybe try that first?

And to blacklist, use
/etc/modprobe.d/blacklist 
and add

blacklist acx_pci

I dunno about the firmware.

---

### Post by Carandol on 2006-06-13
Dapper detects the card, detects the wifi signal, but refuses to connect to the network. I know the network parameters are right, so it must be either the firmware or the driver. Or both, like it was in Dapper. Thanks for the blacklist info, I'll see what I can do!

---

### Post by Carandol on 2006-06-13
Hmm, still no luck. I'm not entirely sure the firmware's in the right place, or has the driver I'm trying to blacklist changed its name? Any help gratefully accepted!

---

### Post by Carandol on 2006-06-13
Ha! Done it. Apparently the default ACX111 firmware provided is wrong, and it needs to be swapped. It's all explained at [http://acx100.sourceforge.net/wiki/Firmware](http://acx100.sourceforge.net/wiki/Firmware) (the last paragraph). Just copy the correct files into the default directory, reboot, and bob's your uncle!

---

