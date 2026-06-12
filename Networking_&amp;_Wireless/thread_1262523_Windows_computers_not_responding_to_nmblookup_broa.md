---
title: "Windows computers not responding to nmblookup broadcasts"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by cromlor on 2009-09-10
Samba is working correctly, WINS server is running and all functionality Windows><Ubuntu is working perfectly with regards file sharing. I have no issue as such.

However when I execute a `nmblookup anywindowspc` from a Ubuntu terminal the windows computers never reply to it. I can see the broadcast going out but it gets no reply. When other Windows computers generate these commands in relation to each other they respond to each other (I can see the broadcasts and replies using Wireshark). It's only when I generate these commands on Ubuntu will the Windows computers (Vista Home Premium 32bit and Ultimate x64) not respond. This goes both for name queries generated automatically by the OS and when I use the command line.

Examining them closely the Windows nbtstat query and the Ubuntu nmblookup query seem to produce identical outputs yet one gets a response and the other one doesn't.

Anybody know why this is happening?

---

### Post by ballards on 2009-10-16
> **cromlor said:**
> Anybody know why this is happening?

Cromlor, did you ever find a solution? I have the same issue and can't figure it out either.

---

