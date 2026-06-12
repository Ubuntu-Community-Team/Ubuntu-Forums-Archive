---
title: "Internet question"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by hammondb3 on 2009-02-01
Yes does anyone know what ISC is I heard it stand for 
internet system consortium, but I noticed it cause it
was in my system log, something about DHCP
IS it normal to have that in logfile?

---

### Post by Iowan on 2009-02-01
I found [this]("https://www.isc.org/software/dhcp") page on ISC DHCP. and from Synaptic's package descriptions:> This is the server from version 3 of the Internet Software
Consortium's implementation of DHCP. For more information, visit
[http://www.isc.org](http://www.isc.org)

---

### Post by albinootje on 2009-02-01
> **hammondb3 said:**
> I noticed it cause it was in my system log, something about DHCP
IS it normal to have that in logfile?

Yes, it is.

---

### Post by hammondb3 on 2009-02-01
So that log is normal?

---

### Post by albinootje on 2009-02-01
> **hammondb3 said:**
> So that log is normal?

I just checked on my Ubuntu desktop, and on some remote Debian machines, and I can't find a separate instance of the word "ISC" in the logfiles.
Can you post an example output of what you have ?

---

### Post by hammondb3 on 2009-02-01
All I have is sys log file is 
Jan 31 23:23:07 -desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1

Jan 31 23:23:07 -desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.

Jan 31 23:23:07 -desktop dhclient: All rights reserved.

Jan 31 23:23:07 -desktop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

What does this mean, I dont get, is this an error

---

### Post by MarblePanther on 2009-02-01
No it is not an error, you are fine.  

ISC just governs the way DHCP is used, they create the standards.  Seriously nothing to worry about.

> About ISC


Internet Systems Consortium, Inc. (ISC) is a nonprofit 501(c)(3) public benefit corporation dedicated to supporting the infrastructure of the universal connected self-organizing Internet&#8212;and the autonomy of its participants&#8212;by developing and maintaining core production quality software, protocols, and operations. 

It is supposed to be in your logfile.  Don't worry about it.

---

### Post by hammondb3 on 2009-02-01
Does anyone know why ubuntu 8.10 freezes after screen saver?
Didnt happen til i upgraded

---

### Post by albinootje on 2009-02-01
> **hammondb3 said:**
> All I have is sys log file is 
Jan 31 23:23:07 -desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
-- cut --
What does this mean, I dont get, is this an error

Okay, so you meant "Internet Systems Consortium" instead of ISC in your OP. Next time please try to be more accurate in your postings, that can save you and us time :)
And as others already said, this is not an error, it's just information from the DHCP client in the logfile.

---

### Post by albinootje on 2009-02-01
> **hammondb3 said:**
> Does anyone know why ubuntu 8.10 freezes after screen saver?
Didnt happen til i upgraded

In the past I've seen people having trouble with certain screensaver choices, are you running a specific screensaver or are you using random screensavers ?

Check here to see whether this bug is already reported :
[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=screensaver&search=Search+Bug+Reports&field.scope=all&field.scope.target=xscreensaver](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=screensaver&search=Search+Bug+Reports&field.scope=all&field.scope.target=xscreensaver)

---

### Post by hammondb3 on 2009-02-02
Seems to have gone away I chose a different screen saver
Another thing is Firestarter really needed for a firewall
on Ubuntu?

---

### Post by albinootje on 2009-02-02
> **hammondb3 said:**
> Seems to have gone away I chose a different screen saver

Good.
> 
Another thing is Firestarter really needed for a firewall
on Ubuntu?

You can also use gufw, I like that better for a desktop machine.
[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html) (Is in the Intrepid repositories).

But is your question about whether firewall management software is really needed for a Linux desktop ?
If you're behind a router/modem with a properly configured firewall, and no untrusted users on your LAN, then it's not needed.

---

### Post by hammondb3 on 2009-02-02
Properly configured meaning what the 
router?

---

### Post by albinootje on 2009-02-02
> **hammondb3 said:**
> Properly configured meaning what the 
router?

Yes. Some DSL-routers and cable-modem come pre-configured with the firewall off, or badly configured.

---

### Post by MarblePanther on 2009-02-02
I recommend you just use gufw.  Install it through synaptic and open it up in system, administration, firewall configuration.  All you have to do is check the boxes Deny Incoming Traffic and Firewall Enabled and youre done.

---

