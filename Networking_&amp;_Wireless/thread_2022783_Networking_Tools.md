---
title: "Networking Tools"
date: 2012-07-11
forum: Networking &amp; Wireless
---

### Post by Kevzz on 2012-07-11
Hi, I was wondering if there is any networking software / tools available for Ubuntu (12.04). I'm looking to monitor my home network traffic, something like Endian Firewall, any suggestions?

Thanks

---

### Post by Kirk Schnable on 2012-07-11
Your question is so vague I don't know where to begin!

Here are a few applications worth looking into:
TCPDump - Packet inspection
Kismet - WiFi scanner
Wireshark - Packet inspection

vnstat - Bandwidth logging
iftop - Realtime traffic monitoring
ifstat - Realtime bandwidth logging


And some graphing software you might like for bandwidth graphs:
MRTG
Munin


And of course there's Nagios for a birdseye view of your network.

As far as firewalls, Ubuntu comes with iptables which is very robust.  ufw is a simple front-end to iptables.

Any of this what you're looking for?

Kirk

---

### Post by poolet on 2012-07-11
> **Kevzz said:**
> Hi, I was wondering if there is any networking software / tools available for Ubuntu (12.04). I'm looking to monitor my home network traffic, something like Endian Firewall, any suggestions?

Thanks

[LEFT]try to used fail2ban and iptables you will be fine, if your want father monitoring by saving dumps files try wireshark but keep in mind that wireshark is not a good idea if you want something for a log time.. If your running server a good idea is iptables with fail2ban, or Nagios as [Kirk Schnable]("http://ubuntuforums.org/member.php?u=1699279")  mentioned...

good luck!! 


[/LEFT]

---

### Post by Cheesehead on 2012-07-11
There are lots of monotoring tools. I use EtherApe and a couple custom scripts.

What is it you really want to know? Bandwidth consumption? Websites visited? Current machines on the network? Packet traffic?

---

