---
title: "GPRS Internet via Samsung Phone"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by Sonofalynx on 2010-08-08
I have a Samsung phone (S3310) and I'm trying use it as a modem to access the net on 10.04. I set up a Mobile broadband connection (under network connections) and I'm pretty sure the settings are correct because it works on a Nokia phone with the same service provider.

When I plug in my Data Cable and set it to Samsung PC Studio mode,  my phone isn't detected as a modem. I just tried wvdialconf and it says "No modem detected". I'm guessing that maybe I'm missing some drivers here. Can someone tell me what I can do get the phone detected as a modem.

Thanks

---

### Post by pdc on 2010-08-08
with the phone plugged in, what does

> lsusb give in a terminal

and if you copy and paste this into a terminal

> dmesg | grep tty

and copy and paste back the results

---

### Post by Sonofalynx on 2010-08-08
lsusb - am assuming these are the lines you are looking for.
> 
Bus 002 Device 003: ID 04e8:6795 Samsung Electronics Co., Ltd 


dmesg|grep tty
> [    0.000000] console [tty0] enabled
[  673.314920] cdc_acm 2-2:1.0: ttyACM0: USB ACM device
[  673.365318] tty_port_close_start: tty->count = 1 port count = 0.


Thank you.

---

### Post by pdc on 2010-08-09
hmmmmmmmmm

> ttyACM0:

should mean: seen as modem .........

I have no further suggestions at this point

---

### Post by Sonofalynx on 2010-08-10
Is there anyway to force Ubuntu to connect to the phone, considering it is detected as a modem anyways. Mobile broadband always auto-connects.

---

### Post by itsme33 on 2010-09-06
> **Sonofalynx said:**
> lsusb - am assuming these are the lines you are looking for.


dmesg|grep tty


Thank you.

i am also using the s3310 and cannot connect to ubuntu :-) please help

---

