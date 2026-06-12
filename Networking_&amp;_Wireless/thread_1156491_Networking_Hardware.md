---
title: "Networking Hardware"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by Stan% on 2009-05-11
I have one system running XP with a wired only NIC connected to a router and in turn to a broadband modem.

A second system running Ibex with a wireless only NIC. 

Computers are in different rooms. 

To network these two computers do I need to install a second wireless NIC in/on the XP system?

---

### Post by Iowan on 2009-05-11
Does the router also provide Wireless access? I suspect you would want the router to be the common point - even if you needed to add an access point connected to router.

---

### Post by Stan% on 2009-05-11
> **Iowan said:**
> Does the router also provide Wireless access? I suspect you would want the router to be the common point - even if you needed to add an access point connected to router.

Yes, router is both wired and wireless.

Access point goes between router and XP computer?

---

### Post by abn91c on 2009-05-11
thats how my network is, wired XP, wireless desktop and laptop(kubuntu on both) I use a linksys wrtg54g router and linksys modem, all you need to do is run the web wizard to make your connections. for the linksys is [http://192.168.1.1](http://192.168.1.1)
the laptop uses a broadcom card, the desktop a belkin usb adapter.

---

### Post by Iowan on 2009-05-11
If the router has wireless access, then the access point is unnecessary - otherwise, I'd put it on another router port. Maybe just my interpretation, but that makes the router the "common point" for access to the modem. Modems sometimes like to "lock onto" a single MAC address. In your case, that would be the router's - which seems optimal.

---

### Post by Stan% on 2009-05-13
Well, the Windows part of the network is working okay.

On the ubuntu system.....

Places> Network> Windows Network> WORKGROUP.........only shows the Ubuntu computer and then the Ubuntu shares.

The XP computer doesn't show at all.

I've searched the Internet till I'm so confused I don't know my own name.

Can someone help?

---

### Post by Iowan on 2009-05-13
Can you **ping** from one box to the other? If so, it may be a workgroup name problem.
... Or, it may be that you need to install Winbind and edit your /etc/nsswitch.conf to include "wins" (without quotes) before "dns" on the "hosts:" line.

---

### Post by Stan% on 2009-05-13
> **Iowan said:**
> Can you **ping** from one box to the other? If so, it may be a workgroup name problem.
... Or, it may be that you need to install Winbind and edit your /etc/nsswitch.conf to include "wins" (without quotes) before "dns" on the "hosts:" line.

I can ping in both directions. Workgroup names are the same.

In synaptic winbind is not installed. (nor winbind4)

---

### Post by lisati on 2009-05-13
> **Stan% said:**
> Well, the Windows part of the network is working okay.

On the ubuntu system.....

Places> Network> Windows Network> WORKGROUP.........only shows the Ubuntu computer and then the Ubuntu shares.

The XP computer doesn't show at all.

I've searched the Internet till I'm so confused I don't know my own name.

Can someone help?

It might be necessary to run the Windows "network setup wizard" and to enable file sharing (if that's what you want to do). The exact place to find it will vary according to which version of Windows you're using, but it's usually found somewhere on the Control Panel in the "networking" category.

---

### Post by Stan% on 2009-05-13
> **lisati said:**
> It might be necessary to run the Windows "network setup wizard" and to enable file sharing (if that's what you want to do). The exact place to find it will vary according to which version of Windows you're using, but it's usually found somewhere on the Control Panel in the "networking" category.

File sharing on XP system is enabled.

---

### Post by Stan% on 2009-05-13
Both computers are on but just as a basic question; do both computers need to be on in order to share files?

---

### Post by Iowan on 2009-05-14
I'm not sure how to retrieve files from a powered-down computer, so I suspect both machines would need to be on.

---

### Post by Stan% on 2009-05-14
> **Iowan said:**
> I'm not sure how to retrieve files from a powered-down computer, so I suspect both machines would need to be on.

I can answer my own question now. Both computers need to be on and Samba Daemons must be started.

Everything reguarding networking is working now. It seems I only needed to do a few things. 

On the XP system I had forgotten that years ago I had turned off some of the services including server services; had to turn that on and configure ZoneAlarm to allow the IP addresses.

On Ubuntu system I just need to start the Samba daemons and make sure FireStarter is disabled.

And it seems I must give the two computers some time (5 mins. or so) to get themselves organized.

Thanks for your help.

---

### Post by Stan% on 2009-05-15
Maybe I still don't have all the bugs worked out.

Before I set this network up the computers connected, how should I say it, directly through the router.

Now they seem to be connecting, still through the router ofcourse, but via the LAN. It seems this is why I have to give it 5 or 10 mins. "to get organized". If I try to get to any web site in those first few mins. it is incredably slow and I may not get to the site at all. I'll need to do some more exparamenting but it seems that both computers must be on in order to make any connection to the internet at all.

In Control Panel> Network Connections reads......

Broadband Connection
Disconnected
WAN Miniport (PPPOE)

LAN or Highspeed Internet
Roadrunner Internet
Connected
{*name of my NIC*}


When a home network is set up MUST the computers connect via the LAN?

---

