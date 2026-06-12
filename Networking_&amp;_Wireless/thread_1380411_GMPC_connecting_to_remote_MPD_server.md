---
title: "GMPC connecting to remote MPD server"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by eiffel on 2010-01-13
Hi,

My setup is a laptop and a workstation both connected up to my router.  I want to play music on the laptop (which is connected up to speakers) and also control it from my workstation.  

I've setup mpd on the laptop and can play and interact wth my music fine on that machine.

However, I simply can't connect to mpd from my workstation.  Putting in the IP of my laptop gives:

```
13/01/10 21:01:53: ERROR:   /build/buildd/libmpd-0.18.0/./src/libmpd.c mpd_check_error():#261:	Following error occurred: 13: code: 0 msg: problems connecting to "XX.X.XX.X" on port 6600: Connection refused
```

I can't see a firewall on my laptop and netstat tells me it is listening on port 6600.

I've also tried commenting out bind_to_address in .mpdconf.

Nothing works.

Any help or advice or thoughts on where I can go from here would be most appreciated.

---

