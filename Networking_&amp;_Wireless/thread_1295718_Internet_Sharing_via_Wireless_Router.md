---
title: "Internet Sharing via Wireless Router"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by Rubiktion on 2009-10-19
Hi all, iam new member here, and new on linux

i have 2 Desktop PC, 1 Notebook, WRT54gl wireless router..
just want to make all these connected and get internget connection

i try HOWTO like [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing") and [this]("https://help.ubuntu.com/community/Router") but no luck :(
my network maybe like this

<modem> ----via USB (eth1)--- <1st desktop PC> ----(eth0)---- <wrt54gl> --(cable)-- <2nd desktop>
                                                                                                            
and use wireless connection for my notebook
maybe i got some wrong with that, how you can help me..

thanks

and sorry for my bad english

---

### Post by madverb on 2009-10-19
Unless you are planning on using the PC as a proxy or the Modem is a 3G USB Modem that's a strange config.
You should just be able to connect the modem to the router and everything else connects to the router.

---

### Post by Rubiktion on 2009-10-19
unfortunately (my modem motorola sb5101) RJ45 slot is broken so i just can use my USB, and this router dont have usb slot..

thanks

---

### Post by Rubiktion on 2009-10-20
please i realy need help, is it i configure wrong?

---

### Post by kain1 on 2009-10-20
Cable in Indonesia ?

---

### Post by Rubiktion on 2009-10-20
yeah cable  on indonesia..

---

### Post by DGortze380 on 2009-10-21
I suggest you get a new modem then.

Otherwise you'll have to configure PC 1 to act as a router, or configure some sort of bridge connection between eth0 and the USB virtual socket...

Sounds like more trouble then it's worth to me.

---

