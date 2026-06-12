---
title: "Can't detect TinyTwin"
date: 2009-11-10
forum: Mythbuntu
---

### Post by adrian11 on 2009-11-10
Hi all,

I've just installed 9.10 but can't get it to detect my DigitalNow TinyTwin tuner.

This page
[http://www.mythtv.org/wiki/DigitalNow_Tiny_Twin_Dual_Tuner](http://www.mythtv.org/wiki/DigitalNow_Tiny_Twin_Dual_Tuner)
claims it "works out the box".. I was hoping it would - I'm a linux novice.

I've tried the tuner on another (windows) box and it works fine there, so the tuner is good.
I've tried the USB ports with a USB stick which got detected fine so I think the USB port is good

dmesg tells me (after I unplug and plug back in):

[ 2129.441534] usb 1-5: USB disconnect, address 6
[ 2133.024043] usb 1-5: new high speed USB device using ehci_hcd and address 7
[ 2133.159733] usb 1-5: configuration #1 chosen from 1 choice

What should I try next ? any suggestions ?

Cheers
Adrian

---

### Post by adrian11 on 2009-11-10
1 thing I forgot to mention in first post.. I'm trying all this on a laptop.. Is that known to be an issue ?

---

### Post by Neon Dusk on 2009-11-12
With the tuner plugged in when the laptop starts what does 
```

dmesg | grep -i dvb

```

return ?

---

### Post by adrian11 on 2009-11-14
Hi, I did sort this out in the end, if anyone else is having the propblem see this forum post for the solution.

[http://forums.whirlpool.net.au/forum-replies.cfm?t=1319886](http://forums.whirlpool.net.au/forum-replies.cfm?t=1319886)

The problem was the TinyTwin reports a different ProductID, so you need to recompile the v4l drivers after editing the dvb-usb-ids.h

---

