---
title: "Random internet stall with Intel PRO/Wireless 4965 AGN"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by Jason_077 on 2009-03-04
Hi guys!

I am quite new in the Ubuntu world and I have to say I love it.
Nevertheless I have an annoying problem with my wireless connection. In the last few days I did a lot of research on Internet and I found that many people are experiencing similar issues.

I have a Toshiba Portege M700 (Tablet) equipped with an Intel PRO/Wireless 4965 AG or AGN. I am running a 2.6.27-13 kernel with the latest version of (proposed) backports available, i.e. linux-backports-module-intrepid 2.6.27.13.16. I kept it updated because I was hoping that the wireless team managed to solve it. Unfortunately the problem still appears.

The problem is that my WPA-secured wireless connection stalls after a random period of time, which may be several minutes to several hours. The network manager does not report anything strange (it keeps saying that the connection is on) but I can't access the network anymore. Moreover, all the processes slow down and even executing a simple 'sudo something' may require several minutes. 

I found that this phenomenon appears more frequently when there is intense wireless traffic (new hosts joining the network, big downloads, etc.). When my connection drops, I can try to restore it in several ways: sometimes it is sufficient to Disable and then Re-Enable the Wireless from the GUI Network Manager. Sometimes it is not enough and I have to remove the iwlagn module from the kernel and the re-add it. Other times (rarely) I need a complete reboot of my machine. 

I report here also the last part of the dmesg output. I found that every time the connection drops I have the message 'iwlagn: Microcode SW error detected'.



[   25.736987] iwlagn 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.737105] iwlagn 0000:01:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   25.737672] firmware: requesting lbm-iwlwifi-4965-2.ucode
[   25.799634] iwlagn loaded firmware version 228.57.2.23
[   26.004189] Registered led device: iwl-phy0:radio
[   26.004397] Registered led device: iwl-phy0:assoc
[   26.004516] Registered led device: iwl-phy0:RX
[   26.004633] Registered led device: iwl-phy0:TX
[   26.169528] NET: Registered protocol family 17
[   27.309966] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: None
[   27.309980] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   55.348613] CPU0 attaching NULL sched-domain.
[   55.348631] CPU1 attaching NULL sched-domain.
[   55.352213] CPU0 attaching sched-domain:
[   55.352223]  domain 0: span 0-1 level MC
[   55.352229]   groups: 0 1
[   55.352239]   domain 1: span 0-1 level CPU
[   55.352245]    groups: 0-1
[   55.352254] CPU1 attaching sched-domain:
[   55.352259]  domain 0: span 0-1 level MC
[   55.352264]   groups: 1 0
[   55.352272]   domain 1: span 0-1 level CPU
[   55.352277]    groups: 0-1
[   56.766533] wlan0: authenticate with AP 00:1c:2e:67:d8:a4
[   56.767783] wlan0: authenticated
[   56.767795] wlan0: associate with AP 00:1c:2e:67:d8:a4
[   56.777630] wlan0: RX AssocResp from 00:1c:2e:67:d8:a4 (capab=0x11 status=0 aid=2)
[   56.777645] wlan0: associated
[   56.817051] cfg80211: Calling CRDA for country: IT
[   64.015675] NET: Registered protocol family 10
[   64.016212] lo: Disabled Privacy Extensions
[   74.096023] eth0: no IPv6 routers present
[   77.410881] wlan0: authenticate with AP 00:1c:2e:67:c9:44
[   77.417105] wlan0: authenticate with AP 00:1c:2e:67:c9:44
[   77.417148] wlan0: authenticated
[   77.417155] wlan0: associate with AP 00:1c:2e:67:c9:44
[   77.424154] wlan0: authenticate with AP 00:1c:2e:67:c9:44
[   77.424182] wlan0: authenticated
[   77.424189] wlan0: associate with AP 00:1c:2e:67:c9:44
[   77.428319] wlan0: RX ReassocResp from 00:1c:2e:67:c9:44 (capab=0x11 status=0 aid=3)
[   77.428330] wlan0: associated
[  126.252538] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 2623.731800] iwlagn: Microcode SW error detected.  Restarting 0x82000000.
[ 2623.755959] iwlagn: No space for Tx
[ 2623.755975] iwlagn: Error sending SENSITIVITY_CMD: enqueue_hcmd failed: -28
[ 2623.755980] iwlagn: SENSITIVITY_CMD failed
[ 2623.964537] Registered led device: iwl-phy0:radio
[ 2623.964588] Registered led device: iwl-phy0:assoc
[ 2623.964627] Registered led device: iwl-phy0:RX
[ 2623.964665] Registered led device: iwl-phy0:TX
[ 2637.150496] mac80211-phy0: failed to remove key (0, 00:1c:2e:67:c9:44) from hardware (-22)
[ 2637.157875] wlan0: authenticate with AP 00:1c:2e:67:c9:44
[ 2637.179284] wlan0: authenticate with AP 00:1c:2e:67:d8:a4
[ 2637.183131] wlan0: authenticate with AP 00:1c:2e:67:d8:a4
[ 2637.183157] wlan0: authenticated
 


Can anyone help me? Is there anything I may try?

I've read that the related kernel panic bug has been fixed (see [https://bugs.launchpad.net/ubuntu/intrepid/+source/linux-backports-modules-2.6.27/+bug/276990?comments=all](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux-backports-modules-2.6.27/+bug/276990?comments=all)). What does it mean? "Fixed" means "solved"? If so, why I am experiencing the same Microcode SW error after the latest kernel and backports updates?

Many many thanks in advance to anyone will help me staying away from the MS world...

J77

---

### Post by nidelius on 2009-03-05
Same issue here on a Zepto Znote 6625WD with INTEL Wireless 4965AGN
WPA personal sometimes hang
WPA Enterprice. terrible.

---

### Post by gnychis on 2009-03-07
I have a Thinkpad x300 with the intel 4965AGN, and I've spent nearly 2 months trying to solve this problem with no luck :(

---

### Post by Jason_077 on 2009-03-09
Thank you for confirming the existence of the problem. Searching the net I found that it is very common.

Does anyone know if this bug affects also the latest beta version of Jaunty? 
Can we hope that at the end of April (foreseen release date for Jaunty) updating our systems will solve the problem?

---

### Post by mbfrog on 2009-03-17
Same problem here.

It seems it could be an overheating issue:

[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1859](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1859)

A workaround *could* be to change the power level. Create a script /etc/network/if-up.d/iwlagn :

```
#!/bin/sh

if [ "$IFACE" = "wlan0" ]; then
	iwconfig wlan0 power on
	# echo 5 >/sys/bus/pci/drivers/iwlagn/0000\:0b\:00.0/power_level
fi
```

I'm currently testing it.  "iwconfig wlan0 power on" sets the power level to 3.  I'll see if it's enough or if I need to enable the second line that explicitely sets the power level to 5.

---

### Post by gnychis on 2009-03-18
> **mbfrog said:**
> Same problem here.

It seems it could be an overheating issue:

[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1859](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1859)

A workaround *could* be to change the power level. Create a script /etc/network/if-up.d/iwlagn :

```
#!/bin/sh

if [ "$IFACE" = "wlan0" ]; then
	iwconfig wlan0 power on
	# echo 5 >/sys/bus/pci/drivers/iwlagn/0000\:0b\:00.0/power_level
fi
```

I'm currently testing it.  "iwconfig wlan0 power on" sets the power level to 3.  I'll see if it's enough or if I need to enable the second line that explicitely sets the power level to 5.

didn't solve my problem, but thanks for the post!

---

### Post by mbfrog on 2009-03-19
> **gnychis said:**
> didn't solve my problem, but thanks for the post!

Well, I've had mixed results: by pushing the power_level to 5 AND making sure the card is properly ventilated (I just lifted the laptop 2 centimeters off the desk), I've had only one stall so far.  That's a big improvement for me.

---

### Post by gnychis on 2009-03-19
I really do not think that my issue is an overheating problem.  I can use the laptop for hours and hours at home without ever seeing a problem, but if I take the laptop to campus, I can't hold a connection for more than 20 seconds.

---

### Post by Jason_077 on 2009-03-20
As for gnychis, I am afraid that my problem does not depend on the overheating issue. I tried the script and I could not resolve it. Again, I figured out that it is (mainly) related to the traffic state of the network. Maybe some received packets make the laptop stall... I have several pc's at home: I can work for hours with my Ubuntu laptop without any problem if it is the only one connected to the WPA-encrypted wireless network, but, if I switch on some other pc's (e.g. a Windows desktop also connected to the wireless) VERY VERY often the Ubuntu laptop stalls. Same thing when I work at my lab.

---

### Post by mbfrog on 2009-03-27
> **gnychis said:**
> I really do not think that my issue is an overheating problem.  I can use the laptop for hours and hours at home without ever seeing a problem, but if I take the laptop to campus, I can't hold a connection for more than 20 seconds.

Just to clarify things, I have experienced two very different problems:

[LIST=1]
[*] At home, with a linksys WRT54G router, and as described in the first post of this thread

> **Jason_077 said:**
>  WPA-secured wireless connection stalls after a random period of time, which may be several minutes to several hours. The network manager does not report anything strange (it keeps saying that the connection is on) but I can't access the network anymore.

I've noticed that this always occurred under heavy network loads (bittorrent). I more or less fixed this one by adjusting the power level (i.e. the frequency of occurrence is dramatically lower).


[*] At work, in a very crowded WiFi environment (I can see at least 12 APs) and a DrayTek Vigor2930 (either in g or n mode), it can't hold the connection longer than 2 minutes and most of the times it ends up in a deadlock and hard reboot of the laptop.  No solution for that one.  I've tried a Dell cheap-o WiFi card (broadcom) with no more luck.
[/LIST]

It is very unlikely that these two problems are related, and I don't think that the second one can be fixed anywhere else than in the kernel drivers or firmware.

---

### Post by gnychis on 2009-03-30
I filed a bug:
[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1953](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1953)

---

