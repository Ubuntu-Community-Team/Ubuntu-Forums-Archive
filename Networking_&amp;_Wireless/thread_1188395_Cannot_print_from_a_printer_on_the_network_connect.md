---
title: "Cannot print from a printer on the network connected to a Host through LPT1"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by Sora1421 on 2009-06-15
I am trying to connect 2 ubuntu machines (one 8.04 and one 9.04) to a Dell printer that is hooked up directly to a Windows XP machine through the LPT1 socket. I enabled sharing of the printer and it's called "Dell-Printer" the host's name is "A7300" 

I tried **lpd://A7300/Dell-Printer** as the device URI but no dice. What am I doing wrong here? I have the correct ppd file straight off the cd

---

### Post by scrooge_74 on 2009-06-15
Is that Dell Printer model supported under linux?

There are tutorials to get it working under CUPS and under SAMBA, if I find them I 'll post them

[http://www.linuxforums.org/forum/peripherals-hardware/52537-cups-hp-5740-xp-ubuntu-printing-comes-out-reversed.html]("http://www.linuxforums.org/forum/peripherals-hardware/52537-cups-hp-5740-xp-ubuntu-printing-comes-out-reversed.html")

---

### Post by Sora1421 on 2009-06-16
I'm sure it is. it is a brand new Dell 5110cn. it's an expensive printer. I'm going to unplug it from an LPT1 and directly connect it using an ethernet cable. I have to make it work for linux and windows, even though I would love to make it work for MAC as well. We have all three in our office.

---

### Post by scrooge_74 on 2009-06-16
The fact that is expensive is not assurance it will work on linux. From what I just read there should be drivers in a CD that comes with it, but the drivers are for Red Hat (but that could have change since this info came out)

[http://www.linuxminthcl.org/browse/product+dell_5110cn?id=497]("http://www.linuxminthcl.org/browse/product+dell_5110cn?id=497")

---

