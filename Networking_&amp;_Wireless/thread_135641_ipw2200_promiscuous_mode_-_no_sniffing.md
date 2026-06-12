---
title: "ipw2200 promiscuous mode - no sniffing"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by v4q3r0 on 2006-02-24
:-k I've got a Dell Latitude D610 with the ipw2200 wireless card inside.  I've updated the driver to:

[FONT="Courier New"]
[4294705.659000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294705.659000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294705.661000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[/FONT]

When I run Ethereal as ROOT, I can NOT sniff traffic other than some cisco packets, and all of my own traffic going and coming.  I was wanting to sniff traffic in the "air" for a class project (to show that email, aim, etc is NOT secure).

Yes, I have the Promiscuous Mode check box checked in Ethereal.  I've tried SNORT and still nothing.

Can anyone help me out?  

Oh - one last thing - I CAN put my eth1 into "monitor" mode (as opposed to "managed") and I can see A TON of traffic - including some aim traffic from others around me.  My problem is, "monitor" mode gives you WAY TOO MUCH junk/white noise - with all the AP essid packet info - It's seems to be giving me stuff on the lower level of the OSI model.

---

### Post by v4q3r0 on 2006-03-02
By the way - I tried two different PCMCIA cards and the BOTH work.  They can sniff in promiscuous mode fine!  It's just this darn internal card.

So far no replies...I guess I'm screwed for now eh?

I may post in other linux forums - like gentoo or basic linux ones - so excuse the double posts.

Peace out,
~Vaquero~

---

### Post by mattiker on 2006-03-05
Hi,

I too am having this problem... would really like to know if there is a way to get the intel pro 2200bg to work in promiscuous mode.

Anyone?

---

### Post by escape on 2006-10-18
Me too. Can you at least explain Monitor mode? You could probably script something with grep in there to cut down on traffic.

---

### Post by tturrisi on 2006-10-19
Promiscious mode won't let you grab "all" the packets in the air, just lets you sniff packets on the lan.  What you want to use is Kismet:
[http://www.kismetwireless.net/](http://www.kismetwireless.net/)
Your cards may or may not work due to the driver being used.

RFMON: what is rfmon?  (monitor mode)
Short for Radio Frequency Monitoring, RFMON is a passive method of WLAN discovery. It is a sniffing mode which allows the card to report drivers from the 802.11 layer. A client with a wireless card that is configured in RFMON mode will be able to capture all RF signals on the channels to which it is configured to listen. RFMON is a receive-only mode. While in RFMON mode, wireless clients are unable to transmit any frames; their cards are only able to receive, and therefore capture traffic.

...and you will NEVER know you are being monitored!!!  Devices even exist to grab other wifi signals & data packets, e.g. cell phones, baby monitors, cordless phones, wireless video, garage door openers too!  Big brother is watching & listening...

---

### Post by mahy on 2006-10-22
I can't see anything even in monitor mode, only my own traffic and broadcasts. The thing i want is just to sniff the local WLAN, nothing else. I tried kismet, but it doesn't appear to be working properly either. And there's so little info about ipw2200 in promiscuous mode around the web. I think i'll buy an external card..

---

### Post by MKR. on 2006-10-22
It has been a while since my networking fundamentals class, but I'm fairly sure promiscuous mode only works with dumb nodes like switches and hubs that send the data to all connected nodes rather than just directing it only to the node that it was sent to.

I know with my closet switch I can sniff packets from one computer that are being sent to and from another, but I can't do the same with two nodes on a router.

---

### Post by tturrisi on 2006-10-22
> **MKR. said:**
> It has been a while since my networking fundamentals class, but I'm fairly sure promiscuous mode only works with dumb nodes like switches and hubs that send the data to all connected nodes rather than just directing it only to the node that it was sent to.

I know with my closet switch I can sniff packets from one computer that are being sent to and from another, but I can't do the same with two nodes on a router.
correct.
But not switches, just hubs.  A switch sends packets to only the target comp while a hub sends to all comps connected to it.  Thus promiscious mode won't work w/ a switch.

If the AP (or client) is plugged into a router, a switch or a router w/ built in switch then promiscious mode won't work.

Like I said, you need to use kismet to grab the traffic.  If kismet won't work, and kismetwireless.com says your card is supported, then you either have the wrong drivers, misconfig'd /etc/kismet/kismet.conf or both.

---

