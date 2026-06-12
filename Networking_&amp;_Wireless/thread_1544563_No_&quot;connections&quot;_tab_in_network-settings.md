---
title: "No &quot;connections&quot; tab in network-settings in UbuntuStudio 10.4"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by getack on 2010-08-02
Just installed UbuntuStudio 10.4 X64 next to my main Ubuntu 10.4 X86. For some reason the network-settings app is not working right.

I use a Netgear WG311v3 wifi card to connect to my home network and I'm a pro with using ndiswrapper to emulate the drivers for both 64 and 32 bit machines. Everything driver-wise works and iwconfig shows my card as installed and working.

When I want to connect to the network I go to System > Admin > Networking to set everything up. But the problem is, there is no "Connections" tab. Only "General", "DNS" and "Hosts". So I cannot select my wifi card to set up the ip's and everything. I haven't tried using a normal UTP cable, as it's quite a hassle to extend it to my room, but I'm sure I will get the same results.

How come everything works hunky-dory in Ubuntu, but not in Studio? It's exactly the same!

If I am being a total noob please help me. Should I reinstall the Network settings app or what?

Thanks!

---

### Post by P4man on 2010-08-02
Ive read this before.. Ive never seen system > admin > networking. Only network tools and they have nothing to do with setting up the networking. Is this some third party app?

Anyway, the "normal" way to set up your networking; right click network manager icon (top right in the notification area) and click "edit connections".

---

### Post by getack on 2010-08-03
For some reason there is no Network icon in the notification area. I am not at my machine now, but I will try again this afternoon. The "networking" app is the default Ubuntu app for UbuntuStudio. I think "network-settings" in terminal invokes it. I just read in another thread that the app is never installed by default in UbuntuStudio. Rather strange I think!
 
Here is a thread explaining my problem, and solving it!
[http://ubuntuforums.org/showthread.php?t=1485952](http://ubuntuforums.org/showthread.php?t=1485952)

---

