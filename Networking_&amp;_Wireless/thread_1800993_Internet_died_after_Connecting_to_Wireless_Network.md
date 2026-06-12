---
title: "Internet died after Connecting to Wireless Network."
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by kexus on 2011-07-09
At my house, I have a wireless router, but my desktop computer is connecting to it, or maybe to the modem, by an Ethernet cable.  It has a built-in wireless card, so just as an experiment, I tried to connect to my network wirelessly.  It didn't work.  And not only did I not get any internet connection, I can't get any internet through the wired connection either.  The internet works fine with Windows Vista (I'm dual-booting), as well as when I boot up Backtrack off of a Live DVD.  I can still access my router's config page by going to 192.168.2.1 on a web browser, but I can't access anything else.  Any ideas as to why this is, or how to fix it? Any help would be greatly appreciated.

---

### Post by nm_geo on 2011-07-09
> **kexus said:**
> At my house, I have a wireless router, but my desktop computer is connecting to it, or maybe to the modem, by an Ethernet cable.  It has a built-in wireless card, so just as an experiment, I tried to connect to my network wirelessly.  It didn't work.  And not only did I not get any internet connection, I can't get any internet through the wired connection either.  The internet works fine with Windows Vista (I'm dual-booting), as well as when I boot up Backtrack off of a Live DVD.  I can still access my router's config page by going to 192.168.2.1 on a web browser, but I can't access anything else.  Any ideas as to why this is, or how to fix it? Any help would be greatly appreciated.

So the wireless attempt killed the INTERNET OMG...
Just a try at humor there..

let try something out of the wild-blue yonder..

In terminal 
```

sudo modprobe ssb
```
```

sudo modprobe b44
```

Let me guess you were trying to install the STA (wl) wireless driver?

---

