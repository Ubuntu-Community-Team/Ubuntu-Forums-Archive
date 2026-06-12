---
title: "Network drops with no error"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by afeather on 2010-05-31
Just installed 10.4 server on brand new hardware.  Have Samba running so XP machines can mount file systems.  Have PS3 Media Server running to stream content to PS3.  Network regularly drops out on the server.  If you are accessing files on from the Samba filesystem on the XP machine(s), the window will suddenly disappear.  PS3 Media Server will be serving up video and video suddenly hangs.  Even telnet sessions to the server suddenly drop out.  No error messages in Samba logs or PS3 Media Server logs.  Only error message I can find is this from the system log with no other surrounding information:

May 31 08:09:41 djlance AptDaemon: INFO: Quiting due to inactivity
May 31 08:09:41 djlance AptDaemon: INFO: Shutdown was requested
May 31 08:09:41 djlance AptDaemon: INFO: Initializing daemon
May 31 08:14:42 djlance AptDaemon: INFO: Quiting due to inactivity
May 31 08:14:42 djlance AptDaemon: INFO: Shutdown was requested
May 31 08:14:42 djlance AptDaemon: INFO: Initializing daemon

Network will come back rather quickly, just odd that it drops in the first place.  I have been using Ubuntu for years now on servers and on my laptop and I've never had issues.

I have tried installing a different network card in the machine with same results.  I have a hardcoded IP address for the machine:

iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

I will be willing to send any information if someone knows of what might be the problem.

---

