---
title: "Can someone walk me through wvdial?"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by xxzachrmxx on 2008-12-23
I am extremely new at Ubuntu and need a little help. I'm attempting to set up a connection with my Cricket Wireless Broadband card, which I know is possible.

I  have this information:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/modem
ISDN = 0
Phone = #777
Password = noauth
Username = <your phone number here>

But unfortunately I don't know what to do with it. How do I go about setting up wvdial and where do I download anything I need to download? Thanks in advance.

---

### Post by ieee488 on 2008-12-23
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

---

### Post by ziesemer on 2008-12-23
First, your "Modem Type = Analog Modem" setting seems suspect.  I'm not sure what exactly should be used here, but I think may need to be something like "GPRS modem".

Second, are you sure your device is mounted as "/dev/modem" ?  It may instead be something like /dev/ttyUSB0 or /dev/ttyACM0, etc.

Third, do you need to be using wvdial directly?

I've recently gone through some of the same setup issues, which I've documented on my blog.  Maybe start with [http://blogger.ziesemer.com/2008/10/alltel-um175al-usb-evdo-ubuntu.html](http://blogger.ziesemer.com/2008/10/alltel-um175al-usb-evdo-ubuntu.html) , and also page through the previous and next few posts as needed.  Hopefully something there gets you a bit closer to your goal!

---

