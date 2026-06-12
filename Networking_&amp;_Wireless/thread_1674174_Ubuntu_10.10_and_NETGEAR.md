---
title: "Ubuntu 10.10 and NETGEAR"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by Venomtek on 2011-01-23
Ok I am completely new to this site as well as Ubuntu. I have been using Windows for many many years and now decided to try this. I have the 64bit version of Ubuntu 10.10. Everything so far looks nice and seems better running then the windows OS that I have dual loaded on my harddrive. My issue is that I am using a Netgear WN111v2 wireless device on my computer. Windows can use the device but Ubuntu 10.10 won't. I have looked across the forms and everything doesn't really make since to me so if anyone can have the kindness and patience to help a newbie out that would be amazing. Once I am able to connect to the internet through Ubuntu I am fully planning to delete Windows from my system.

I am not sure if it'll help but here is my system info....

Motherboard: G31TM-P21 (MS-7529)
Graphics:    ATI Radeon HD 4600 Series (4670)
Processor:   Pentium Dual-Core E5200 @ 2.50GHz 2.50GHz
Wireless:    NETGEAR WN111v2 RangeMax
Chipset:     Intel G31

---

### Post by Tedd81 on 2011-01-23
Hello!

Try the Ubuntu hardware support:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB")

Your adaptor is listed there. Follow the link and instructions.

Wireless can be a pain in the backside but this should get you started.

Good luck

Ted

---

### Post by Venomtek on 2011-01-23
I have tried this and nothing works so far. I had to fix my post as the model number of the mother board was off by one number, and I also added my chip set number. I just got off the phone with NETGEAR which got me no where as the man wanted me to buy and extended warranty plan for the adapter. Any other assistance would be appreciated as I really would like to get this solved...

---

### Post by Tedd81 on 2011-01-24
Hi,

Please give more detail:

[http://ubuntuforums.org/showthread.php?p=6183681]("http://ubuntuforums.org/showthread.php?p=6183681")

Post you outputs for the commands listed in the above thread.

Ted.

---

### Post by Venomtek on 2011-01-27
My chipset is different then any of the ones listed....
When I went to the site that you supplied, it had the device.. but for the Atheros ar9170 chipset. My chipset is the Intel G31 chipset. not to mention I don't know where to find the NDSWrapper or whatever it's called inside the Ubuntu 10.10. But I am still determined and I would like continued help to get me through this situation. I like the OS just need some help getting it running to it's full potential.

---

### Post by kwacka on 2011-01-27
You seem to be confusing the motherboard chipset with the wifi chipset.

What is the output of the command ```
lsusb
```

---

