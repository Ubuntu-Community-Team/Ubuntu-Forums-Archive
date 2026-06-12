---
title: "Equivalent of /etc/conf.d/net file ?"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by dany74q on 2011-04-19
Hello there ,

I just moved from gentoo to ubuntu ,and one thing that I really miss is the gentoo 'DIY' ideology .
I`d like to configure my wireless network alone , though I am missing the /etc/conf.d/ dir .

Where can I find the 'net' file ?

Thanks ,

Danny .

---

### Post by chili555 on 2011-04-19
How can I fit BMW pistons to my Mercedes? You can't.

Gentoo and Debian (Ubuntu is a variant of Debian) are so completely different that it's fruitless to compare them.

By default, Ubuntu uses the automagic, one-size-fits-all Network Manager. It takes over all networking. Configuration using manual methods is very difficult to impossible with it installed and running. If you want to configure networking manually, remove NM:```
sudo apt-get remove --purge network-manag*
```Then populate /etc/network/interfaces:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```Also, /etc/resolv.conf:```
nameserver 192.168.1.1
```Restart networking:```
sudo /etc/init.d/networking restart
```Enjoy! Post back if I can help you further.

---

### Post by dany74q on 2011-04-19
Thanks , following by your steps I`ve configured it successfully.
Must say though , ubuntu brings much more 'out of the box' , after I`ve been using gentoo for a while it feels quite peculiar,
not sure I like it yet .

Thanks again ,

Danny.

---

### Post by Iowan on 2011-04-19
> **dany74q said:**
> ...not sure I like it yet . Guess that's why there are Fords, Chevys, BMWs, and Mercedes (to name only a few) - choose the one you like for the features it offers. :)

---

