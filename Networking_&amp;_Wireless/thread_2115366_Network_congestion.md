---
title: "Network congestion"
date: 2013-02-12
forum: Networking &amp; Wireless
---

### Post by Fake51 on 2013-02-12
Hi, wondering if someone might have some clues on how to troubleshoot a network congestion problem.

I'm on a Lenovo netbook with ubuntu 12.04 installed. I've got wireless running fine, out of the box. The problem I'm seeing is that this laptop is creating slowdowns for other devices on the same router. We've got one wireless router/modem that two phones, a tablet and two laptops (one windows 7, one ubuntu) connect to. When the ubuntu is not online, everything is dandy, no slowdowns or problems with requests grinding to a halt. When the ubuntu machine is running, the other devices have network slowdowns, sometimes lost connectivity.

My main concern is that it might be malware related: something participating in a ddos or something like that, creating lots of traffic on the network, hence slowing the other devices down. I don't particularly think this is likely but I'm not quite sure how to test the theory. I've installed and run clamav, and have set up sysrescuecd on a usb stick, booted from that and tested the disk with rkhunter and chkrootkit, all negative.

So, what could be possible reasons for what I'm seeing and how can I go about checking the scenarios?

Tia
Fake

---

### Post by tgalati4 on 2013-02-12
I like etherape.  It gives you a visual feel for traffic on your network.

In a terminal:

```
sudo apt-get install etherape
etherape
```

---

### Post by Fake51 on 2013-02-13
Thanks, tried that, looks pretty good.

I don't seem to have a lot of stuff going on (judging by etherape). I do see requests to 224.0.0.251 and 255.255.255.255 very often though, which surprises me a bit. Judging by google, the likely culprit is avahi-daemon, for the first IP. No idea if I actually need that to run.

However, a few more symptoms: leaving the computer on with no browser or anything else actively generating traffic means the network is doing fine. Installing etherape using apt-get meant an instant degrading of the wifi for the other devices online. No browser open or anything else, just apt-get from the command line.

Another thing is that if the other laptop runs wired, it's fine - no noticeable degradation of service, when the ubuntu is on the wifi. I'm not entirely sure what this seems to suggest nor how to confirm any suspicions. Ideas?

---

