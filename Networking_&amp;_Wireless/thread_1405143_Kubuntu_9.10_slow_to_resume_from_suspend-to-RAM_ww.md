---
title: "Kubuntu 9.10 slow to resume from suspend-to-RAM w/wifi?"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by josh2112 on 2010-02-12
My laptop has an issue when resuming from suspend-to-RAM.  Upon opening   the laptop lid, the screen is black for several seconds (sometimes up to 30). The mouse pointer is on the screen and can be moved around, seeming to indicate that the resume operation has completed, but the Unlock Screen window doesn't appear right away.  No amount of mouse or keyboard input will make it appear, it just pops up randomly after some number of seconds.

Checking dmesg the other day, I found this:

[ 1277.432940] PM: resume devices took 2.844 seconds
[ 1277.433310] PM: Finishing wakeup.
[ 1277.433311] Restarting tasks ... done.
[ 1277.921392] Registered led device: iwl-phy0::radio
[ 1277.921414] Registered led device: iwl-phy0::assoc
[ 1277.921445] Registered led device: iwl-phy0::RX
[ 1277.921467] Registered led device: iwl-phy0::TX
[ 1277.988292] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1277.989513] r8169: eth0: link up
[ 1278.000966] /dev/vmnet: open called by PID 1314 (vmnet-bridge)
[ 1278.000978] /dev/vmnet: hub 0 does not exist, allocating memory.
[ 1278.001016] /dev/vmnet: port on hub 0 successfully opened
[ 1278.001027] bridge-eth0: up
[ 1278.001031] bridge-eth0: attached
[ 1284.011187] wlan0: authenticate with AP 00:1d:7e:96:60:cc
[ 1284.013010] wlan0: authenticated
[ 1284.013017] wlan0: associate with AP 00:1d:7e:96:60:cc
[ 1284.015644] wlan0: RX AssocResp from 00:1d:7e:96:60:cc (capab=0x411 status=0 aid=6)
[ 1284.015649] wlan0: associated
[ 1284.035872] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

Notice the 6-second gap between "bridge-eth0: attached" and "wlan0: authenticate".  I believe this is exactly the period where the screen is black.  So it seems that the wireless network configuration is blocking the Unlock Screen dialog from appearing.

Sure enough, when wireless is disabled, there is never a delay - the unlock screen window appears as soon as I open the lid!

So... why is this happening and how do I fix it?  :confused:

Vitals:
Kubuntu 9.10 Desktop x86
HP Pavilion dv6500t
Intel Core2 Duo, ICH8 chipset
Wireless: Intel 4965 A/G/N

---

### Post by Diemer on 2010-02-16
Hi,

I am having the exact same problem since my upgrade to Kubuntu 9.10 a few months ago.

My MSI Wind Netbook takes several seconds to show me the password prompt to unlock the screen after resume from suspend-to-ram. I also have a feeling that this is related to WiFi. Haven't really looked into it much, but I do find it annoying.

Any Ideas what could be wrong?

---

### Post by Diemer on 2010-02-16
This bug seems to be related:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/483429](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/483429)

---

### Post by lodp on 2010-02-21
My laptop behaves exactly the same since the 9.10 kubuntu update. I noticed that there's no delay if it's been suspended only a couple of minutes, but if resumed after a longer period, there's a delay of 20 sec minimum.

---

