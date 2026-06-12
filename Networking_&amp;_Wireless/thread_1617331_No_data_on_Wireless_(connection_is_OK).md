---
title: "No data on Wireless (connection is OK)"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by pschalkx on 2010-11-09
Hi all,

I have a desktop currently on wired networking which I want to move to my home wireless network.

The desktop is an HP7620 and comes with a wireless interface with an external antenna. So, I deactivated the wired connection, and added a new wireless connection (secured with WEP).

The card connects to the network, I get the icon on the status bar telling me I got signal. I can ping my ADSL router (although responde is slow), but I can't get any data traffic through the connection.
I rebooted the machine (windows style) to no avail.

So my browser displays "connecting to whateever" stays there for a while end then times out reporting an error.

Any ideas what could be wrong?

Thanks in advance,

Philip

---

### Post by pschalkx on 2010-11-10
I also tried booting Windows (the machine is dual boot), and the wireless connection works fine. My aptop with Ubuntu 10.04 works fine via wireless.

So I would say that hardware is working OK and that my ADSL modem is not doing anything funny.

In Linux my browser still gets data veeeeeeryyyyyy slooooowlyyyyy, e-mail just times out.

Is there some setting I'm not aware of? Where else can I look for a cause?

Rgds,

Philip

---

### Post by uncaspi on 2010-11-10
can you ping google.com

---

### Post by pschalkx on 2010-11-10
Hi Uncaspi,

Thanks for helping.

In the first minutes after establishing the wireless communication, I can ping Google.com. The browser will also load 1 or 2 pages quite fast.

Then it starts quickly getting slower and slower. It reports response times of around 30ms. Then the ICMP numbers begin jumping the sequence like 27, 35, 56...

When I compare with my laptop (also Ubuntu on the same wifi network) it also reports 20+ ms to respond, but ICMP numbers are in sequence: 1, 2, 3...

So apparently some data packets are being lost on the desktop under Ubuntu.

I checked with Windows and the wifi controller is listed as a USB wireless b/g controller, and it says that software is made by Gemtek.

Any ideas?

Rgds,

Philip

---

