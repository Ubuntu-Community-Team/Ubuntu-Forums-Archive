---
title: "PVR-150 remote and sensor without PVR-150"
date: 2008-02-14
forum: Mythbuntu
---

### Post by andrewb78 on 2008-02-14
I am working on a cheaper frontend-only box.  When I buy the parts for this, I also intend to buy an extra PVR-150 for the backend.  For about $10 extra, I can get the version of the PVR-150 with the remote and remote sensor.  Is there any way to hook up this remote sensor to the frontend box without having the PVR-150 actually in the frontend box and have it work with lirc?  The backend, which is also a frontend, already has a PVR-350 with working remote, so it won't need the PVR-150's remote or sensor.

---

### Post by ian dobson on 2008-02-15
Hi,

The PVR 150 IR sensor uses a special connector that only works for that card.

I was in almost the same situation as you (PVR-150 in backend on PC-1, seperate frontend) so I purchased a "homebrew" IR receiver on ebay for about 15Euro. You can pick them up more cheaply, but this one also supports switching on/off the frontend using the remote.

I just consists of a small PCB with a microprocessor that watchs the IR signal and if the programmed button is pressed it switchs on/off a relay that is connected to the power switch on the motherboard.


It took me abit of screwing about as the reciever runs from a serial port which you need to manually exclude from kernel use with the setserial command.


Regards
Ian Dobson

---

### Post by andrewb78 on 2008-02-15
Thanks.  I would guess that the remote would work even with another IR sensor, though?  That might make it worth getting the PVR-150 with the remote anyway, since the person who it's for is used to the PVR-350 remote.

---

### Post by newlinux on 2008-02-15
> **andrewb78 said:**
> Thanks.  I would guess that the remote would work even with another IR sensor, though?  That might make it worth getting the PVR-150 with the remote anyway, since the person who it's for is used to the PVR-350 remote.

Yep, it would work with another IR sensor.

---

### Post by ian dobson on 2008-02-15
Hi,

Yes it would work with any IR sensor that accepts a RC5 signal.

Regards
Ian Dobson

---

