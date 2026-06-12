---
title: "which linux+broadcom=works out of box on laptop?"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by D1ZZ4ZZT3R on 2009-04-16
hi, incase the title isn't self-evident, i'm wondering what distributions of linux work with broadcom wireless out fo the box. i've got a laptop and i'm attempting to save myself from the process of getting it to work with ubuntu or, just buying a new wireless card. i've already got to buy two new fans and a hard drive for it.

any suggestions?

---

### Post by pytheas22 on 2009-04-16
I don't know of any distributions that work with Broadcom chips out-of-the-box.  The reason is that most Broadcom cards currently require proprietary firmware to work, and Broadcom has yet to grant third-parties the right to redistribute it, which presents some legal ambiguities.  None of the major Linux distributions are willing to risk a lawsuit.

However, getting a Broadcom device working in most cases is as simple as enabling the card in System>Administration>Hardware Drivers, or typing:
```

sudo apt-get install b43-fwcutter
```

which will manually install the firmware (the catch is that you need to have a pre-existing Internet connection to grab the firmware).

Also, a few of the newer Broadcom cards are supported by a driver that doesn't require firmware; see [Broadcom's site]("http://www.broadcom.com/support/802.11/linux_sta.php") for the list of specific models.  If you have one of these devices, it should completely work out-of-the-box.

Finally, I want to mention that the b43 developers (the people who write the open-source drivers for Broadcom chips) are close to creating stable free firmware, which Ubuntu will be able to distribute without having to worry about legal issues.  This means that in the near future, all Broadcom cards should be able to work out-of-the-box in Linux.

---

### Post by D1ZZ4ZZT3R on 2009-04-17
thanks. that's the kind of information i like. thorough, simple, and to the point. i'll try out that install; i'll just plug in the good ol' cable. i'll have to wait, though, as my cat's using it as a pillow at the moment.

---

### Post by D1ZZ4ZZT3R on 2009-04-18
didn't work. said package could not be found : \

---

### Post by StuartN on 2009-04-18
I had Ubuntu 8.04 and now 8.10 running with a Broadcom wl (i.e. Broadcom's own Linux) driver using BCM4311 802.11b/g WLAN on a Dell laptop. The wl driver is in the kernel.

---

### Post by pytheas22 on 2009-04-18
> didn't work. said package could not be found : \

Try running these commands--the first one will update your package list before trying to download the firmware, which may solve the problem:
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```

As long as you're using Ubuntu 8.04 or later and are connected to the Internet, that should work.  If not, please post the exact error message you get.  It would also be useful to see the output of:

```
lspci -nn | grep -i broadcom
lshw -C Network
```

---

