---
title: "Two wireless adaptors connected on one computer"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by Levy1234 on 2009-11-17
Hi folks.  I have 9.10 on my laptop.  The computer comes with a Broadband wireless adaptor.  To try to get better range, someone suggested that I use an external USB wireless adaptor with an antenna.  I chose an Alpha (Realtek).  When I plug the Alpha in and click on the network icon, it shows both the Broadcom and the Realtek as connected to my home network at the same time!  The connection works so there is no complaint there.  I can also click "disconnect" on either and get  left with just one connected and working.  Here is my question.   Are they both *really* connected?  And if so, does that have any practical significance?  If both are connected, do I get any kind of benefit?  Or are they likely to interfere with each other.  Thanks for any information you can provide.    Cheers.  Levy

---

### Post by SGAZ on 2009-11-17
To see if there is any benefit one way or the other you can try a speed test like the ones available at [http://www.dslreports.com/speedtest]("http://www.dslreports.com/speedtest").

---

### Post by spd106 on 2009-11-17
Yes they probably are both connected to your AP/router with separate IP addresses. This shouldn't cause too much on a problem as Network Manager will select one of as the default gateway (I believe it chooses the last one to connect) and uses that for all non-local traffic.

You can see this information if you open the System -> Administration -> Network Tools program and select the netstat tab.

Wireless is a shared medium, so will potentially be reducing the performance for all uses of the network, but only be a negligible amount. Sadly there's no speed bonus i.e. you don't get double the performance with two links, not without getting a more complicated set-up and probably some new hardware.

You might want to consider the extra power draw and CPU resources needed to maintain the redundant connection.

---

### Post by Levy1234 on 2009-11-17
Thanks, spd106 is quite right that it did not affect the speed of my connection (I tested it.)  And he is also right that netstat looks different.  When I connect with the internal broadcom adaptor, it specifies "interface" as "eth1" and when I connect with the USB adaptor, the interface is wlan0.  (Both connect to the same IP's.)  I would have thought they would both come up as wlan0 since both are for wireless, but what do I know?  I am sorta new to wireless.  The main good thing about the Alfa USB adaptor is it gives a significant increase in distance, though identical speed.  So I will probably only use it when I need that distance.  Thanks again for the info.  Levy

---

