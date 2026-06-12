---
title: "Network adapter driver can't get any signal when network manager request 'disconnect'"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by howwow20 on 2011-08-08
I'am developing a wireless USB data modem(3G, LTE).

USB Network adapter driver can't get any signal when network manager request 'disconnect'.(that means click disconnect in Network Manger).
 
Also, I checked belows after Network Manager request 'disconnect'.
1. ifconfig <name> -> Status is RUNNING
2. ethtool <name> -> Link detected: yes
3. /sys/class/net/ptuml290/carrier value is 1(link on)
 
I think that Connection is not actually disconnected. Because RUNNING is not appared, yes -> no, 1 -> 0 when connection is disconnected. 
---------------------------------------------------------------------------------------------- 
1. Why doesn't USB Network Adapter get any signal when network manager request 'disconnect'?
   Driver need a signal to process 'disconnect request'.
   Is it normal? I think that this issue is because of ubuntu(actually Network Manger).
----------------------------------------------------------------------------------------------

And after Network Manger request 'disconnect', Connection Manager's status is 'Connect-dormant'.
----------------------------------------------------------------------------------------------
2. Is there any way for Connection Manager's status to change from 'Connect-dormant' to 'disconnected' ?
----------------------------------------------------------------------------------------------

Thanks in advance.

---

