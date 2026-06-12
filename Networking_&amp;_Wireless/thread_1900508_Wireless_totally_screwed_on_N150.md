---
title: "Wireless totally screwed on N150"
date: 2011-12-26
forum: Networking &amp; Wireless
---

### Post by Cadmus on 2011-12-26
Evening,

I'm using Ubuntu Netbook 10.04 on a Samsung N150, it's got the usual Realtek wireless interface in it.

```
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 rev 01)
```

A couple of days before Christmas I did a full update so it was good to use when travelling, I have two non-standard repositories, voria and mame.

All seemed well until I tried to connect to any wireless access point. It seemed that any attempt to turn the wireless on or off produced a total system freeze. The only thing that changed was the kernel version, and I checked I had the right version of samsung-wireless installed as part of the update.

So I tried removing network-manager and replacing it with wicd, which worked after a sort, if I started the machine on a wired connection it would be ok if I unplugged it.

So I tried the following in no particular order

[LIST]
[*]Dirk Hoeschen's Realtek Driver Script
[*]installing ndiswrapper and using the XP x86 drivers
[*]blacklisting the current drivers
[*]manually modprobing the drivers
[*]removing wicd and putting network manager back on
[*]removing, adding, removing, and adding the samsung-wireless packages from voria (checked the kernel matched)
[/LIST]

And the best I've gotten out of any of this was the odd freeze and constant requests to confirm the correct wireless key (checked correct using phone)

So I reckon I've made a a total mess of this machine now. Before I wipe it and try again/go back to Windows is there anything people can think of I may not have tried?

---

### Post by TimGS on 2011-12-26
It might be the same problem as I have had. See [http://ubuntuforums.org/showthread.php?t=1900532](http://ubuntuforums.org/showthread.php?t=1900532)

-- Tim.

---

### Post by Cadmus on 2011-12-26
Duly noted and I'll keep an eye on your thread, currently backing up home dir as I think my efforts to 'fix' this have caused some serious harm to the machine, so a wipe seems the right move.

But as long as it's not me once I'm back to a standard install I'll know to wait and see what happens.

---

### Post by Cadmus on 2011-12-26
I've booted the 35 kernel as that's the last version which had a specific release of samsung-wireless. If I manually modprobe r8192_pci then I get networking back and that will do until I get back to my own flat.

The rest will need sorting out at some point, but I have pidgin and OpenTTD running and that should see me through the festive season.

---

