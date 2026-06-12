---
title: "Wifi router hang"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by jryals on 2011-10-15
After upgrading on my laptop from 11.04 to 11.10, the wireless (wlan0) would connect to my router like normal but after a minute or two the router will completely hang. I have to reboot the router and turn off the wireless adapter on the laptop and then use eth0 in order to get the laptop online.  I have repeated this wireless hang condition multiple times. I have an IBM thinkpad w510 and a buffalo WZR-HP-G300NH router running DD-WRT firmware. The wireless adapter is the Centrino Ultimate-N 6300 adapter from Intel. A google search found someone else that had the same issue but with a different laptop and a cisco router.

---

### Post by Maduri on 2011-10-15
I am in the same boat. I am running Lenovo ideaPad Y530 with fresh install of Ubuntu 11.1. Once the wireless adapter is turned on, I connect to my router for about a minute or so. Then once I open Chrome and type something in the Google search bar the router kicks me out. The router goes nuts and all my other machines in the household lose connection. I am using a standard issued Verizon ActionTec FIOS router and it was working flawlessly with 11.04.
My machine is working OK if it is linked to the router with a cable, but the wireless issue is causing a lot of troubles. Please advise.
PS I Forgot to mention that i have to reset the router after every failed attempt to connect

---

### Post by dbiddy on 2011-10-17
same problem here.  same buffalo router, WZR-HP-G300NH, with the latest buffalo-branded dd-wrt, with my system76 pangolin performance.  worked fine with natty.  i've tried disabling ipv6, as well as manually setting my dns servers to the google ones, as i read these were both potential issues, but neither of these seemed to do the trick

---

### Post by Maduri on 2011-10-22
Guys after some digging I found this webpage:
[http://thelinuxexperiment.com/guinea-pigs/tyler-b/ubuntu-11-10s-wifi-crashes-my-router/](http://thelinuxexperiment.com/guinea-pigs/tyler-b/ubuntu-11-10s-wifi-crashes-my-router/)
It did the trick for me. I hope this helps.

---

### Post by klauskiwi on 2011-11-12
I had the exact same problem with a Lenovo T-410 and DD-WRT. Upgrading to Kernel 3.1.1 from kernel-ppa solved the issue.

But the funny thing is that this most probably exposed a DD-WRT bug also. I'm using build 16785 on an Atheros-based router (WRT-160nl).

---

