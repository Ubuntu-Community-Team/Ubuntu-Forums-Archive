---
title: "Lirc with  Mobile Action Technology MA620 Infrared"
date: 2010-04-10
forum: Multimedia Software
---

### Post by imblack on 2010-04-10
I have this USB IrDa
 Mobile Action Technology, Inc. MA-620 Infrared Adapter

Can any one help me using LIRC with this? probably some one that has done it before for un-detected devices?

My device works good, gets attached to ttyUSB0, but how to configure it with LIRC?

thanks, please help

---

### Post by WinterRain on 2010-04-10
See [this]("http://www.lirc.org/html/configure.html").

---

### Post by imblack on 2010-04-10
I went there, first of all my Remote is real generic but before that. Lirc cant get my above said IR adapter right.

I used this tool gnome-lirc-properties to configure that my IR reciever is generic and is at /dev/ttyUSB0 and then close it but then LIRC says the config is incorrect.

"irrecord: file "lircd.conf" does not contain valid data"

Maybe gnome's aint updated.

But if i do 'cat /dev/ttyUSB0' and then press keys on my remote my Reciever shows junk characters, on analysing them through hex editor I only see combination of two things.

E0 and 00, I think its pulse modulation. but that means my IR adapter is okay, how to show this to LIRC so that it lets me use irrecord?

btw i get no /dev/lircd0 etc to use with irrecord

and irrecord fails on /dev/ttyUSB0:

Please help!

---

### Post by int2ag0n on 2010-08-01
I have the same ir dongle ma620 i cat the /dev/ttyUSB0 and as long as i hold down a button in my remote controls the right led flashes. However nothing is visible in the shell from the cat command. Any idea how you achieved this?

---

### Post by imblack on 2010-08-02
I just used dmesg to see what ttyUSB device my irda got attached to and then simply cat that device.

---

