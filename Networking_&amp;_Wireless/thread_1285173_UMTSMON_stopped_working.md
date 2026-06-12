---
title: "UMTSMON stopped working"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by paul2009 on 2009-10-07
I'm not sure where to go with this request, or even if I can correctly identify the problem. I've been using a USB modem to connect to the web (Alcatel x020, i think), and I'd set up usb_modeswitch and umtsmon - and everything had been working fine for about a year.

Two weeks ago, suddenly things weren't fine. I didn't update any of the software: the modem is still recognised, usb_modeswitch is still doing its job and I can still pick up the network signal. When I go to connect with umtsmon, however, the following happens:

1. As soon as I employ any function in umtsmon - whether it's trying to connect, or checking profiles, etc - the network signal just disappears. As soon as the function is complete or cancelled, the network signal reappears.

2. As a result, I always get the following error message:

Connection failed
Unfortunately PPP could not make a connection

And under the PPP stdout tab of umtsmon, I get:

Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB2
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup

3. After updating utmsmon, now if I try and connect again, I get this error message:

Failed to start PPP.
Please re-run UMTSmon from the commandline with -v5 and check the output

>>>>>

I have run through every possibility that I can think of to fix this - trying to connect through Gnome-PPP doesn't work either (more error messages and hanging) - and I've messed around with the wvdial configurations with no luck. I'm going to keep trying, but if anybody else has any ideas, they'd be really, really welcome right now. I have no idea why this would suddenly stop working when nothing else had changed....

---

