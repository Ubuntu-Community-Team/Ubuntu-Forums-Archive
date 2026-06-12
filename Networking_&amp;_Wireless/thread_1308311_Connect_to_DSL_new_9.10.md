---
title: "Connect to DSL new 9.10"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by bob brazie on 2009-10-31
I have just finished a clean install of 9.10 and have no connection to my DSL modem.

I have tried both Ethernet and USB connections to my actiontec modem. It is working (the modem) as I am using  it on this machine using Ubuntu 8.10.

If I check network connections Auto Ethernet is shown.


When I  hover over the icon in the top bar it says wired network connection "Auto eth0 is active" 

I cannot connect to any sites in firefox and an update manager try returns errors that it cannoct connect.

Am I missing something that needs changing?

Thanks in advance. Bob.

---

### Post by faical117 on 2009-10-31
Try this command in the terminal -> sudo pppoeconf
(use the Ethernet modem port)

---

### Post by bob brazie on 2009-10-31
It says not connected.

It says that the access concentrator of your provider did not respond.

And possibly another running pppoe process might be running which controls  the modem.

??

---

### Post by bkratz on 2009-10-31
> **bob brazie said:**
> I have just finished a clean install of 9.10 and have no connection to my DSL modem.

I have tried both Ethernet and USB connections to my actiontec modem. It is working (the modem) as I am using  it on this machine using Ubuntu 8.10.

If I check network connections Auto Ethernet is shown.


When I  hover over the icon in the top bar it says wired network connection "Auto eth0 is active" 

I cannot connect to any sites in firefox and an update manager try returns errors that it cannoct connect.

Am I missing something that needs changing?

Thanks in advance. Bob.


Please see the below thread:  It doesn't look like good news for dsl users.

[http://ubuntuforums.org/showthread.php?p=8191083#post8191083](http://ubuntuforums.org/showthread.php?p=8191083#post8191083)

see posts 4 and 5.

---

### Post by Iowan on 2009-10-31
If your Actiontek is like mine, it should look like a router to Ubuntu. Did you set it up as DSL before? 
Does **ifconfig -a** provide the expected IP address, etc.?

This laptop runs Jaunty - I haven't gotten Karmic yet.

---

