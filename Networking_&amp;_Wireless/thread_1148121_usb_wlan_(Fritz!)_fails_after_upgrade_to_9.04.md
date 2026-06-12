---
title: "usb wlan (Fritz!) fails after upgrade to 9.04"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by pompompompom on 2009-05-04
well... I have been reading a lot about wireless failures after an upgrade to Ubu9.04, regardless
of what wireless hardware was being used and so far no real fixes (at least that'd work for me).

anyway, I'm using a USB device called Fritz! (living abroad in Germany), which comes with a windows
driver. It used to work perfectly with Ubuntu 8.04 and 8.10 :( and which can not be driven correctly 
by the system anymore: keeps asking me about the key and fails at connecting eventually. :confused:

I'd like not to give a point to Winyeark, which I was about to drop, but on the other hand I'd like to avoid 
spending nights on the issue, which I thought would quite trivial... I would be very grateful for any 
guidance there, and so would be, I'm sure, thousands of users around if we can get if fixed. ;)

Cheers !

---

### Post by pompompompom on 2009-05-05
no answers :(
ok I'll try to more proactive:

> 
>lsusb
Bus 001 Device 002: ID 057c:6201 AVM GmbH WLAN USB v1.1
>

May I add any further useful info to get some support ?
Thanks a million !

---

### Post by flash63 on 2009-05-08
Hi,
try a
```
sudo renice +19 $(pidof wpa_supplicant)
```while connecting.

---

### Post by pompompompom on 2009-05-08
Thanks Flash for that. Unfortunately this does not help in my case
> 17:25:06 thomas@pcDeZogust> sudo renice +19 $(pidof wpa_supplicant)
[sudo] password for thomas: 
4251: priorité précédente 0, nouvelle priorité 19
3753: priorité précédente -2, nouvelle priorité 19


goes fine but connection loop keeps going on and asking me again for
the authentification.
Is there anyother command I can use to check that I did not mess around the net 
drivers etc. in my various attemps to get wifi back ?

---

### Post by flash63 on 2009-05-08
64bit or 32bit system?
```
uname -a
```
Driver version?
```
cat /etc/ndiswrapper/*/*.inf | grep DriverVer
```

Sometimes the network-manager has a problem with mixed encryption (WPA1/2). Change the settings of your router to pure WPA1 or better WPA2 and try again.

---

