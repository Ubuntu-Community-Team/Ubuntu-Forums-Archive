---
title: "SY-VIA-GA (SYBA) 10/100/1000Mbps NIC"
date: 2006-04-15
forum: Networking &amp; Wireless
---

### Post by SadaraX on 2006-04-15
I bought a SY-VIA-GA (SYBA) 10/100/1000Mbps NIC card from newegg:
[http://www.newegg.com/Product/Product.asp?Item=N82E16833328002](http://www.newegg.com/Product/Product.asp?Item=N82E16833328002)

Now there are various claims about this card working with linux (which is why I bought it), most specifically it says "Red Hat Linux 7.3(kernel 2.4.18-3) or later", now I'm running Ubuntu (and a debian system as well) with kernel the Ubuntu kernel 2.6.12 and debian kernel 2.6.15. Neither of them can use this card

I have tried manually adding entries to my /etc/network/interface file but it does not good. Basically I am wondering if anyone has ever got a card like this to work under linux as it claims and how they did it. Thanks

---

### Post by Stormbringer on 2006-04-16
Are there any changes that the chip on the card is either a VIA VT6120 or VT6122 Gigabit Ethernet NIC? The image at Newegg clearly shows the VIA Logo on the chip, but the type isn't readable at all.

If that's the case, then you may need to download the driver and compile the module yourself.

Find the VIA Velocity Liunux driver [here]("http://www.viaarena.com/default.aspx?PageID=420&OSID=20&CatID=2440&SubCatID=130").

Let's hope there are some instructions included ...

Cheers,
Storm.

---

### Post by SadaraX on 2006-05-17
[QUOTE=Stormbringer]Are there any changes that the chip on the card is either a VIA VT6120 or VT6122 Gigabit Ethernet NIC? The image at Newegg clearly shows the VIA Logo on the chip, but the type isn't readable at all.

If that's the case, then you may need to download the driver and compile the module yourself.

Find the VIA Velocity Liunux driver [here]("http://www.viaarena.com/default.aspx?PageID=420&OSID=20&CatID=2440&SubCatID=130").

Let's hope there are some instructions included ...

Cheers,
Storm.[/QUOTE]

Wow, I did not notice someone had replied to this post. Well, the case is chip on the card is a VT6122... Now I have the card in a system, and while Linux (in this its a Debian System) sees the card is present, it cannot use it correctly at all. Its powered up (orange and green lights on in the back), so that's good, but nothing else.

---

### Post by SadaraX on 2006-05-27
Well I downloaded the drivers for the vt6122 chip ( [http://downloads.viaarena.com/drivers/LAN/velocityget.tgz](http://downloads.viaarena.com/drivers/LAN/velocityget.tgz) ) for the generic linux system and tried to compile it. On two systems (one debian and one ubuntu) I had the same problem. I extracted the tgz file's contents to a directly and ran the 'make' command. Here's the output

> 
make -C /lib/modules/2.6.15-chw-2/build SUBDIRS=/root/velocityget modules
make[1]: Entering directory `/usr/src/kernel-source-2.6.15-chw-2'
  CC [M]  /root/velocityget/velocity_main.o
/root/velocityget/velocity_main.c:1760: warning: initialization from incompatible pointer type
/root/velocityget/velocity_main.c: In function `velocity_ethtool_ioctl':
/root/velocityget/velocity_main.c:2223: error: structure has no member named `slot_name'
/root/velocityget/velocity_main.c: In function `velocity_suspend':
/root/velocityget/velocity_main.c:2394: error: too many arguments to function `pci_save_state'
/root/velocityget/velocity_main.c: In function `velocity_resume':
/root/velocityget/velocity_main.c:2430: error: too many arguments to function `pci_restore_state'
make[2]: *** [/root/velocityget/velocity_main.o] Error 1
make[1]: *** [_module_/root/velocityget] Error 2
make[1]: Leaving directory `/usr/src/kernel-source-2.6.15-chw-2'
make: *** [default] Error 2


Any idea what to do?

---

