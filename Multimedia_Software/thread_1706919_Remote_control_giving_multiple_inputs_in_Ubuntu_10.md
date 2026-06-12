---
title: "Remote control giving multiple inputs in Ubuntu 10.10"
date: 2011-03-14
forum: Multimedia Software
---

### Post by Another Monkey on 2011-03-14
I will admit to doing a lot of fiddling to get "lirc" to work (and accidentally following old guides - oops), so there is a good chance I have messed something up!

I am using an old Windows XP MediaCenter 2005 remote and receiver.  It wasn't working ("irw" would show "^[[A" rather than "up") but after seeing [this post]("http://ubuntuforums.org/showpost.php?p=9984844&postcount=4") and following the steps for A1 & A2 (blacklisting "lirc_mceusb") I now get sensible output from "irw".  But I get it multiple times.

I really think I might be making matters worse, so is there some kind of "clean up" or other action I should follow to make "lirc" behave correctly?

This was a fresh install of Ubuntu 10.10 before I started messing.

Kernel: 2.6.35-27-generic (64-bit)

ls -l /dev/lir*
```
lrwxrwxrwx 1 root root 19 2011-03-14 19:05 /dev/lircd -> /var/run/lirc/lircd
```

lsusb:
```
Bus 006 Device 005: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
```

lshal:
```
usb_device.product = 'eHome Infrared Receiver'  (string)
```

lsinput:
```
/dev/input/event2
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "Media Center Ed. eHome Infrared "
   phys    : "usb-0000:00:1d.1-2/input0"
   bits ev : EV_SYN EV_KEY EV_REP
```

lsmod | grep mce:
```
lirc_mceusb            14580  0 
lirc_dev               12140  1 lirc_mceusb
mceusb                 12846  0 
ir_core                16906  8 ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,mceusb
```
("lirc_mceusb" is now blacklisted an no longer showing)

"hardware.conf" and "lirc.conf" are default from the "lirc" install for the Windows remote.

---

