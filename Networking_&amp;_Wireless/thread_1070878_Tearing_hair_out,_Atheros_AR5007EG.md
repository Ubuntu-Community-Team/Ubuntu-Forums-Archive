---
title: "Tearing hair out, Atheros AR5007EG"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by andy_cowman on 2009-02-15
Ok this is getting silly, have spent all day trying to sort out my wifi but its having none of it. Worked perfectly on 8.04 (Ubuntu and Xubuntu) but now have switched KUbuntu 8.10. Loving the system but no Wifi!!

Laptop is an ASUS X50RL and LSPCI -V returns this:


02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI ExpressAdapter (rev 01)
        Subsystem: Device 1a3b:1026
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fa9f0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k
        Kernel modules: ath5k, ath_pci

This is after attempting to install the latest Madwifi snapshot and then removing it, and following the instructions from the release notes to install from Backports the module with ATH5k. Once I did that I gained another item in the Restricted Drivers Manager which is active. Screenshot attached at bottom. 

Now as far as I can see the card is found and using the ath5k driver, but also attempting to use ath_PCI?? But I have blacklisted that in /etc/modprobe.d/ 

I am getting a Wlan0 interface but can not find any AP when scanning. On 8.04 it appeared as ath0 if that means anything? When I try and turn the card on or off using the switch the light flicks but doesn't stay on?

ANy suggestions?! Really could do with some help. I am thinking that it should work but that its trying to use two modules maybe?Not sure how to proceed though. 

Thanks
Andy

[IMG]http://www.andycowman.co.uk/albums/userpics/10001/snapshot1.png[/IMG]

---

### Post by andy_cowman on 2009-02-15
Ok I tried the Madberry idea found [here]("http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/") and now my lscpi -v read out is this:

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Device 1a3b:1026
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fa9f0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k
        Kernel modules: ath5k


Difference is its now only trying to use ath5k however my switch on the front still doesn't do anything and whilst Ifconfig shows the interface i can not scan. 

Help!?

---

### Post by andy_cowman on 2009-02-17
Right

Well I got there in the end by myself. Should anyone have a similar issue using the Asus X50RL laptop then I solved it by installing from the Backports the driver and fully updating. 

My laptop doesnt actually have bluetooth but was loading modules so I blacklisted as below in /etc/modprobe.d/blacklist

blacklist rfcomm
blacklist bnep
blacklist sco
blacklist l2cap

I then un blacked listed the following as couldn't remember if it was me who added them!

# blacklist ath_hal
# blacklist ath_pci


then I discovered this folder
/sys/devices/platform/asus-laptop

and the file wlan and bluetooth. Bluetooth was set to a 1 (turning it on but its not there!) and wlan a 0 which turned it off. THis file resets everyboot. Very annoying.

So I did this, as root edit /etc/rc.local and add the following lines directly above exit 0:

echo  1  >  /sys/devices/platform/asus-laptop/wlan
echo  0  >  /sys/devices/platform/asus-laptop/bluetooth

Now it should work!!

---

### Post by deg12 on 2009-02-19
Does it work? I have the same laptop with the same problem. Keep me up to date please.

---

### Post by andy_cowman on 2009-02-23
Yes its all working! Only had it forget itself once and not switch the wlan file to a 1. But just edited it manually and then all good. Reception and speed are fine, reliabilty also.

Good luck

Andy

---

