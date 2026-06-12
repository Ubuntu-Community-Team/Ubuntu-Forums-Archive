---
title: "Auto mount Airport Network drives"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by Hyter on 2009-11-10
I'm trying to get my Airport Extreme network drives to mount on boot.
But I haven't gotten any luck yet.

I've added this to /etc/fstab 
```
#Network Drives
//jesse-airport.local/MOVIES/meda/movies /media/movies smbfs guest 0 0
//jesse-airport.local/tv%20shows/TV%20Shows /meda/tv smbfs guest 0 0
```

When I type "sudo mount -a" I get this...
```
Warning: mapping 'guest' to 'guest,sec=none'
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
Warning: mapping 'guest' to 'guest,sec=none'
mount error: can not change directory into mount target /meda/tv
```

Any suggestions?

---

