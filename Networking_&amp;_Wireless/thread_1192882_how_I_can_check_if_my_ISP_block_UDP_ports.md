---
title: "how I can check if my ISP block UDP ports"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by angryalf on 2009-06-20
Hi everyone!

So, here is problem: i try use VOIP (Twinkle) but can't call... my VOIP provider say me - i have blovked UDP ports.... how I can check this?

PS: Twinkle do registration (registration succeeded (expires = 3600 seconds)) , but when I try call any have next:
Line 1: call failed.
500 Server internal failure

---

### Post by angryalf on 2009-06-21
so, nobody don't know?

---

### Post by Brandon Williams on 2009-06-21
You could try using traceroute. If you have access to a machine somewhere outside of your local network, use traceroute to trace the path from the external machine to your home machine. Make sure you specify the correct port number with the -p flag.

Before trying to figure that out, though ... Do you have an internet gateway so that multiple machines can share your broadband connection? And if so, does the VOIP device also go through the internet gateway? And finally, if the device goes through the internet gateway, did you configure the necessary port-forwarding rules in the gateway? I had one VOIP provider for which reconfiguration of my internet gateway was required, but that is not true of my current provider.

---

### Post by angryalf on 2009-06-21
Hi!

 can ping this PC, and VOIP software connect & do authorization... but this is all.. I can't cal.... my VOIP check system logs and say - maybe i have block UDP on this ports.... i need check this.. and don't know how... any ideas?

---

### Post by cariboo on 2009-06-21
If you know what port voip is using, you try [canyouseeme]("http:///www.canyouseeme.org/") to see if the port is blocked.

---

### Post by jhannah on 2009-06-24
Provided you have access to another machine on the Internet, netcat would be a simple test.

First install it on both machines:
```
sudo aptitude install netcat
```

On your home machine, turn off the VOIP software and run (replace 1234 with the port you wish to test):
```
nc -lup **1234**
```

On the other machine, run the following (replace 1.2.3.4 with your IP and 1234 with the port you wish to test):
```
nc -u **1.2.3.4 1234**
```

At this point, you should be able to type something in either running netcat window and see it on the other. If you don't, that port is being filtered.

---

