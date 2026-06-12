---
title: "Auto Network Config Command Line"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by LGN on 2011-01-22
Hello all,

I just recently installed ubuntu server.
I want to be able to install packages and such but can't until I connect to Internet.
I tried wifi but couldn't figure out how (I'm a n00b) but now I have ethernet and can't figure out how to make it work.

So my question is, how do I connect to my Ethernet with ubuntu server, I could if I had graphical, but I can't get that until I have Internet.

I didn't configure network during install, so how do I do it now?

---

### Post by Iowan on 2011-01-22
Servers (as I recall) still use */etc/network/interfaces* for network configuration. Do you plan to use DHCP or static addressing (more common for servers)?

---

### Post by LGN on 2011-01-22
It's a home server, I think the cable company gives us DHCP.
Though the way I have it hooked up currently is via OS X Internet sharing with an Ethernet cable, if that makes any difference

---

### Post by LGN on 2011-01-22
Got it working!!!

But I can't get repos to update, something about unable to reach security.ubuntu.com
But I can connect, I pinger google.com and it worked perfectly!

---

