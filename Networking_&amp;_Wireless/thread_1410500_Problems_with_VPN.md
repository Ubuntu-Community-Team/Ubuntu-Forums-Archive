---
title: "Problems with VPN"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by Zorn@41 on 2010-02-18
I am running Ubuntu 9.10 on a laptop with VMWare Workstation 7 installed. Ubuntu is the host operating system. I have built a Windows XP Virtual Machine on the laptop. 

Here are the problems I am seeing with VPN. 

1. When VPN is running on the Ubuntu host and running a speed test from Speedtest.net, the upload piece hangs. The Windows XP guest running VPN does not have any problems.
2. When VPN is running on the Ubuntu host and trying to connect to an Oracle database, I get a connection lost and the Oracle server reports a time out on the incoming connection. Again the Windows XP guest running VPN does not have any problems.
3. When VPN is running on the Ubuntu host and trying to connect to our Citrix web portal, the site trys to load but hangs and then brings back a blank screen. Again the Windows XP running VPN does not have any problems.

All of the above functions work fine on the Ubuntu host when I am at work and connected directly to the internal LAN.

I am at a complete loss as to what could be happening. Any suggestions would be much appreciated.

---

