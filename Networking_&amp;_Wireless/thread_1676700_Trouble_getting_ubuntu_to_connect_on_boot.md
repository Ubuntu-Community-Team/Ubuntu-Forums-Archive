---
title: "Trouble getting ubuntu to connect on boot"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by Giruga on 2011-01-27
So, I'm somewhat new at the linux game but I had a situation where it is the best solution. I'm using a barebones computer to connect to a university network and then share the connection via a router. Additionally, it will eventually work as a file/print/torrent/whatever server. Right now I'm having issues connecting to the university network
 
The computer will not complete the connection on boot. If I attempt to force the connection to start with the following command,
 
```

sudo wpa_supplicant -ieth1 -c/home/girugaserver/wpa_supplicant.conf -Dwired -B
```
 
I get the following message
 
```

ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

```
 
If I go ahead and delete the file that it is talking about, and reissue the first command, it connects with no problem.
 
I'm sure that the gurus out there will need more information from me and I will be ready to give it.
 
NOTE: This is Ubuntu 10.04.1 Server Edition. No GUI here.

---

