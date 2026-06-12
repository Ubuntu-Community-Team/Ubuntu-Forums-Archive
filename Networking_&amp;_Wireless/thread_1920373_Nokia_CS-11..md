---
title: "Nokia CS-11."
date: 2012-02-04
forum: Networking &amp; Wireless
---

### Post by e-San on 2012-02-04
Hi!

I am trying to solve some simple problem.
I am on xubuntu 11.10 and have mobile internet.
I use Nokia CS-11 model which is multi-device usb. 
At first it is recognised as CD-ROM, but, after doing 'eject' it changes it's ID (via lsusb) and starts to act as mobile modem.

Any time i connect it i have to open terminal and hit 'eject'.

So, i want to add this to udev, to make it done automagicli.

I tried like that:
```
san@eeepc:~$ cat /lib/udev/rules.d/40-usb_modeswitch.rules 
# Nokia CS-11
#ATTRS{idVendor}=="0421", ATTRS{idProduct}=="061d", RUN+="sleep 3 && eject" 
SUBSYSTEM=="usb", SYSFS{idVendor}=="0421", SYSFS{idProduct}=="061d", RUN+="sleep 25 && eject"
#RUN+="/usr/sbin/usb_modeswitch -v 0x19d2 -p 0x2000 -M 5553424312345678000000000000061b000000020000000000000000000000 -R 1"

```

Yes, it is not modeswitch, but i do not see any reason to use it.
And, yes, it is far to much to sleep 25 s. But it is only for tests purposes.

Why it does not work?

Best regards,
San

---

