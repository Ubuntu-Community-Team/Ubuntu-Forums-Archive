---
title: "Samba Timeout"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by UltraZone on 2009-12-11
Situation:  I use samba to connect to a NAS drive (it's connected to my wireless router).  My laptop connects to the wireless router, and the NAS drive is mounted using smb://192.168.2.103 (the local IP of the NAS).  The NAS is full of music but when I use Rhythmbox to play, at minute 5:09 of every song the connection gets lost and Rhythmbox skips to the next one.  So due to the repeatability of this problem I think that there must be some setting in an .rcf file somewhere telling samba to cut off at 5 minutes.  Anyone know where this setting is located?  Note that I actually have installed samba-common, which I think is all I need to connect to SMB servers.

---

### Post by capscrew on 2009-12-11
> **UltraZone said:**
> Situation:  I use samba to connect to a NAS drive (it's connected to my wireless router).  My laptop connects to the wireless router, and the NAS drive is mounted using smb://192.168.2.103 (the local IP of the NAS).  The NAS is full of music but when I use Rhythmbox to play, at minute 5:09 of every song the connection gets lost and Rhythmbox skips to the next one.  So due to the repeatability of this problem I think that there must be some setting in an .rcf file somewhere telling samba to cut off at 5 minutes.  Anyone know where this setting is located?  Note that I actually have installed samba-common, which I think is all I need to connect to SMB servers.

Are you using dhcp to provide IP addressing (even if the addreses are fixed)?

If so, and the lease is for 5 minutes, then when the lease is renewed, the Samba daemon (smbd) is reloaded and you loose connectivity.

The cure, if you are connected this way, is either assign a fixed (manually configured (e.g NO DHCP)) IP address (prefered) or a reserved IP address with a permanent DHCP lease.

---

### Post by UltraZone on 2009-12-15
I did fiddle with the wireless router settings, but changing to static IP made it worse (ie. songs cut out at random times, even as little as ~2mins).  The Auto DHCP lease time is set to 0 minutes which means one day (according to the router settings webpage :-k](*,)).  I also set it to 60 minutes, but nothing changed for the better.  Is there any setting that I can fiddle within SMB to get around this?  I hate to say it but playing iTunes when booting into Windows doesn't have this problem (the NAS is a mapped drive).  Any ideas?

---

### Post by kingjm on 2010-01-27
I am having similar problems. I have upgraded my server from 8.04.3lts to karmic. In the old system the samba server never crapped out. Now after the upgrade this is a continual problem. I am also looking for a solution.

---

### Post by reqlar on 2011-01-17
I'm having the exact same problem.  I have my windows computer setup with iTunes, and all my music shared.  When I access my shared music via smb, I can connect and browse and play songs, but the connection times out after 5 minutes.  I don't have the same problem when connecting from another windows machine.  I noticed that when my music stops playing the icon in Nautilus that indicated the SMB share is mounted DISAPPEARS!

---

