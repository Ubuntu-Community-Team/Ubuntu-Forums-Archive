---
title: "wireless ralink 2870, anygate xm200ua not scanning networks"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by suffice on 2010-08-22
Hello,

So I bought a Wireless N USB stick (anygate XM200UA) which i beleive to have a ralink 2870 chipset.

the device shows up in lsusb.  It shows up in lshw. It seems to show up in lsmod (not really familiar with lsmod, though know that it shows which modules/ drivers are in use by the kernel)

****
lsmod output
...	vboxnetflt             12242  0 
vboxdrv              1767671  2 vboxnetadp,vboxnetflt
rt2870sta             525366  0 
arc4                    1473  2 
snd_hda_codec_idt      61418  1 
rt2800usb              33496  0 
rt2x00usb              11260  1 rt2800usb
rt2x00lib              32133  2 rt2800usb,rt2x00usb
led_class               3732  1 rt2x00lib
tuner_simple           15041  2 
tuner_types            18305  1 tuner_simple
wm8775                  3725  2 
tda9887                10633  2 
tda8290                14720  0 
.....


lshw output
....
-network:0
       description: Wireless interface
       physical id: 5
       logical name: wlan0
       serial: 78:28:02:0d:2c:e1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

.....


now the problem is that it all seems to be there, but it cant scan networks it simply says in the menu 'disconected'

and

iwlist wlan0 scan says no resutls.....


any ideas where to go from here?

---

### Post by suffice on 2010-08-24
well after a few more days of searching i got it to work.

i needed to edit 

/etc/modprob.d/blacklist.conf

and add the line

blacklist rt2800usb 

to the file.

reboot and networks scanning and working!

---

