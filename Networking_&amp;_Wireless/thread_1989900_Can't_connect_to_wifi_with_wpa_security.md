---
title: "Can't connect to wifi with wpa security"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by Jt00 on 2012-05-29
Hey everyone, I'm new here, and sorry if this has already been answered, but I can't use the search bar on my ipod touch (closes out the dropdown box when I type). Anyway, I got my Zyair AG-200 wireless adapter working with ndiswrap and configured my home wifi connection there. I tried to connect to my network, but it ignored the pre-configured settings in ndiswrap and asked me for a password, as well as encryption type. My first and foremost concern is the lack of WPA options. There are 2 WEP options, a five character password and a 128-bit option, then LEAP, then Dynamic WEP. My router is configured for WPA personal. Ndiswrap had this option, but the built-in wireless connection setup doesn't. How can I connect to my network?
A smaller concern of mine is having to pick the encryption type everywhere you go. If I have my ipod I can just use a wifi analyzing app, but if I am without it, I am at the mercy of the owner's memory (most people only remember their password and have forgotten/weren't told what the encryption is. Seems like there should be an auto-detect feature.
This is Ubuntu 10.04 LTS on a Compaq Presario 1244.

---

### Post by mringer on 2012-05-29
Warning: I am a beginner myself.

I believe that wicd can scan nearby wireless routers and tell you
the type of encryption. You need a companion program called the tray
icon. Beware of the booby trap: you cannot run wicd and Network
manager at the same time, they interact badly. You must make sure 
that you remove NM before starting Wicd (& vice versa). Also it 
would probably be a good idea to make sure that you have the package
file for NM in a safe place in case wicd refuses to work for you.

---

