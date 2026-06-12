---
title: "primary wifi router connectivity troubleshoot"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2012-08-06
There are 2 available wireless connections for the 'puter. The host wifi router and the 2ndary wifi router. I can only connect to either of them via wireless, as the devices are in the next door neighbors apartment.

About 2 weeks ago, I started seeing my 'puter connected to the 2ndary wifi. I have tried, over several days to re-establish a connection to the primary wifi as the signal strength is about 20 to 25 % stronger. At first, this was possible. On cold boot, the OS would pull the 2ary and I could disconnect from it and select and connect to the primary. As of today, I cannot do that.

Both wifi's were set up at about the same time (a year or so ago). Both use the exact same settings, (example: iv4P, etc.) except for the WEP key.

While I had been using a Linksys wifi router to play with DD-WRT a few weeks ago: 

1. that was via a wired connection to this 'puter's ethernet port (RJ45)
2. the IP addresses of the Primary & 2ary devices were/are unchanged, along with all the other default settings in both of them. Only the Linksys had it's internals changed.

This morning, Ubuntu Update Manager said I would receive an nvidia-security update of about 33 meg. The download stalled. I cancelled it after 10 minutes and tried again. It stalled again, with this message:

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-current_295.40-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-current_295.40-0ubuntu1.1_i386.deb) Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)


I rebooted, opened Update Manager and got to about 34% finished, when I received this error message:

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-current_295.40-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-current_295.40-0ubuntu1.1_i386.deb) Could not connect to security.ubuntu.com:80 (91.189.92.184). - connect (113: No route to host) [IP: 91.189.92.184 80]

I tried to load Chrome and even though I'm getting 50% signal strength (so says panel icon) through the 2ary router, Chrome cannot get back online. I next tried Firefox and it can't get through to the 'net, either.

The panel wifi icon (sig strenght bars) says: "requesting net' address" but seems to never receive one.

help me, now, as I'm using (blacch!) Win7 (this is the joke part of this post, it is blacch!, but not I'm joking about 'now'.)

---

### Post by Mark_in_Hollywood on 2012-08-07
The foregoing is/was a temporary state. I'm marking this thread as "solved" as I believe the problem to be an anomaly.

---

