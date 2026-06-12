---
title: "Transmission says Port closed for Linksys WRT54G after PortForward"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by RonB123123 on 2010-10-24
My port is set to 51413 for Transmission v2.11. I have a Linksys WRT54G with firmware 3.03.6. My local IP address is 192.168.1.7. My MTU is set to auto and I have tried to set it at 1492 to see if there was a significant difference. 

Here is a screenshot of my port forwarding settings. 
[img]http://img836.imageshack.us/img836/4609/screenshotrb.png[/img]

I found this topic archived but didn't get a solution:
[http://ubuntuforums.org/archive/index.php/t-879334.html](http://ubuntuforums.org/archive/index.php/t-879334.html)

They mentioned a command to check if Ubuntu saw the port as open and it did.
[quote=terminal]
$ nc -z -v -w2 192.168.1.7 51413
Connection to 192.168.1.7 51413 port [tcp/*] succeeded!
[/quote]

Why is Transmission not seeing that the port is open? Is it a setting on my router, Ubuntu Lucid, Transmission, or a bug?

My router also has UPnP enabled and its enabled in Transmission so why does my router need to forward the port? My speeds are around 50 kb/s with a lot of seeders. Used to be much higher and I have tried many torrents. All seem to be about this speed.

Thank you,
Ron

---

### Post by claracc on 2010-10-25
I have had this same problem with transmission or deluge in any ubuntu distro since jaunty.

I think is a fault in these programs. I have an edimax BR6204 wg router UPnP enabled, port forwarded from ufw and in the router but deluge and transmission always detect port closed. I gave up to use these programs.

I recommend to use ktorrent or qbittorrent, they don't present any problem with forwarding ports to share files

---

### Post by RonB123123 on 2010-11-21
Thank you. I'm using Deluge now and I'm much happier. It's too bad Transmission was giving me that problem because I like how quick Transmission is. Oh well.

:D
~Ron

---

