---
title: "Issue connecting through ethernet"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by Jollyollydog66 on 2009-02-20
I'll start this by saying that this is the first time I've tried to connect to the internet though ethernet on a Linux machine. On both my Windows machines by setting the network to find the information automatically (ip and whatnot) I've had no issues. I can't seem to connect on a Linux machine through DCHP or static ip address though. My router says it has activity and my ethernet port was detected so I don't know what the issue is.

---

### Post by ugm6hr on 2009-02-20
We will need more detail to help.

Have a look at the Wifi help link below (much of it also applies to ethernet).

Then, plug the ethernet in, reboot, and run the following:
```
ifconfig
lspci
lshw -class network
route -n
ping -c 3 http://208.67.219.101/
ping -c 3 http://www.opendns.com/
```

Copy and paste everything that comes out back here.

---

