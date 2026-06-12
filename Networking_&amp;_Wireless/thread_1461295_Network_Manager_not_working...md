---
title: "Network Manager not working.."
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by sunnyengineeer on 2010-04-24
Hello,
         I've Ubuntu 8.10(Interpid Ibex).I'm using my Mobile to connect to the internet thru GPRS using USB cable.
    Recently Im facing a strange problem:-
My network icon on the top shows disconnected,whereas if I type "lsusb" in terminal it shows Nokia Phone as USB device.
   But If I click on the top icon I get the statusbar "[COLOR=Blue]Network Manager not working[/COLOR]"

Even reconnecting it is not making any chnage not by swithcing off the mobile & than connecting...
...Can somebody plz guide me how can I start this process?

Thanks
Sunny Sharma
===============================================
[COLOR=Red]*"There are only 10 types of persons in this world,one who understand binary & other who don't"*[/COLOR]
===============================================

---

### Post by dineshs on 2010-04-24
1.For NM to manage connections,
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
must display
```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true
```
That is the last line should be
managed=true
and
```
gksudo gedit /etc/network/interfaces
```
should contain only this
```
auto lo 
iface lo inet loopback
```
Can you check this?
2.You are connecting via nokia mobile.Which method are you using ?
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by sunnyengineeer on 2010-04-24
Hello Dinesh,

          I got it ,my internet connection is Broadband not Dialup..sry
...Abt the problem now..

Now when my net is working in Ubuntu the first command is showing:-

[COLOR=Blue][main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false[/COLOR]

The second command is showing the same as required & given by you...

But the 1st command o/p is difft.,
...Plz elabrote what I've to do with the 1st .conf file when I face the problem?

Thanks
Sunny Sharma
=====================

There are 10 types of persons in this world-
One who understand binary
One who don't
=====================

---

### Post by dineshs on 2010-04-24
Do you have a broadband modem?How is it connected? via ethernet?

---

### Post by sunnyengineeer on 2010-04-24
@Dineshs
               No I don't have wired internet.
When I need to do surfing ,I connect my mobile to PC thru USB.....Ubuntu automatically detects & says"You are ow connected to Airtel"
        In the properties it shows "Airtel Broadband Connection".
Thanks
Sunny Sharma

---

### Post by NichoTL on 2010-04-24
> **sunnyengineeer said:**
> @Dineshs
               No I don't have wired internet.
When I need to do surfing ,I connect my mobile to PC thru USB.....Ubuntu automatically detects & says"You are ow connected to Airtel"
        In the properties it shows "Airtel Broadband Connection".
Thanks
Sunny Sharma

I don't understand why NetworkManager is not working... try and restart it:
```
sudo start network-manager
```
Any change?

---

### Post by Iowan on 2010-04-24
> **NichoTL said:**
> I don't understand why NetworkManager is not working...NM may have been running - just not working because it had nothing to manage. Changing **nm-system-settings.conf** gave it something to manage.

---

