---
title: "Intermittent Extremely Slow Wired Ethernet"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by jkounis on 2012-05-09
I have a desktop computer with a Gigabyte GA-G41M-Combo motherboard. It has an Atheros AR8151 onboard LAN (10/100/1000 MBit), and I'm running Ubuntu 10.10.

I have an unusual problem that is perplexing me: Most of the time, the network bandwidth is just fine--measured at more than 900 Mbits using iperf, which is fine for a gigabit ethernet connection. However, about 20% of the time, the networking is _extremely_ slow when I boot the machine -- around 2-200 kilobits. 

If I restart networking with sudo /etc/init.d/networking restart, it has no effect; the network is still unbearably slow. The only thing that solves the problem is a reboot, after which the computer usually resumes with gigabit speeds and works just fine. 

The problem only occurs during reboot. Once the machine boots correctly, it will run for weeks or months without a network slowdown. Conversely, if the machine boots with a slow network, nothing seems to speed it up, except for a reboot.

I have searched the forums and online, and I have found many slowdown issues for wireless connection, but no issues for a wired connection like I have.

Any ideas?

---

### Post by drtheradio on 2012-05-09
Have you tryed cleaning the borad really good. Static build up on dust / dirt. Could be building up and causing
Capacitance and will cause hardware to malfunction . And rebooting will fix till the Charge builds agian.
  

Also could be a Defect in the hardware its self.   Mabe try upgrading....


Just some ideas.

---

### Post by jkounis on 2012-05-09
Thank you for the suggestions.

The problem appeared since the board was new. It has only been running a few months now, so the board is still pretty clean.

If it were a hardware problem, wouldn't the problem manifest itself when the machine is running normally?

The problem has never appeared after a successful reboot--even weeks later. It either boots successfully or it doesn't. The Ethernet speed in the first 30 seconds of uptime define what it will be for the rest of the time it's running.

---

