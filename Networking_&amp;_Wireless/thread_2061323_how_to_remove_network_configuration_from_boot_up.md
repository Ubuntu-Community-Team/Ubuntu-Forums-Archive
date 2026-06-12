---
title: "how to remove network configuration from boot up"
date: 2012-09-22
forum: Networking &amp; Wireless
---

### Post by shariharan301 on 2012-09-22
hi. Am using Ubuntu 12.04 Desktop LTS.

when i boot my ubuntu,following configuration msg is appear.
 "wait for network configuration" & " waiting for 60 more seconds for network configuration". 

After booting system without LAN connection. Network notification icon is not appearing.?

can u help pls..?

Thanks in Advance...

---

### Post by shariharan301 on 2012-09-23
Finally i got the result..

_To skip the network configuration time while system starting.. do the following steps._

1. Type the cmd in terminal.
   "gksudo gedit /etc/init/failsafe.conf" (suppose access permission is not available. pls provide it.)

2. After the open the file. make some changes wat i mention.

on line 26 -> change "sleep 20" to "sleep 5".
on line 32 -> comment the sleep time using '#'. (eg: #sleep 40)
on line 35 -> comment the sleep time using '#'. (eg: #sleep 59)

then save it. and restart.


_without LAN Cable activate Network Manager._
_No need to connect LAN Cable, while system boot. easy way to config network manager._

on File system-> etc -> network -> Interfaces

edit the "interface" file.. using following content to replace the existing content.

//

auto lo
iface lo inet loopback

//

This is working for me..

---

### Post by OrangeMadness on 2012-09-23
You are getting that message because something is wrong with your network configuration. A better approach is to look for what is wrong and try to fix it rather than get rid of the message!

Try:
```

ifconfig -a

```

Bring your interfaces down one by one  with:
```

ifconfig <interface> down

```

Reset the network:
```

/etc/init.d/networking reset

```

Dont forget to bring your interfaces up one by one
```

ifconfig <interface> up

```

Almost certainly you will see some error, like a misconfigured interface.

---

### Post by jander on 2012-11-14
As far as I could see, the message and the delay will occur when the interface eth0 is in the /etc/network/interfaces file and the cable is not connected.

My solution was just to leave the loopback interface there and let NetworkManager handle any other interface.

I had no time to take a closer look...

J

---

