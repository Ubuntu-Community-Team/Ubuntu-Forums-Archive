---
title: "How do you make Elgato eyetv diversity work in 9.10?"
date: 2010-03-03
forum: Multimedia Software
---

### Post by jis on 2010-03-03
In Kaffeine I can not press "Start scan" button, because it is disabled. The USB-ID of the DVB-T dual-tuner device is 0fd9:0011.

---

### Post by jis on 2010-03-04
It is hard to buy hardware that works in Ubuntu. I had tested a tuner that has exactly same name in my computer and it worked. Still the one I bought has different USB-ID, and does not work.

I found some post about a patch for the hardware I own (dated Sun, 8 Feb 2009): this [http://mail.spinics.net/lists/linux-dvb/msg31652.html](http://mail.spinics.net/lists/linux-dvb/msg31652.html)

When/how is support added to Ubuntu?

---

### Post by BFG on 2010-03-05
I have the same need. :)

One of our machines is an Intel Mac Mini.  It has an Elgato EyeTV Diversity which works well in Mac OS.  It's a dual-boot with Ubuntu 9.10.

I can't get Ubuntu to recognise the device.  I've tried the following sources....

[http://www.linuxtv.org/](http://www.linuxtv.org/)
[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)

I had to make the change advise in other sources, opened the .config file,
changed, CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n


I confess I don't have the skills and I need a walk-through to get this working. :)


Somebody has managed it...
[http://www.digitv-forum.co.uk/viewtopic.php?t=6011&postdays=0&postorder=asc&start=45](http://www.digitv-forum.co.uk/viewtopic.php?t=6011&postdays=0&postorder=asc&start=45)
user "Goob", but they don't say how.

---

### Post by jis on 2010-03-06
Maybe Goob is using an older version (2007) of the tuner. I have tried the older one and it works fine in Ubuntu.

---

### Post by BFG on 2010-03-09
Thanks for that Jis.  I have a 2009 model. I know that there was a change and now you;ve told me it's the old one that works, well that helps.

 I've posted in the elgato forum asking if anyone knows what the chip details are on the new one but no luck yet,

---

### Post by smurfix on 2010-09-26
Support is in kernel 2.6.35, so should work with Maverick aka 10.10.

---

