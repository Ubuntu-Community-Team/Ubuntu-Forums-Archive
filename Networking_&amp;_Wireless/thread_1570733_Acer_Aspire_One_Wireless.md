---
title: "Acer Aspire One Wireless"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by hockeytux on 2010-09-08
Ive got an Acer Aspire One with 10.04 on it...however my wireless connection stopped working.

Checking other posts related to the same issue on different makes I tried 'rfkill unblock all' and other suggested options to no avail. The Enable Wireless option is still deactivated and greyed out.

Any ideas?

---

### Post by krimzonstarr on 2010-09-08
Which model of AAO are you using?

I have an Acer Aspire One ZG5, and my wifi has worked OOTB with Karmic, Lucid, Mint Isadora, Lucid Puppy, and PinguyOS (only ones I've tried recently).

---

### Post by hockeytux on 2010-09-09
The same... a ZG5. My wireless worked OOTB with Lucid as well but only for a day. I havent changed anything which makes it ever more strange. It just stopped working and the enabling option in the menu is greyed out since then...

---

### Post by chili555 on 2010-09-09
First, let's check what driver it requires. We'll try to manually load it and see if it improves. Please post:```
sudo lshw -C network
```If you need to write it down to post it, just post the part related to wireless.

---

### Post by krimzonstarr on 2010-09-09
When I first installed Ubuntu and wiped Windows XP off my ZG5, my wireless wouldn't work either. After hunting and hunting for a solution: I toggled the wifi switch on the front base of my netbook, and rebooted. Worked perfectly. It seemed that during the Ubuntu install, my wifi radio had turned itself off. Since there was (still isn't) and on-screen notification when that switch is toggled in any distro I have tried, I never realized it.

To this day, if I hit that switch, I have to reboot, hit it again, then reboot. Thankfully, I haven't hit it in a LONG time =)

So, try toggling your dongle, and rebooting!

---

### Post by hockeytux on 2010-09-12
> **chili555 said:**
> First, let's check what driver it requires. We'll try to manually load it and see if it improves. Please post:```
sudo lshw -C network
```If you need to write it down to post it, just post the part related to wireless.

description: Wireless Interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
version: 01
serial: 00:22:69:30:97:e4
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath5k




An Ath5k driver then...

---

### Post by chili555 on 2010-09-12
You have an interface, wlan0 and a driver, ath5k. Are there networks showing in Network Manager? How about:```
sudo iwlist wlan0 scan
```What does this tell us?```
dmesg | grep -e wlan0 -e ath5k
```

---

### Post by jsredna62 on 2010-12-28
> **chili555 said:**
> You have an interface, wlan0 and a driver, ath5k. Are there networks showing in Network Manager? How about:```
sudo iwlist wlan0 scan
```What does this tell us?```
dmesg | grep -e wlan0 -e ath5k
```

Since hockeytux didn't answer, and I have  exactly the same problem and exactly the same computer I hope that someone can help me.
If I type ```
 sudo iwlist wlan0 scan 
``` I get:
wlan0     Interface doesn't support scanning : Network is down

And if I type ```
dmesg | grep -e wlan0 -e ath5k
``` I get this:
[    8.722026] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.722073] ath5k 0000:03:00.0: setting latency timer to 64
[    8.722176] ath5k 0000:03:00.0: registered as 'phy0'
[    9.922252] Registered led device: ath5k-phy0::rx
[    9.922341] Registered led device: ath5k-phy0::tx
[    9.922352] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   10.438403] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Hopefully someone can help me, I'm a beginner at Ubuntu

---

### Post by Alessandro Allegri on 2010-12-30
Hi everyone.
I have an Asus Eee901 netbook working Lucid.
Very same problem with the same driver. 
Same dmesg too: link is not ready.

Quite curious to see what's to be done now...

---

### Post by demauk on 2011-01-31
I have the same problem. Ubuntu 10.10, AspireOne ZG5, wlan0, ath5k.

I can actually scan for networks, though.

But the dmesg says the same: ADDRCONF(NETDEV_UP): wlan0: link is not ready.

Help!

---

### Post by playaz on 2011-04-29
Did anyone manage to find a fix for this??

I have the same issue albeit just updated to newer Ubuntu 11.04 - but the same problems :(

---

### Post by Tom_T on 2011-05-03
Hi

I have an Acer Aspire One D150, my wireless has worked fine with Ubuntu for as long as I can remember..

Now when I boot up, it just sits there looking like it's trying to connect, but it never does..

If I disable wireless or networking via the 'wireless Icon' then re enable it, it connects straight away and works well...

Any way to get this working properly ?

Thanks

---

### Post by spur on 2011-05-03
I have an Aspire one Zg5. I installed Ubuntu 32bit from alt install CD, using Wubi. 
I have successfully connected my wireless router (shared Internet) and my usb stick. Different Internet accounts for both. The wireless router is a Belkin N+ and the usb stick is for Iinet prepaid. (Huawei E1762). No problems with either. I like the ability to switch one off as I use the router connection at home and the usb when camping, so I installed the switcher program (forget what it is called).
For those in Australia the number for Iinet is *99# and the APN you need to put in is 'iinet' .
I hope this helps as I had been very frustrated trying to get this set up on 10:10, but 11:04 it worked straight away.:D
A little explanation:- the wireless router is cable connected to my main computer which runs Kubuntu 11:04. The connection to the net-book is wireless.

---

