---
title: "IR Blaster Not Working"
date: 2008-11-17
forum: Mythbuntu
---

### Post by ed3120 on 2008-11-17
I'm using a PVR150 with a Motorola cable box.  I selected this option in MCC in 8.10 and it still isn't working.

Is there something else that I need to configure? Do I need a channel change script?

---

### Post by codymyth on 2008-11-19
yea mine doesn't work either, does yours flash at all?

---

### Post by ahood on 2008-11-20
Hello,

I had the same problem. Maybe the steps in the link below will help?

[http://ubuntuforums.org/showthread.php?p=5417214#post5417214i](http://ubuntuforums.org/showthread.php?p=5417214#post5417214i)

---

### Post by ed3120 on 2008-11-20
> **codymyth said:**
> yea mine doesn't work either, does yours flash at all?

No, it does not.

---

### Post by codymyth on 2008-11-20
yea thats the same issue i am having, sadly i no longer have anytime to try and fix it anymore. You think you could send me a pm if you ever get it figured out

---

### Post by Rompalle on 2008-11-21
> **ed3120 said:**
> I'm using a PVR150 with a Motorola cable box.  I selected this option in MCC in 8.10 and it still isn't working.

Is there something else that I need to configure? Do I need a channel change script?

you will need to be a bit more specific. How are you testing this?

have you tried with the irsend command ?

---

### Post by SoftwareMaven on 2008-11-25
So I'm seeing the same problems (seemingly, anyway :)).  Receiving works fine; sending does not.

So I started getting an error from irsend saying:

> irsend: command failed: SEND_ONCE dish 0
irsend: hardware does not support sending

I changed /etc/lirc/hardware.conf, changing the REMOTE_MODULES line to "lirc_dev lirc_pvr150" instead of "lirc_dev lirc_i2c".

With that change, I now get:

> irsend: command failed: SEND_ONCE dish 0
irsend: transmission failed

And dmesg shows:

> lirc_pvr150: failed to get data for code 0, key 525 -- check lircd.conf entries

According to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/275549"), it looks like that is a result of the driver trying to send the wrong codes.

Unfortunately, I can't figure out how to get the "right" codes sent.  I tried to use the lirc.conf from [blushingpenguin.com]("http://www.blushingpenguin.com/mark/blog/?p=24"), but that causes a segfault when starting the lirc daemon.

Thoughts?

Thanks.

tj

---

### Post by SoftwareMaven on 2008-11-25
So, using the configuration files in [this thread]("http://ubuntuforums.org/showthread.php?t=927974&highlight=pvr150"), I was able to send and receive.  Now I just need to get my codes being sent. :)

tj

---

