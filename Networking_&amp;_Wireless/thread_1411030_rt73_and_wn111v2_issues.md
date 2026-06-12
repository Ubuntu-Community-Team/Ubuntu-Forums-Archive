---
title: "rt73 and wn111v2 issues"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by cfastner on 2010-02-19
I have two issues that I am working on.  The first:
I have Karmic Koala installed a Sylvania Meso G netbook.  The built-in wireless is identified as RT73USB.  It works to connect to my router but it seems to have a very limited range (when I take the netbook to the local coffee shop, it can't even SEE the wireless network).  Is there an updated RT73 driver that may increase the wireless range?  (How do I determine the version number of the driver in Karmic).  

Because of the first issue, I now pose the second:
I have purchased a WN111v2 801.2N usb wireless adapter (to see if I can get better range with IT).  I have read on the Ubuntu Forums that this wireless adapter is supported by Koala "out of the box".  I can't get it to be recognized at all.  Do I have to blacklist the internal RT73 adapter to get the WN111v2 USB adapter working?  What is the procedure to get this adapter working?

I would appreciate any assistance that you can provide with either/both issues!

Thanks,

Charlie
  ~~~

---

### Post by Triptol on 2010-03-22
What I noticed (and I don't know if that is your problem) is that udev changes the name of the new network card to wlan2 (or wlan3, whatever is new for your system).

Udev somehow "remembers" what cards you put in your system and keeps increasing the wlanX number.

Personally I couldn't get the card to connect with the "/etc/network/interfaces/"-method. I have no clue why it wouldn't. Since my machine is headless I also have problems with networkmanager (no nm-applet on a headless machine).

What works (kinda) is wicd. My only remaing problem is the speed of the device: 50K internet download max and don't you try to ssh into the box a second time 'cause then everything will fail.

---

