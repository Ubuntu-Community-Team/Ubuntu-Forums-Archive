---
title: "Mobile Broadband E220 suddenly stopped working in Ubuntu"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by xylith on 2009-05-26
Hi. I have been using Ubuntu since Gutsy Gibbon.

During Hardy i used wvdial for my E220 Mobile Broadband with Tele2 (sweden)

And since Intrepid i've happily used Network Manager for the same modem, same provider..

However. Since two days ago my Jaunty Jackalope suddenly started refusing to connect. It's there in the NM list of devices, i click it, one green light, two green light and then the message You have been disconnected.

So i guessed something went wrong in my system and did a clean reinstall of Jaunty Jackalope. No improvement what so ever.

However, the modem works very well when i dual-boot to Windows XP, so it's not a hardware error (but i do feel very trapped in this Windows environment).

I appreciate any help you can give me as how to analyze this problem. Where do I start? What logs could be of any help?

Thanks!

---

### Post by xylith on 2009-05-27
I finally got around to install wvdial (by running around with flash drive).

It seems for some reason both Network Manager and wvdial provoces the modem to hang up, but i have no idea why.

I'm in desperate need of help. Please?

Using the following wvdial.conf:
```
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0&C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = USB Modem
Phone = *99#
Username = ''
Password = ''
Carrier Check = no
Stupid Mode = yes
```

I get this output from wvdial:
```
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0&C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0&C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed May 27 21:37:00 2009
--> Pid of pppd: 3552
--> Using interface ppp0
--> pppd:  ï¿½h[08](ï¿½h[08]
--> pppd:  ï¿½h[08](ï¿½h[08]
--> pppd:  ï¿½h[08](ï¿½h[08]
--> pppd:  ï¿½h[08](ï¿½h[08]
--> pppd:  ï¿½h[08](ï¿½h[08]
--> pppd:  ï¿½h[08](ï¿½h[08]
--> Disconnecting at Wed May 27 21:37:02 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
```

A check in /var/log/messages:
```
May 27 21:37:07 mikael pppd[3561]: pppd 2.4.5 started by root, uid 0
May 27 21:37:07 mikael pppd[3561]: Using interface ppp0
May 27 21:37:07 mikael pppd[3561]: Connect: ppp0 <--> /dev/ttyUSB0
May 27 21:37:07 mikael pppd[3561]: CHAP authentication succeeded
May 27 21:37:07 mikael pppd[3561]: CHAP authentication succeeded
May 27 21:37:09 mikael pppd[3561]: Modem hangup
May 27 21:37:09 mikael pppd[3561]: Connection terminated.
May 27 21:37:09 mikael pppd[3561]: Exit.
```

---

### Post by xylith on 2009-05-31
Bump.

No one?

---

### Post by GeorgeVita on 2009-06-02
Hi **xylith**,
possibly you need to set the APN for your provider:

**Init3 = AT+CGDCONT=1,"IP","internet.tele2.se"**

Regards,
George

---

### Post by sickofthesea on 2009-06-21
I have a E160G running jaunty and after an update my internet just stopped working. However, mine connects, it shows that it is connected in network manager and the lights on the modem show that it is connected but I can't get any web pages or e-mail at all.

The update included a kernel update and I've tried going back to the previous kernel and it's still the same. So I'm assuming it is not a kernel issue but something else. I am writing this only by installing Windows on a spare bit of drive and connecting. The modem works perfectly under Windows.

I am away from home at the moment, but 5 days ago just before I left, my other laptop lost internet connection showing these same symptoms, also running jaunty, also after an update but that was a wireless connection to my router, not a mobile broadband stick.

So I am completely lost on this one. It's a real pain. Something has a bug in it somewhere and I haven't a clue where to begin to look.

Martin

---

### Post by sickofthesea on 2009-07-08
It was just too much of a show stopper. I've re-installed, see if it happens again!

---

### Post by jamb on 2009-07-26
Hi,
This is the way I did it on my ASUS Eee PC 1000HE netbook (xubuntu 9.04). You *should* be able to use NM, 
but as an alternative you can use **umtsmon** which requires very little tweaking and is less confusing than NM...

Download latest *umtsmon* (*.deb) version from:
[http://people.debian.org/~winnie/umtsmon/]("http://people.debian.org/~winnie/umtsmon/")

To install, run in a terminal:
```
$> sudo dpkg -i umtsmon_0.9-1_i386.deb
```

These WAN dongles must be switched from the initial flash storage mode to an USB modem. This is in the *udev-extras* package:
```
$> sudo apt-get install udev-extras
```


When you run the umtsmon from the menu, you have to fill in the Access point name (APN) for your ISP. 
If not known, download the *mobile-broadband-provider-info* database.
```
$> sudo apt-get install mobile-broadband-provider-info
```

Open the file */usr/share/mobile-broadband-provider-info/serviceproviders.xml* and look up your country, ISP and the APN.

When I boot with the E220 attached to the computer the green blinking (searching for network) occurs, but sometimes it does not blink. Without the initial green blinking I never gets a connection. However, once logged in, and hot-plugged, it always work.

Before launching umtsmon, check that the system recognize the modem:
```
$> lsusb
Bus 002 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd.
E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
``` 
and the mode switching does work (gives you two USB devices):
```
$> ls -l /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 2009-07-23 15:11 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2009-07-23 15:11 /dev/ttyUSB1
```

Make sure that your user account includes the *dialout* group:
```
$> groups
jamb adm lp dialout cdrom dip plugdev lpadmin admin sambashare
```

If you change the groups, remember to logout and login again.
Ok, it's time to connect, and usually your ISP only requires the correct APN.
If this does not work, ask your ISP if a password is required.

Good luck!

---

