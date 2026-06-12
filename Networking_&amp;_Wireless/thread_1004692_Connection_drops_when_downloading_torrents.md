---
title: "Connection drops when downloading torrents"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by jamiepgs on 2008-12-07
I've got a problem with Ubuntu 8.10, which is fully up-to-date.

Whenever I open a torrent program, after less than a minute the connection drops. However, it still says that I''m connected and it's reading a signal. Usually, taking out the adapter and plugging it back in will restore the connection, but it will still drop if I attempt to download a torrent. I've tried several programs (Transmission, Vuze and utorrent in wine) and it's still the same.

I did a search, and this problem was 'apparently' solved by changing the connection from 'wlan0' to 'lo' however, this didn't solve my problem. 

I checked the log and when it was connecting to my network, it was still saying it's connecting to 'wlan0' so I'm wondering if it should say it's connecting to wlan0 or lo, even though I've changed it to lo, because it's possible I didn't to it correctly.

```
Dec  7 19:26:12 jamie-compaq NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Dec  7 19:26:12 jamie-compaq NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Dec  7 19:26:12 jamie-compaq NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
```

I also tried changing the max upload and download speeds to 80% of my speeds in each program, still not yielding any sufficient results.

So, am I doing anything wrong or is there something else I can try?

I'm using a Zoom Wireless 4410B.

Thanks

---

### Post by jmoorse on 2008-12-07
Change your wlan0 to static IP.  I would recommend against binding anything to lo (local loopback)

---

### Post by jamiepgs on 2008-12-07
> **jmoorse said:**
> Change your wlan0 to static IP.  I would recommend against binding anything to lo (local loopback)
THANKS! Seems to be working so far, I'll keep you posted whether it stays on or not.

---

### Post by jamiepgs on 2008-12-07
Guess I spoke too soon, still dropped the connection.

Just to be sure I did it right, could you tell me, or point me somewhere, how to change it to a static IP. I did it using the network manager.

Also, I just looked at my router settings, says my IP is 192.168.1.101, when I set it to be 192.168.1.123, and 192.168.1.101 is what I got when it was DHCP, so I've clearly done something wrong :s

EDIT: Just looked at the log:
```

Dec  7 22:26:15 jamie-compaq avahi-daemon[4698]: Withdrawing address record for 192.168.1.123 on wlan0.
Dec  7 22:26:15 jamie-compaq avahi-daemon[4698]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.123.
Dec  7 22:26:15 jamie-compaq avahi-daemon[4698]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec  7 22:26:15 jamie-compaq avahi-daemon[4698]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Dec  7 22:26:15 jamie-compaq avahi-daemon[4698]: New relevant interface wlan0.IPv4 for mDNS.
Dec  7 22:26:15 jamie-compaq avahi-daemon[4698]: Registering new address record for 192.168.1.101 on wlan0.IPv4.

```

---

### Post by jmoorse on 2008-12-07
You can give it a shot from the terminal:
[http://ubuntuforums.org/showthread.php?t=457903](http://ubuntuforums.org/showthread.php?t=457903)

Be sure to alter the correct interface.

---

