---
title: "VERY slow SMB performance in Win7"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by mons00n on 2012-05-14
Hi everyone,

I've done a lot of searching but have been unable to find an actual answer to my question.  I basically have a 12.04x64 file server sharing folders via samba over a gigabit wired network.  To my MAC it works flawlessly, transfer speeds are beautiful.  To my Windows7 machine that's a different story; they're excruciatingly slow.  We're talking ~1meg/sec.  I've tried all the smb.conf tricks I found from previous posts (socket_options, so_recbuf, so_sndbuf, rlimit_max, iptos_lowdelay, so_keepalive, etc) and none of them have worked.  Has there been any type of resolution for this?  Since it works great with OSX I think it's a problem on the windows side...

---

