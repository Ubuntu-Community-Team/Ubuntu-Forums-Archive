---
title: "pppoeconf &quot;Access Concentrator... did not respond&quot;"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by arohanui on 2008-12-29
I'm trying to configure my internet connection.

Running pppoeconf fails with an "Access Concentrator of your provider did not respond" message.

I'm running Gutsy since I can't connect to update, with a Motorola Sufboard SB5101 ethernet cable modem, and New Zealand TelstraClear is my cable provider.  I have a flawless connection to Windoze.

sudo tail -f /var/log/messages:

Dec 30 16:53:34 Athena kernel: [   59.371786] Bluetooth: L2CAP ver 2.8
Dec 30 16:53:34 Athena kernel: [   59.371791] Bluetooth: L2CAP socket layer initialized
Dec 30 16:53:34 Athena kernel: [   59.433415] Bluetooth: RFCOMM socket layer initialized
Dec 30 16:53:34 Athena kernel: [   59.433430] Bluetooth: RFCOMM TTY layer initialized
Dec 30 16:53:34 Athena kernel: [   59.433432] Bluetooth: RFCOMM ver 1.8
Dec 30 16:56:23 Athena kernel: [  228.365916] PPP generic driver version 2.4.2
Dec 30 16:56:23 Athena kernel: [  228.378770] NET: Registered protocol family 24
Dec 30 16:56:42 Athena pppoe-discovery: Timeout waiting for PADO packets
Dec 30 16:56:57 Athena pppoe-discovery: Timeout waiting for PADO packets

I know next to nothing about networking.  Any ideas, or do I need to contact Telstra?

---

### Post by arohanui on 2008-12-30
Bump.

I really hope someone can help me out - Telstra sadly doesn't provide linux support.

---

### Post by carml on 2008-12-30
Are you sure that you choosed the correct device from the list? Haven't you got a ethernet also?

---

### Post by arohanui on 2008-12-30
Oh! I do have ethernet, that's my only device (eth0).  I see, pppoe is for ADSL and ethernet should work without configuration, I misread the documentation.  Told you I was a networking know-nothing.

It must be something else that is preventing my pings.  I'll look into it further.

Thanks for shedding some light.

---

