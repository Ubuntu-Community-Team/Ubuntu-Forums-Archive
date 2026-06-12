---
title: "Wired connection: WAN drops, but LAN OK"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by easye1161 on 2010-08-17
I've had a computer running Ubuntu connected to my TV for a few weeks now, but as of yesterday, I can't get it to keep a connection to the Internet.  

Everything works well for an hour or so after a reboot, but then no WAN connections work.  When this happens, no sites load in Firefox or Chrome, I can't ping Google, I can't SSH to the box from work, and none of the pages I have running on apache load from remote computers.  However, all local area connections seem to work fine.  SSH from within my LAN takes much longer than usual, but it does still connect.

Anyone have any ideas on how to troubleshoot this?  If more information is needed, please let me know!  Thanks.

---

### Post by Iowan on 2010-08-17
Check contents of */etc/resolv.conf* before/after. Also see if **route -n** results change. [Here]("http://ubuntuforums.org/showthread.php?t=971064") is an older thread that *might* be similar.

---

### Post by easye1161 on 2010-08-17
> **Iowan said:**
> Check contents of */etc/resolv.conf* before/after. Also see if **route -n** results change. [Here]("http://ubuntuforums.org/showthread.php?t=971064") is an older thread that *might* be similar.

Thanks for the tip, but that wasn't it.  It's still set to

nameserver 8.8.8.8
nameserver 8.8.4.4

like it should be.  (Those are Google Public DNS servers).  I tried setting it to the more standard

nameserver 4.4.4.1
nameserver 4.4.4.2

and it still had the same problem.

---

