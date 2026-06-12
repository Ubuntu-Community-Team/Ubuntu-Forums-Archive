---
title: "Wake on Wireless LAN (WoWLAN) Assistance."
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by bradyr on 2012-05-11
Hello, I am trying to get WoWLAN working on my ubuntu 12.04 laptop.

My goal is to be able to send a magic packet to my wireless mac address, from my ubuntu server and wake up my laptop from suspend/sleep mode.

I know for a fact that my laptop supports WoWLAN and is configured (in bios) to allow it.  My reasoning for this statement is that I dual boot Windows 7 and if I sleep the laptop in windows 7, I can send a magic packet to my wireless mac address and it will wake the system.   So, there is no reason to divert this discussion into theory as to whether or not my specific hardware or wireless card supports wake-on-wireless lan.

Here are the specs:

Laptop is a dell latitude e6520 with a Intel centrino advanced-n + wimax 6250 card.

I am dual booting 12.04 (gnome shell is my primary environment, otherwise it's stock.  using networkmanager, etc).   

Currently, if i suspend/sleep the laptop (while in ubuntu), if i send a magic packet to the wifi mac address it ignores it,  if i send a magic packet to the ethernet mac address it will wake the system.   

It is my understanding that the current kernel (I'm running 3.3.5) has support for wowlan for quite some time, and i further read somewhere that the intel wifi driver should also support wowlan.  

any advice or help that could be given would be greatly appreciated.

-Ryan

---

### Post by lores on 2012-10-10
This would be of interest to me, too. Until now, all I've found is [http://wireless.kernel.org/en/users/Documentation/WoWLAN](http://wireless.kernel.org/en/users/Documentation/WoWLAN) , which is rather laconical regarding the actual config ("Use iw to configure WoWLAN before going to sleep"). So, has anyone had some experience with WoWLAN?

EDIT:
```
iw phy phy0 wowlan enable any
``` is supposed to do the trick, but I keep getting ```
command failed: Operation not supported (-95)
``` with ```
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)

```
The same for ```
iw phy phy0 wowlan show
```

---

