---
title: "cannot get WMP600N card workin"
date: 2011-12-06
forum: Networking &amp; Wireless
---

### Post by nethero on 2011-12-06
I have a linksys WMP600N card.  I'm running 10.04.  I removed my old wireless card and inserted the WMP600N into the pci slot and restarted my computer.  I have the rt2860sta kernel module insalled (came installed with 10.04).  I can see my card when I type lspci -v and when I type lsmod I can see the rt2860sta module is loaded.  However, I can't see any wireless networks.  Is there a command I'm missing?  Thanks.

Edit:
I can see my interface when I type sudo iwconfig.  The interface is called ra0.  I tried sudo ifconfig ra0 up and I got the message  "SIOCSIFFLAGS: Operation not permitted"  So does this mean my card is recognized and the drivers are loaded properly?  Am I missing a config edit somewhere?

Edit:
running dmesg gives me this....
```
[   14.296214] lp0: using parport0 (interrupt-driven).
[   14.343342] rt2860 0000:01:06.0: enabling device (0000 -> 0002)
[   14.343881] psmouse serio1: ID: 10 00 64
[   14.343909] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   14.343918] rt2860 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   14.344168] 
--
[   16.839198] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
[   16.844290] !!! rt28xx Initialized fail !!!
[   16.846664]   alloc irq_desc for 26 on node -1
--
[   17.282849] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
[   17.298491] !!! rt28xx Initialized fail !!!
[   22.808881] cdrom: This disc doesn't have any tracks I recognize!
--
[  141.911182] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
[  141.916264] !!! rt28xx Initialized fail !!!
[  145.339930] RX DESC f4793000  size = 2048
--
[  145.749155] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
[  145.754247] !!! rt28xx Initialized fail !!!
[  189.645338] RX DESC f4793000  size = 2048
--
[  190.055024] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
[  190.060110] !!! rt28xx Initialized fail !!!
[  749.650623] RX DESC f4793000  size = 2048
--
[  750.059769] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
[  750.064846] !!! rt28xx Initialized fail !!!
[  750.069412] RX DESC f4793000  size = 2048
--
[  750.478989] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
[  750.484063] !!! rt28xx Initialized fail !!!
[  750.485327] forcedeth 0000:00:08.0: irq 26 for MSI/MSI-X
```

Any ideas?

EDIT (yet again)
Okay I installed the compat-wireless-lucid-generic package and the card seems to work okay.  However it also knocks out my audio.  When I play a wave/mp3 I just hear static.  When I put my old wireless card back in there is no static but the sound is very low.  Now I have to fix my audio card problems.  I'm about the give up on this card.  Also, my transfer rates haven't increased all that much.  I was able to connect to my router at 3300 Mb/s using my wireless g card, with this card my connection is only 8800 Mb/s.  Not exactly what I was expecting.

---

### Post by nethero on 2011-12-07
On a side note I think I see why the upgrade to wireless N did not increase my speed that much.  Here is an article by smallnetbuilder that covers the throughput hit that is taken when a 802.11n client connects to a router servicing 802.11b/g clients.  The throughput is reduced by 50% to 80%.  The router I'm connecting to still has a few 802.11g clients associated with it

Edit:
Forgot to link the article :D...
[http://www.smallnetbuilder.com/wireless/wireless-features/30224-add-dont-replace-when-upgrading-to-80211n](http://www.smallnetbuilder.com/wireless/wireless-features/30224-add-dont-replace-when-upgrading-to-80211n)

Another good one for people having trouble getting wireless N speeds...
[http://www.smallnetbuilder.com/wireless/wireless-basics/30664-5-ways-to-fix-slow-80211n-speed](http://www.smallnetbuilder.com/wireless/wireless-basics/30664-5-ways-to-fix-slow-80211n-speed)

---

### Post by nethero on 2011-12-08
Okay I give up.  This card only works when I install linux-backports-modules-wireless-2.6.35-lucid-generic.  However, sometimes when I start or restart my computer the audio doesn't work, I just get a hissing noise when I try to play a audio file.  This never happened with my old card.  I do not know whether this is a result of the WMP600N or the linux-backports-modules-wireless-2.6.35-lucid-generic package.

---

### Post by nethero on 2011-12-12
Okay problem solved.  My speaker cable input was the problem, the connection on it was going bad.  The cable was bent because of the extra antennas in the new sound card.  The old sound card did not have many antennaes so the cable did not have to bend.  I replaced the cable and everything works fine.  Grrrrr.  I wish I'd thought to check this earlier.  I've been going nuts trying to fix this.  It never ceases to amaze me the number of times the (seemingly) most complicated problems have the simplest solutions.

---

