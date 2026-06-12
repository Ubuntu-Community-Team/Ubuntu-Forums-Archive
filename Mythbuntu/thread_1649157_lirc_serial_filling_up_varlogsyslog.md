---
title: "lirc_serial filling up /var/log/syslog"
date: 2010-12-19
forum: Mythbuntu
---

### Post by bogustrumper on 2010-12-19
I'm struggling to get a serial irblaster working in Mythbuntu 10.04.  I'm not sure where I'm going wrong.  Since I'm using a Comcast DTA, and the mythbuntu setup GUI doesn't  have the right entries, I tried to do this manually.  I had this hardware working before on a Mythdora install.  Figured it was worth an update, though, since I've moved and gotten a new TV etc etc.  So... now my current headache.

I've verified that the hardware works by using my cellphone camera to verify that the LED lights up when I run:

echo 12345678901234567890 > /dev/ttyS0

So it seems to me that there's no hardware problem, and things are physically hooked up properly.

The trasmitter is set up in /etc/lirc/hardware.conf as follows:

TRANSMITTER="Serial"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="/etc/lirc/lircd.conf"
TRANSMITTER_LIRCD_ARGS=""

I have no /etc/modprobe.d/lirc-serial or anything lirc related in /etc/modprobe.d

If I boot, I see lirc-serial in lsmod, so it seems to be loading.  But, when I look in /var/log/syslog, I see, over and over again, these two lines:

Dec 19 20:19:43 lircd-0.8.6[940]: accepted new client on /var/run/lirc/lircd1
Dec 19 20:19:43 lircd-0.8.6[940]: removed client

Thus, my syslog file is gigabytes long.

I'm fresh out of ideas, and I'm not sure what to try.  Any tips?

---

### Post by thatguruguy on 2010-12-19
[http://ubuntuforums.org/showthread.php?t=1609804&highlight=lirc+serial+maverick](http://ubuntuforums.org/showthread.php?t=1609804&highlight=lirc+serial+maverick)

---

### Post by bogustrumper on 2010-12-19
Hi thatguruguy,

Thanks for the note.  In my attempt at scouring Google for an answer, I had already come across that forum link.  Unfortunately it doesn't look like it has anything for me.  Seems that for the post in the link the necessary change was:

LIRC_LOAD_MODULES="true"

...which I already have enabled in my hardware.conf.  Any other thoughts?

I did some digging, though, and figured out that if I remove my remote from hardware.conf (which uses the same config file, btw), then I don't get the log messages... but, then I can't use irsend.  So, still stuck.

---

