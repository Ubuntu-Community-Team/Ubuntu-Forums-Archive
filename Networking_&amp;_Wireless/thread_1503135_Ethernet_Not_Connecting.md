---
title: "Ethernet Not Connecting"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by brwarner on 2010-06-06
Hi, I just installed the newest version of Ubuntu Desktop (10.04) and this is my first time really trying to use Linux but unfortunately things are not going well...

I have connected an ethernet cable to my router but Ubuntu refuses to connect to it. Here is the information I have on my ethernet card (built into motherboard)
"Sundance Technology Inc / IC Plus Corp IC Plus IP100A Integrated 10/100 Ethernet MAX + PHY (rev 31)"
The motherboard is an ABIT make.

My router is wireless/wired. Model: D-LINK DIR-625

EDIT: A lot of people seem to have trouble networking with 10.04, so I am in the process of downloading 9.10 until this is figured out.
EDIT2: (9.10 doesn't seem to be working well either :( )

---

### Post by Iowan on 2010-06-06
[Here]("http://ubuntuforums.org/showthread.php?t=1484913") is a link I just "re-discovered" in my subscriptions.

---

### Post by brwarner on 2010-06-06
That seems to be about computers going into hiberate and somehow damaging their network settings. This is a fresh install. I am now running Ubuntu 9.10 Server edition but still no luck. :(

---

### Post by Iowan on 2010-06-06
Sorry that one didn't help.  What are results of **sudo lshw -C network**? Does machine get IP address by DHCP - or is it static?

---

