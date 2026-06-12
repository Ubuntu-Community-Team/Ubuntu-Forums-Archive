---
title: "SCP/SFTP slow downloads but fast uploads"
date: 2012-09-13
forum: Networking &amp; Wireless
---

### Post by mmulqueen on 2012-09-13
Hello,

I have a server running Ubuntu 11.10 and am having trouble with download speeds over SSH.  The server is running OpenSSH_5.9p1.  I am able to download files via HTTP at about 56MB/s but downloads via SFTP or SCP are more like 52KB/s.  Upload speeds are fine.  I've been searching for a while and not found many discussions on this topic.  One answer suggested that the problem may be hardware related.  I tested this by switching NICs with another server last night and still found the same problem.  Does anyone know what could be causing this?

Thanks,

Matt

---

### Post by mmulqueen on 2012-09-20
*Bump*

It looks like not many people have had this problem before.  I'm planning to reinstall OpenSSH tonight to see if that helps.

---

### Post by mmulqueen on 2012-09-20
That didn't work.  Downloads from the server via SFTP and SCP are still very slow while uploads are fast.  Anyone have an idea as to what this could be?

---

### Post by Rsxhawk on 2012-09-24
First thing you should always do when dealing with a possible network issue, is check the speed and duplex of the ethernet interface that you are using at both ends and all along the path.  Make sure there are no speed/duplex mismatches anywhere on your network, replace the cables if you have to.  ifconfig -a in unix/linux should show you the interface stats if there are errors incrementing.  Any of these type of issues will slow you down.  To make things easy, set everything to auto/auto.

A good place to check as well is the router/switch that is in between the client and server. 

Beyond that, make sure there is no transfer rate limit on the client application or server side configuration.  If HTTP downloads are fast and just these others are slow, could just be application related.

---

### Post by nodeon on 2012-10-09
I'm glad I found someone with the same problem. I have the same issue with completely different setup. The server is a Windows 2008 R2 with WinSSHD and I am doing the transfers with pscp.exe. The funny thing is, when I use a different client (WinSCP, MobaXterm etc.), there is no problem. So I wonder if it is a configuration issue. If you found a solution, I would be glad for an update.

---

### Post by Mephist0 on 2013-04-05
> **mmulqueen said:**
> Hello,

I have a server running Ubuntu 11.10 and am having trouble with download speeds over SSH.  The server is running OpenSSH_5.9p1.  I am able to download files via HTTP at about 56MB/s but downloads via SFTP or SCP are more like 52KB/s.  Upload speeds are fine.  I've been searching for a while and not found many discussions on this topic.  One answer suggested that the problem may be hardware related.  I tested this by switching NICs with another server last night and still found the same problem.  Does anyone know what could be causing this?

Thanks,

Matt

Hello! 
I had the exactly same problem as you.. Fast upload speeds 10-11MB/s on a 100Mbit connection.. But only 52KB/s in download speed. But i also found the problem! Maybe it will help some of you!
The problem was that my network adapter were set to 100Mbit HALF DUPLEX. I did turn off auto negotiation and set the NIC to FULL Duplex. That solved my problem. 

My server was running on SLES 10 and i did the following to fix it:

ethtool -s eth0 autoneg off
ethtool -s eth0 duplex full

---

