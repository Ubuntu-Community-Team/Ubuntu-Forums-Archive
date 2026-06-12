---
title: "lircd.conf for gigabyte u7000 remote?"
date: 2009-01-11
forum: Mythbuntu
---

### Post by pdwerryhouse on 2009-01-11
Hi all,

Has anyone got the small credit-card sized remote control that comes with a Gigabyte U7000 USB DVB receiver working? I'm looking for a working lircd.conf file for it.

The remote control itself appears to be recognised, because when I press buttons on it, I get kernel messages such as:

```
Jan 11 21:00:01 rove kernel: [ 3496.100305] dib0700: Unknown remote controller key:  B  0  0  0
Jan 11 21:00:01 rove kernel: [ 3496.252296] dib0700: Unknown remote controller key: 1F 13  0  0
Jan 11 21:00:05 rove kernel: [ 3500.208322] dib0700: Unknown remote controller key: 14 7E  1  0
Jan 11 21:00:06 rove kernel: [ 3500.518061] dib0700: Unknown remote controller key: 14 7F  1  0
Jan 11 21:00:06 rove kernel: [ 3501.276266] dib0700: Unknown remote controller key: 19 7C  1  0

```

I guess all I need is the correct lircd.conf file to translate these 'unknown keys' into something useful...

Thanks,

Paul

---

### Post by aresthedog on 2009-02-11
Hello! 
Have you have managed to set the remote control ?

Thx

---

