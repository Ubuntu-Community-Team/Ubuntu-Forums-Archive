---
title: "Very slow DNS lookups with Natty 11.04 and new Netgear WNR2000 router"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by SteveTheRed on 2011-07-15
I did some serious Googling about this, but I haven't found a solution that works. I work in IT, but networking is my weakest
area.

I'm getting very slow DNS lookups (60+ seconds with lots of page timeouts)in Firefox and Chromium on my Kubuntu laptop. Windows
clients (xp and 7) work fine.

I just replaced a Vonage D-Link wireless phone modem combo that died with a Netgear N300 (WNR2000, more specifically WNR2000v3)
and a Vonage wired phone modem.

The Netgear arrived before the Vonage box, so I immediately hooked it up. The Vonage box has since arrived and is now connected between the cable modem (Comcast) and the wireless router. This did nothing to change the problem.

The Netgear automatically checks for firmware updates, so no love there. I changed it from the default settings to enable N mode with WPA2 (AES), made all of the IP addresses for the clients static, changed the DNS servers to OpenDNS (I also tried Google and Comcast DNSes) and changed the admin password ;) 

Restoring to factory settings didn't fix the problem, nor did switching to G-only mode.

I'm using Kubuntu Natty 11.04 AMD64, fully updated. My laptop is an Acer Aspire 5741G-6883 with a Broadcom wireless N adapter:

```
steve@bender3:~$ lspci -nn | grep "802.11"
03:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
```

On my machine, I disabled specifying my preferred DNS servers, since I can now specify them at the router. Changing that back didn't help.

I disabled IPv6 on my machine and in the two browsers. Nothing.

I tried disabling the Broadcom STA driver in favor of the one in the kernel. I also tried using two of the open-source Broadcom drivers (my memory gets fuzzy here, I can't remember the names) with no success.

I got a good deal at Newegg on the router, but I'm about ready to send it back. Before I go even more days without wireless (shudder), does anyone have any ideas about how to fix this? I'd really appreciate it. Thanks.

[COLOR="Red"]To future visitors looking for a solution:

I booted my machine with an older kernel and the problem went away. When I rebooted with the now-current kernel, the problem was still gone, even after several more reboots. I have no idea why this worked or if it will work for you.[/COLOR]

---

### Post by ratcheer on 2011-07-15
Maybe you are double-NAT'ing. Is your cable modem also a router? If the cable modem is doing NAT, then your Netgear router is also doing NAT, that could very well be causing the problems you describe.

Tim

---

### Post by SteveTheRed on 2011-07-15
Thanks for answering.

My cable modem doesn't do NAT but the Vonage and Netgear routers do. I have the same behavior with or without the Vonage router.

Wouldn't double-NATing cause problems with the Windows clients as well? They are all working well with this new configuration.

---

### Post by SteveTheRed on 2011-07-15
One thing I forgot to mention in the OP:

I have the same slow DNS lookups with the Netgear router when I disconnect from wireless and connect via and Ethernet cable. Sorry I forgot to mention that.

---

### Post by ratcheer on 2011-07-15
It was just a guess...

Tim

---

### Post by SteveTheRed on 2011-07-15
Sorry, I didn't mean to sound unappreciative.

The plot thickens:

Since posting this thread two hours ago, I've had three kernel panics. I've been using Linux for ten years and I've never had a kernel panic in all of that time.

I booted using an older kernel (2.6.38-8-generic) instead of the current one (2.6.38-10-generic) and the problem has completely disappeared! My DNS lookups are as fast as they ever were!

I'm not marking this as solved yet, since I can't stay on 2.6.38-8 forever.

Any ideas would be appreciated before I file a bug. Thanks!

---

### Post by AllanM on 2011-07-16
Hi. Have you tried using another DNS provider. I'm on 11.04 (Linux HP-ProBook-4515s 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 athlon i386 GNU/Linux) with an N300 WNR2000v2 router using opendns (208.67.222.222/208.67.220.220) and dns is fast. I have other problems withthsi router in that my wireless card (broadcom 4322) won't connect to it either n or g. Seems to be the broadcom drivers as a galaxy tab and sony vaio connect fine. Good luck. Allan.

---

### Post by SteveTheRed on 2011-07-16
Thanks to everyone who responded.

I've rebooted several times in the current kernel (2.6.38-10-generic) and my DNS problem *and* kernel panics have gone away.

I'm baffled, but at least it works now. I'm marking this as solved and placed a brief synopsis of the mysterious "fix" in the first comment. I'm not happy about marking it solved, but I don't want anyone to waste their time trying to fix a problem that doesn't exist anymore.

If anyone has any ideas why this worked, I'd love to hear them. Thank you.

---

