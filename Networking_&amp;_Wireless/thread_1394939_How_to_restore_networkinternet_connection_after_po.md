---
title: "How to restore network/internet connection after power outage?"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by itsols on 2010-01-31
Hi everyone, Please let me know if this is normal?

Sometimes either due to a power outage or due to lightning I turn off my Wimax modem and continue to use my laptop on the battery.

Then when I turn the modem back on, there is no internet connection.

Here's what I've tried:

1. turn off and on the network connections - right-clicking on the icon on the bar on top of my screen.

2. turn off and on the dsl-provider connection - no effect.

3. When I tried to re-do pppoeconf, it says that there's no response from the concentrator...

This has happened a few times in the past and the only thing I can do to go online again is restart the computer. And it works.

Now on Windows, the double-computer icon showing a network indicates connectivity AND data movement. Unfortunately we don't have this on Ubuntu.

I'm just after a restart and I'm online now. But I'd like to know if there's a way around this without having to restart.

Many thanks in advance.

---

### Post by tantonyan on 2010-03-01
Hi,

I am having the very same problem with a few machines on the same network - in a lab.
Once in a while I would find all machines offline in the morning, I assume that there was a network outage sometime during the night each time. Although the network has been up and running by the time I got here (as other machines: Mac and even Ubuntu-Server are online) all of the Ubuntu desktops need to be restarted before they are online.

I was thinking that there will be a way of renewing the configuration, and that perhaps I can set it up as a crontab to run and renew the connection in case it happens while there is no one in the lab and if we need to access any of the machines remotely, but so far I did not find anything on this issue.

Your help is greatly appreciated !

Thank you!
Tigran

---

### Post by tantonyan on 2010-03-01
I seem to have found the solution to this problem:
```
sudo ifconfig eth0 down; sudo ifconfig eth0 up; sudo dhclient
```

I am going to set up a crontab for root to see if this will help prevent future outages.

Hope that it works and that others too find it helpful !

Tigran

---

### Post by itsols on 2010-03-01
Thank you Tigran for sharing your thoughts on this... Excuse my ignorance on Ubuntu/Linux, but I'm a little unsure if running dhclient will resolve this because I'm using static IPs for the computers and dynamic ones only for the Internet connections.

Also pls let us know if this worked on your system. Here's a test:

log on to the network... Go online... after a little while, turn off the only the Internet router/modem and bring it on back after about one minute. Then try your ifconfig lines and see if it all gets back.

Thank you once again for your tip.

---

