---
title: "Wireless worked under 5.04 but not 6.06"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by steves on 2006-06-03
This /was/ going to be my first forray into using ubuntu as my primary OS, but it got sidetracked.

I had previously recovered some stuff off of a dying windows drive using the only ubuntu cd I had laying around, 5.04.  I got the wireless card working fine with ndiswrapper via:

```
ndiswraper -i mrv8k51.inf
modprobe ndiswrapper
```

and then it would appear in my "Networking" control panel.

With Dapper, I can't seem to manage to get it working, even though everythign seems fine when I type ndiswrapper -l.  I got through all of the steps and the card doesnt appear in the Networking control panel and doesn't appear when I type iwconfig.  Could it be that my card only works with the version of ndiswrapper found on the 5.04 disc?

For reference, I'm trying to use a D-Link DWL-G510 card that has a Marvell W8300 chipset.  I think I read somewhere that this card should be supported natively, but I don't know how to get it working without ndiswrapper. The card wasnt listed in the Networking control panel prior to ndiswrapper installation, either.

The card is definately working.  I am using it to post this message via windows as we speak. 

Any help would be appreciated.

---

### Post by steves on 2006-06-03
Could it be possible that my system is trying to use the MadWiFi drivers?  They are listed when I:
```
modprobe -l | grep madwifi
```

---

### Post by Lambert on 2006-06-03
Marvell chipsets are not supported natively in Linux, you have to use ndiswrapper.

madwifi doesn't tell much as the driver name will be ath_pci. Grep for this.

run this command and it should list the driver bound to the device. (not in all cases does it though)

```
lshw -C network
```

You will see a line Capabilities:
In that line you will see something like driver=XXXX if there is one bound to the device.

---

