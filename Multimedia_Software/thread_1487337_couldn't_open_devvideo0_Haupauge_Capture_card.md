---
title: "couldn't open /dev/video0 Haupauge Capture card"
date: 2010-05-18
forum: Multimedia Software
---

### Post by followet on 2010-05-18
I'm trying to watch tv and record some vhs tapes onto my desktop. I've tried to run a couple programs, but they don't launch or they exit themselves. I'm now trying Zapping TV Viewer and it's giving me an error message:

Couldn't open /dev/video0, try other devices? Y/N

clicking y gives me another window of the same size, but with no text.

I've run this 

```
followet@followet-desktop:~$ dmesg | grep video
[    0.590518] pci 0000:00:02.0: Boot video device
[   14.449226] Linux video capture interface: v2.00
followet@followet-desktop:~$ lspci | grep video
03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 04)
followet@followet-desktop:~$ 
```Does anyone have any help for me?

---

### Post by kiddykoff on 2010-05-19
bump

---

### Post by kiddykoff on 2010-05-20
can anyone help?

---

