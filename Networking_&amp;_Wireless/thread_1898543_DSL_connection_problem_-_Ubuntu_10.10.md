---
title: "DSL connection problem - Ubuntu 10.10"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by anku94 on 2011-12-21
Hi gurus

Ubuntu version: 10.10

I use a router to connect to the internet via a router. It works perfectly on Windows 7 installed on the same laptop, accessed via the same ethernet card.

Normally, I use bridged mode to connect to the internet. So, I used pppoeconf and the pon dsl-provider to configure and connect to the net. It disconnects after a while and plog is like this (this one was copied from the internet, but the error messages are the same).

Aug 21 23:56:33 mandalai pppd[9177]: CHAP authentication succeeded 
Aug 21 23:56:33 mandalai pppd[9177]: peer from calling number 00:30:88:01:A3:34 authorized 
Aug 21 23:56:33 mandalai pppd[9177]: local  IP address 92.72.175.71 
Aug 21 23:56:33 mandalai pppd[9177]: remote IP address 92.72.160.1 
Aug 21 23:56:33 mandalai pppd[9177]: primary   DNS address 195.50.140.116 
Aug 21 23:56:33 mandalai pppd[9177]: secondary DNS address 195.50.140.246 
Aug 21 23:59:00 mandalai pppd[9177]: No response to 4 echo-requests 
Aug 21 23:59:00 mandalai pppd[9177]: Serial link appears to be disconnected. 
Aug 21 23:59:00 mandalai pppd[9177]: Connect time 2.5 minutes. 
Aug 21 23:59:00 mandalai pppd[9177]: Sent 3877 bytes, received 5475 bytes. 
Aug 21 23:59:06 mandalai pppd[9177]: Connection terminated. 
Aug 21 23:59:06 mandalai pppd[9177]: Modem hangup 
Aug 22 00:00:11 mandalai pppd[9177]: Timeout waiting for PADO packets 
Aug 22 00:00:11 mandalai pppd[9177]: Unable to complete PPPoE Discovery 
Aug 22 00:01:16 mandalai pppd[9177]: Timeout waiting for PADO packets 
Aug 22 00:01:16 mandalai pppd[9177]: Unable to complete PPPoE Discovery 
Aug 22 00:02:21 mandalai pppd[9177]: Timeout waiting for PADO packets 
Aug 22 00:02:21 mandalai pppd[9177]: Unable to complete PPPoE Discovery 
Aug 22 00:03:26 mandalai pppd[9177]: Timeout waiting for PADO packets

So, I tried switching to the PPPoE/PPPoA mode (the one in which the router automatically connects to the internet). Again, it worked fine on Windows, but when I restarted into Ubuntu, the internet didn't work. Can you help? Thanks.

Please let me know if you require any more information about my laptop. It's a HP dv6 6165tx.

PS: If it helps, I'm unable to access my router settings on Ubuntu. The page - 192.168.1.1 doesn't open. I am also unsuccessful in connecting to the device via telnet in Ubuntu. If I use ifconfig, it displays an IPv6 address assigned to eth0, and no IPv4 address. When I remove and re-insert the LAN wire in Ubuntu, I don't get any 'eth[n] is connected/Connection established' message. But I have been able to successfully access the internet for short periods (in Ubuntu) using the PPPoE/PPPoA mode and pppoeconf command. In Win7, it works for hours without any interruption.

Any help would be appreciated. Thanks a lot.

---

