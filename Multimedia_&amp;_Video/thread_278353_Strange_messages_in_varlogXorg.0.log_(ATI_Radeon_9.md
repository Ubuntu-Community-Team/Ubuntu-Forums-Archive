---
title: "Strange messages in /var/log/Xorg.0.log (ATI Radeon 9600)"
date: 2006-10-16
forum: Multimedia &amp; Video
---

### Post by epennings on 2006-10-16
I need some help tweaking my (xorg) configuration for ATI radeon 9600.

I was looking at my /var/log/Xorg.0.log today and noticed this line :
```
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
```

I have a single ATI Radeon 9600, with 2 BusID's (PCI:1:0:0) and (PCI:1:0:1)
The first one is working properly(3d rendering and stuff)
I am not sure what to do about the second one.
Is it for tv-out perhaps? Or Dual-Head (I have both DVI and D-sub, using DVI)?
I already tried adding a copy of the current device section in my xorg.conf with that BusID and a different identifier, but that didnt help either.

Another thing I noticed was this :
```

drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
.
.
.
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card254
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
```

It looks like it's trying to find a card that doesnt exist (related to BusID PCI:1:0:1?). I'd like to disable that if possible.

I hope someone can help me fix this little annoyance :D

---

