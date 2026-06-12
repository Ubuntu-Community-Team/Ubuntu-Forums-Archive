---
title: "Cannot open Gnome-ppp"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by etienne@Rofti on 2009-07-06
Hi!

I am attempting to set up an internet connection using my mobile phone via Bluetooth. I have seen it done before, so it shouldn't be too difficult. I am attempting to use the tutorial outlined at [http://wiki.glug.org.za/index.php/Networking/Internet/Bluetooth_Dialup](http://wiki.glug.org.za/index.php/Networking/Internet/Bluetooth_Dialup)

However, when I attempt to run Gnome-ppp, I get the following message:

```
$ gnome-ppp
WVCONF: /home/etienne/.wvdial.conf
Segmentation fault

```

And when I attempt to run wvdial, the following happens:

```
$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

```

I do not have a modem attached, nor an inbuilt one. I want to setup Gnome-ppp to use my mobile phone via bluetooth rather than a modem. I know it is possible, but I am struggling.

Thanks in advance for any help...

---

### Post by GeorgeVita on 2009-07-07
Hi **etienne@Rofti**, according to the link you supplied in your post, you must gain a bluetooth connection with your phone as device: **/dev/rfcomm0** By default **wvdial** uses /dev/modem which can be changed (and all other connection parameters) with:
**sudo gedit /etc/wvdial.conf**
In this parameter file you must edit all data to appropriate with your hardware and your provider's data connection. A typical /etc/wvdial.conf could be:
[B][Dialer Defaults]
Modem = /dev/rfcomm0
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = user
Password = pass
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = AT+CGDCONT=1,"IP","internet"
Phone = *99***1#
Stupid Mode = 1[/B]

If your phone has various setup profiles, set it to modem.

Connect using **sudo wvdial** from a terminal window. Most times the system cannot co-operate with wvdial and seems to be offline, so untick "work offline" from firefox (ALT-F W).

I cannot help you with the "Segmentation fault" error of gnome-ppp.

Post any new message to follow up.

[COLOR="Blue"]EDIT: see also [http://ubuntuforums.org/showthread.php?t=1204288](http://ubuntuforums.org/showthread.php?t=1204288)[/COLOR]

Regards,
George

---

