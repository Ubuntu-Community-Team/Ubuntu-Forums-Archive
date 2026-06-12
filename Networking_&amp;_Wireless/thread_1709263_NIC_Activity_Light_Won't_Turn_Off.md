---
title: "NIC Activity Light Won't Turn Off"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by caffeinated blood on 2011-03-18
I've recently noticed that both indicator lights on my integrated NIC are on even when the network connection is disabled.The green light is steady and the yellow activity light is always flashing.I disable my network connection(just my PC to a router/internet)by selecting both 'Disconnect' the ethernet connection on the Wired Network and unchecking 'Enable Networking' in Network Manager.The System Monitor then shows absolutely no network activity when I do so.Is this just a hardware driver issue with Ubuntu?More importantly, is activity actually taking place?I have a recent MSI board with Realtek LAN.Sorry to use Windows as an example(dual-boot PC), but for comparison, the NIC indicator lights both go out when I disable my network connection on that OS.

---

### Post by BkkBonanza on 2011-03-18
One way to see what connections are open is with **netstat -ntp**. It doesn't show actual current traffic though. **iptraf** should give some idea of traffic and you can see what is going on.

Even just using **ifconfig** and watching the packet counts gives an indication of activity.

watch -n 1 ifconfig

---

### Post by caffeinated blood on 2011-03-18
I've run both netstat -ntp and iptraf and both show no traffic when the connection is disabled.But I also ran ifconfig and that shows that there are 533 RX/TX packets when disabled?The activity light still flashes - guess there is no activity?

---

### Post by BkkBonanza on 2011-03-18
Seems odd. You may want to test a different cable. Sometimes cabling can affect the connection and perhaps that is causing the flashing.

---

### Post by caffeinated blood on 2011-03-18
I gave another ethernet cable a try and it made no difference.Thanks for the suggestion though.I didn't think it would - as I mention previously, Windows will shut it off so one OS does:one OS doesn't.

---

### Post by geezerone on 2011-04-03
I too find that sometimes booting into Ubuntu the link LED flashes very fast but no internet/router connectivity. If I removed and re-insert eth cable in router the flashing stops. Booting into Windows is fine also or if I boot into Windows first and then Ubuntu it's fine.

Using Gigabyte 870 UD3 mobo for into.

---

### Post by caffeinated blood on 2012-03-28
The solution for this issue was to install ethtool and then disable WOL on the NIC.

---

