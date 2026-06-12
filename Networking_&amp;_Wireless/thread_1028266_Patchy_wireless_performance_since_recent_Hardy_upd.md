---
title: "Patchy wireless performance since recent Hardy updates"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by impalerau on 2009-01-02
I've been experiencing very patchy wireless performance on 2 machines, both running the rt61pci driver since applying a large Hardy update about a week ago.  Machines running ndiswrapper and other drivers were not affected.

One of the affected machines was a laptop which I've upgraded to Intrepid.  It's running a different driver after the upgrade and is OK now.  The other is a desktop which I'm not ready to upgrade yet.  It runs my torrent client, so I really need to get this fixed.  It normally uploads at a steady 82 kB/s for 18 hours a day and drops to 72 kB/s while downloading at 160 kB/s for the remaining 6 hours.  It's been running for the best part of a year 24/7 and never had network performance problems before.

This is what I've observed since the upgrade:

- performance seems to fluctuate between 2 states: 1) normal, very steady at the throttled rates or 2) very variable but no more than about 30 kB/s when uploading and about the same speed when downloading with the upload dropping to just a trickle

- the periods of normal performance have become less and less frequent

- left on automatic, nw-applet show connection speed as either 1 or 2 Mb/s

- if the speed is manually set to 24M or 54M using iwconfig, it reconnects ok and shows the appropriate connection speed in nw-applet but has no affect on performance

- I know it's not an ISP issue because other boxes are getting normal download speeds.  

- surfing into my modem or access point from the affected machine takes the best part of a minute while from other boxes it's almost instantaneous, so the problem is definitely internal

- another strange symptom is that nm-applet on the affected box shows 2 networks of equal strength, 1 with my ESSID and the other anonymous.  Running iwlist scan on that box only shows my network.

- running iwlist scan on the laptop that I'm typing this on which is only 2 metres away shows my network on channel 11 and a much weaker anonymous network on channel 6

Can anyone shed any light on what's going on?

---

### Post by k_aneda on 2009-01-02
I may be seeing something similar, however only on certain channels.

My home AP for example on Channel 7 has not given me any problems, however I've just spent 2 days troubleshooting the APs at work on Channel 11 and I still see occasional patchy performance.   It's not a drop-out, but the performance drops enough that it causes disruptions with applications.

Is it too much hassle for you to switch channels (set it to 7 or 4 or something) and see how it goes for a few hours?

Also what are your wireless cards?

---

### Post by impalerau on 2009-01-02
Thanks for the heads up k_aneda.  I've been doing the channel changing thing for a few days now and nothing seemed to make any difference.  The good boxes worked equally well on all channels and the bad ones equally badly :)

The card I've been doing battle with tonight is a D-Link DWL-G510 PCI card.  The other culprit was a TP-Link TL-WN510G PCMCIA card.  Well how about that?  Seems to be a pattern there :)

Both cards worked well straight out of the box when I got them about a year ago.  Both went haywire on Hardy about a week or so ago.  The TP-Link came good on Intrepid.

Another peculiar thing while I was waiting for a reply...  Thought I'd install a NIC in the box and put up with a cable running through the middle of the lounge room while getting this sorted.  I tried 3 different NICs both alongside the wireless card as well as replacing it, and the machine just wouldn't boot.  I'd get the log on screen and the disk would start chattering as normal, then silence and finally a blank, white rectangle would appear in the top right corner of the screen.

I finally replaced the D-Link with an old Netgear WG311v3 that I found while looking for a NIC.  Installed ndiswrapper from the old 8.04 installation CD (no network connection) and it's running beautifully.  Funny thing is I ditched the Netgear card in the first place to get one that worked with Ubuntu out of the box.  Go figure.

Would love to know what the problem is with the other one though, AND why it won't boot with a normal NIC.

Anyway, almost 3am here so I'm off to bed.  Torrent client is throttled up to 480 kB/s to make up for the last few nights of lost downloads.  Kids will have movies to watch tomorrow  :)

---

### Post by k_aneda on 2009-01-02
Good to hear all OK - though now it means I have more work troubleshooting my wi-fi @ work on Monday ;)

yes, 3.42am and it's freezing in Sydney...

---

