---
title: "Wake on LAN stopped working in 12.04"
date: 2012-07-11
forum: Networking &amp; Wireless
---

### Post by parish on 2012-07-11
Was working fine in 11.10. I upgraded to 12.04 and it hasn't worked since.

I've read of problems with RealTek-based NICs but this is an Intel PRO/1000

Output from ethtool (ignore the fact the hostname is kubuntu, I am running Ubuntu)

```
root@kubuntu:~# ethtool eth1
Settings for eth1:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: umbg
	Wake-on: g
	Current message level: 0x00000007 (7)
			       drv probe link
	Link detected: yes
```

I've not changed any settings since upgrading, either in Ubuntu or the BIOS.

Anyone any ideas?

---

### Post by mantrius on 2012-07-12
I have the same problem with a PRO/1000 card (82541PI) and haven't been able to find a solution.  Wake on lan works fine in 11.10 (clean 11.10 install) but does not in 12.04 (clean 12.04 install) and nothing has changed in the bios.  DMESG reports that I'm using e1000 driver version 7.3.21-k8-NAPI. *edit* I should probably mention that this is for both S4 and S5 states.

---

### Post by parish on 2012-07-12
> **mantrius said:**
> I have the same problem with a PRO/1000 card (82541PI) and haven't been able to find a solution.  Wake on lan works fine in 11.10 (clean 11.10 install) but does not in 12.04 (clean 12.04 install) and nothing has changed in the bios.  DMESG reports that I'm using e1000 driver version 7.3.21-k8-NAPI.

Same driver version here.

This is doubly annoying as I bought the Intel because my mobo has an on-board RealTek based NIC that had problems in an earlier version of Ubuntu (would ony connect at 10Mbit) and I read that there are still problems with the Realtek driver.

I really need WOL as I use the RAID array for backing up my Mac using Carbon Copy Cloner which runs a script to wake the Linux box up so I don't have to switch it on manually.

EDIT: Just tried re-enabling the Realtek on-board and it both connects at 1Gbit and WOL works with it :)

---

### Post by mantrius on 2012-07-12
I've gone back to using the built on Intel 82579V adapter which uses e1000e (thankfully it looks like they've fixed the issues it had with maintaining a link) and I can now wake on lan from S4.  Wake from S5 is still broken with this adapter when it should work fine as the bios are configured to allow wake from S4/S5.  Either way I'd like to find a resolution for the pro/1000 adapters as I've had far fewer problems with that card.

---

### Post by mantrius on 2012-07-18
> **parish said:**
> Same driver version here.

This is doubly annoying as I bought the Intel because my mobo has an on-board RealTek based NIC that had problems in an earlier version of Ubuntu (would ony connect at 10Mbit) and I read that there are still problems with the Realtek driver.

I really need WOL as I use the RAID array for backing up my Mac using Carbon Copy Cloner which runs a script to wake the Linux box up so I don't have to switch it on manually.

EDIT: Just tried re-enabling the Realtek on-board and it both connects at 1Gbit and WOL works with it :)

I ended up purchasing an Intel 82572GI (Intel EXPI9400PT) PCIe nic as the onboard still won't boot from S5 (though S4 works just fine).  So far the new 82572GI resumes from S5 with no problems just like my old 82541PI.  There must be some incompatibility with the e1000 driver and 12.04 with regards to wake on lan with these 82541PI cards but I'm not experienced enough to figure out where.

---

### Post by rempatterson on 2012-08-30
I have a WOL problem with an Intel based machine running 12.04.  All my AMD machines are fine.  I'd love to find a solution other than getting another AMD box.

---

