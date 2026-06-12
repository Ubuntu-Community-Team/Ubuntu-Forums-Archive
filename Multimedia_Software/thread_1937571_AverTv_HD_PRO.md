---
title: "AverTv HD PRO"
date: 2012-03-08
forum: Multimedia Software
---

### Post by Number6 on 2012-03-08
Hi there,

Well I'm in an obviously long line of people struggling to get USB TV tuners to work, in my case the AverTV HD PRO, I have downloaded, compiled and installed the driver as per an very clued up Italian(Gazzax or something) guys directions, so I've got the firmware in the /lib/firmware but I get the old dmesg:
:

[   17.805994] dvb_usb_af9035: disagrees about version of symbol dvb_usb_device_init
[   17.805996] dvb_usb_af9035: Unknown symbol dvb_usb_device_init (err -22)

 I have tried a make clean, and recompiling and reinstalling, then I got:

[   17.805986] dvb_usb_af9035: disagrees about version of symbol rc_keydown
[   17.805989] dvb_usb_af9035: Unknown symbol rc_keydown (err -22)
[   17.805994] dvb_usb_af9035: disagrees about version of symbol dvb_usb_device_init
[   17.805996] dvb_usb_af9035: Unknown symbol dvb_usb_device_init (err -22)

So that actually made it worse! Does anyone have any ideas? This device won't work in Windows due to what I suspect is flaw in the current NVidia drivers, to get it working in Linux instead would be a coup! :)

---

### Post by RGG on 2012-03-10
Hi Number6,

I've the same USB stick running in 11.10 following this steps:

```


sudo apt-get install linux-headers-`uname -r`

sudo apt-get install build-essential

wget http://xgazza.altervista.org/Linux/DVB/Drivers/AF9035_xgaz_3.0.0.tar.bz2

tar -xjf AF9035_xgaz_3.0.0.tar.bz2

cd AF9035_xgaz_3.0.0

make

sudo make install

cd /lib/firmware

sudo wget http://xgazza.altervista.org/Linux/DVB/dvb-usb-af9035-01.fw



```

from here:
[http://xgazza.altervista.org/Linux/DVB/af9035.html]("http://xgazza.altervista.org/Linux/DVB/af9035.html")

Even the remote works ;)

Hope it helps you

---

### Post by Number6 on 2012-03-12
Lucky you! :) Those are the exact same instructions I followed but I still get that error in the dmesg output, What did you use to actually watch TV through the device?

---

### Post by RGG on 2012-03-12
I use VLC but it works in MeTV and Mplayer too.
I saw similar messeges after a kernell update...
It solves reinstaling the driver

---

### Post by Number6 on 2012-03-12
Sadly reinstalling many times has had no effect for me, I cannot get VLC to open DVBT Capture Device. Noone else will help me so I guess I have to give up

---

### Post by bctechnzl on 2012-03-12
I watched as it make, then installed with no obvious errors
but checking dmesg later, I saw

```
dvb_usb_af9035: probe of 1-4:1.0 failed with error -5 
```

so things aren't going right for me either.
Is there anywhere we can discuss further with the developer?

---

