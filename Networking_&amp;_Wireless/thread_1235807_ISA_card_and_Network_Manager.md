---
title: "ISA card and Network Manager"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by ola on 2009-08-09
Hi, I just installed Xubuntu 9.04 on an old P3 computer with an ISA network card (Intel EtherExpress).

I added the module (*eepro io=0x210 irq=5*) for the card to */etc/modules* and rebooted

If I open *Edit Connections...* in Network manager I can see the card (see screenshot 1) but when I try to connect with it I can't (see screenshot 2).

If I manually do *sudo dhclient eth0* the card works (I write this from the computer).

Ideas for how I can get it to work?

If there isn't any good solution what's the best way to remove network manager? If I'm not mistaken Firefox uses some offline mode that's triggered via Network Manager?

---

### Post by ola on 2009-08-10
I just removed network manager with: *sudo apt-get remove network-manager*

Then I added the card to to */etc/network/interfaces*:
```
$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

It seems to work.

---

### Post by Iowan on 2009-08-10
*Might* have worked by adding the card to */etc/network/interfaces* without removing NM, but...

---

### Post by ola on 2009-08-12
@Iowan: Thanks for replying. I tried that first but it seems like [Ubuntu has a special config for NM so it doesn't manage cards that are in */etc/network/interfaces*]("http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-45c7dcb29a13372e1da1221b5ed499d981ea7ec6").

---

### Post by Iowan on 2009-08-12
Your experience would override my suggestion... my interpretation is that if it's defined in */etc/network/interfaces*, NM doesn't mess with it. If it were defined there (with "auto"), it should work. 
But, I don't think I'd change things back to find out... :)

---

### Post by ola on 2009-08-13
@Iowan: I think you are correct. But...

If I had NM installed and eth0 in */etc/network/interfaces[/] the network worked fine (ping worked). The problem was that Firefox started in offline mode ([i]File / Work offline*) and I had to change that every time I started Firefox.

---

