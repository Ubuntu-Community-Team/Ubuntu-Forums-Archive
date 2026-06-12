---
title: "irrecord MCE reciever"
date: 2008-07-07
forum: Mythbuntu
---

### Post by pmbsa on 2008-07-07
Hi, I am trying to get irrecord to work so I can get the correctIR codes for my remote but I canseem to get it working and I cant find much help on it.

I run the following
irrecord -d /dev/ttyUSB0 /tmp/lircd.conf
and i get the following output (lirc is not running)


irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get hardware features
irrecord: this device driver does not support the new LIRC interface
irrecord: major number of /dev/ttyUSB0 is 188
irrecord: LIRC major number is 61
irrecord: check if /dev/ttyUSB0 is a LIRC device
irrecord: could not init hardware (lircd running ? --> close it, check permissions)


any assistance would be much appreciated

thanks
Paul

---

