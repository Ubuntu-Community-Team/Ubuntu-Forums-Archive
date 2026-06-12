---
title: "Kismet driver problem?"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by taylor102387 on 2009-02-15
Ive been trying to crack my wifi, but I cant configure kismet. this is what I get when I try to run kismet:

```
taylor@taylor-laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (Linux): Enabling monitor mode for b43 source interface eth1 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.

```

I dont know what to do. Here is what I get when I run iwconig:

```
taylor@taylor-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

taylor@taylor-laptop:~$ 

```

How do I fix this?

---

### Post by azwar on 2009-02-17
Hi taylor,

It seem you have the same problem like me, you can refer to this page as I now can use the kismet by following some advice in this thread.
[http://ubuntuforums.org/showthread.php?t=1067390&highlight=kismet]("http://ubuntuforums.org/showthread.php?t=1067390&highlight=kismet")

---

