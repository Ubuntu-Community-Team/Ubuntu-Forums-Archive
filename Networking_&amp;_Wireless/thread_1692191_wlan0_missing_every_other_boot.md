---
title: "wlan0 missing every other boot"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by kakotako on 2011-02-21
I just installed Ubuntu 10.10 on a Sony VAIO VGN-NR110E.

Literally, every other time I boot the wlan0 interface is missing. I saw that there used to be some problems with network manager in the past. My NM is running fine. 

When this happens
```

sudo ifconfig wlan0 up
```

returns:

wlan0: ERROR while getting interface flags: No such device

If I reboot the wlan0 comes back up. Any tips are appreciated. This is my mom's computer, I can't deliver her faulty goods.

---

### Post by gigaferz on 2011-02-22
whoever is willing to help you will ask you for the outputs of 
dmesg 
lshw 
or 
lsusb or lspci

---

### Post by kakotako on 2011-02-24
Thanks.

I realized this is happening only after 

```
sudo reboot
```

but not if I shutdown and restart so it's managable.

---

### Post by cu3us on 2012-01-13
Hi.  I just installed Ubuntu 10.04 and the same thing is happening to  me.  When I 'sudo ifconfig eth0 up' I also get 'wlan0: ERROR while  getting interface flags: No such device'.

Also, 'iwconfig' returns no values for wlan0.

This is really more of an inconvenience than anything, but I would like to have this resolved.  Does anybody have advice?

---

