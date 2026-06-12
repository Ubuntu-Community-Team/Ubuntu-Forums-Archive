---
title: "bit torrent issues"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by ryant on 2006-07-09
Ok this is strange...

Running bit torrent on windows, works fine.

Boot into ubuntu, run bit torrent (tried default bit torrent client and azureus).  torrent does not upload, eventually leads to no download speed.

ok, port forwarding, setup a few ports for the torrent apps and forwarded them on the router to the client computer.

open up bit torrent and it works for about 5 minutes, uploading works, 5 minutes later, both upload and download go to 0kb/s and stay there.

is there any internal firewall in ubuntu that could be blocking this?  any solutions?

Thanks,
ryan

---

### Post by davidsxls on 2006-07-09
no firewall by default.

---

### Post by ryant on 2006-07-09
ok, what could be causing this then?

---

### Post by Shampyon on 2006-07-10
I just tried to use bittorrent, and the download rate was terrible. I used Firestarter to configure the ports to be open, the same as they were in XP and on my router.

Problem: I haven't been able to even access my router from Ubuntu for days.

I know there's no firewall by default, but isn't this because most of the ports are closed by default, unlike in Windows? Would making those ports available in Firestarter be enough, or is there something else necessary to open up the ports?

---

### Post by blissend on 2006-07-14
> **Shampyon said:**
> ...

I know there's no firewall by default, but isn't this because most of the ports are closed by default, unlike in Windows? Would making those ports available in Firestarter be enough, or is there something else necessary to open up the ports?

This is something I'd like to know. I think these ports are closed and mine wouldn't function properly until I forwarded it with firestarter.

---

