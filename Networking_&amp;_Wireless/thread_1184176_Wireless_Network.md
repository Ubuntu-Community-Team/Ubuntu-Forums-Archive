---
title: "Wireless Network"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by obarima on 2009-06-10
Does one necessarily have to download and install a Windows wireless driver ("bcmwl5.inf") on Ubuntu Jaunty to make it run a wireless LAN on Dell Latitude D610? Somebody, please clarify this for me.

---

### Post by superprash2003 on 2009-06-11
it depends on your card , post output of lshw -C network from the terminal , have you looked for drivers under system->admin->hardware drivers ?

---

### Post by pastalavista on 2009-06-11
It would probably work better if you upgraded to Hardy. There are drivers for them [in the repositories]("http://packages.ubuntu.com/search?suite=default&section=all&arch=i386&searchon=all&keywords=Intel+Wireless+2200BG+802.11+b%2Fg"). The Dapper drivers would probably work without upgrading.

---

### Post by MaindotC on 2009-06-11
Did you mean upgrade to Koala or DOWNGRADE to Hardy?

---

### Post by pastalavista on 2009-06-11
> **strAlan said:**
> Did you mean upgrade to Koala or DOWNGRADE to Hardy?
Sorry, I had him confused with another post who was still running Gutsy. I would have to say, with Jaunty, I doubt his Windows drivers would be necessary or even advisable. Had to do a lot of that kinda stuff with older releases... there should be a driver available but he might first have to connect via wired ethernet to download them

---

