---
title: "Network fails"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by ygoe on 2013-05-19
I have installed Ubuntu 12.04 Desktop on my ALIX computer. Once again after a long time. At first it was working fine. I could SSH to the box. But I noticed that my DNS configuration wasn't applied because the method to do it has changed. So I replaced the files in /etc/resolvconf/resolv.conf.d/ to have the correct nameservers written in /etc/resolv.conf. After a reboot, the network fails completely. I cannot establish any network connection in or out. The eth0 interface is up, has a static IPv4 address assigned but reports some packets sent and some packets received, but mostly all of them dropped. Nothing about the problem in the syslog.

What's up here? What can I do do analyse the problem and fix it? I'm absolutely clueless why this damn thing is failing again...

---

### Post by Iowan on 2013-05-19
Have you tried pinging by IP address?
 Have you checked your routing table?

---

### Post by ygoe on 2013-05-20
Ping says all packets were lost. The route looks normal (default gateway is my DSL router, its IP address is explicitly set as a route).

Update: I've pinged my Windows box with Wireshark running. I can see an echo request coming in an all the replies going out. Seems the Ubuntu box rejects any incoming packets. iptables is not installed. Can there be a firewall setup anyway?

Update 2: I found that after my Wireshark monitoring, Ubuntu accepts all ping replies from my Windows box, but still from no other computer (like the DSL router). Something is unpredictable in that system.

---

### Post by ygoe on 2013-05-20
More hw info: This is an AMD Geobe board with a VIA Rhine-III ethernet adapter. It is connected to my Gigabit switch which has always worked fine for all other devices. The ping capability is very random. I have four other machines up for testing right now.

1. FritzBox DSL router
2. My desktop computer, Windows 7
3. The ALIX' "father", created the image with debootstrap from there, running on my desktop in VMware, Ubuntu 12.04
4. Smartphone RAZR i, Android, via WiFi

I cannot get an echo reply from the FritzBox at any time. I sometimes get a single reply from my desktop, the rest is dropped. I always get all replies from the Ubuntu VM client. After that, I also get all replies from my desktop. But not forever. The smartphone also seems to work always.

I see ARP messages in Wireshark, and the ALIX system has some entires in its ARP cache. I cannot flush it, doesn't seem to be possible with the arp command. Didn't check the correctness of the MAC addresses, but since the packets are counted as "dropped", I assume everything is fine on the network layer and the problem is inside the ALIX Ubuntu system, either network driver or OS level.

Last time I can remember I used this, was with Ubuntu 11.10 I think, and everything was good there. (Except other issues after which I had the ALIX board replaced but untested since then.) Does Ubuntu 12.04 (with latest updates and kernel 3.2) have some issues here?

Added: The FritzBox also has a Fast Ethernet switch built-in, but the ALIX doesn't even get a link with it (light stays off). So I can only test with my Gigabit switch.

---

