---
title: "Huawei E1552 USB-stick modem"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by Saunatonttu on 2009-09-04
Does anybody here know how to monitor or see USB-modems signal strength?  

iwlist is good fo wireless connections, but  it doesnt work with this usb-stick...

---

### Post by puppywhacker on 2009-09-04
the vodafone mobile connect software is showing mobile signal strength. I guess the way it works is by running an AT command over /dev/ttyUSB3

---

### Post by Saunatonttu on 2009-09-08
Hmm!

I found gcom program from ubuntu. 

but it gives an error:

gcom -d /dev/ttyUSB1
 ***SIM ERROR***
Check device port configuration.
Check SIM is inserted
Test SIM in a mobile phone?


My modem works with that NetworkManager Applet 0.7.0.100, but i just want to see signal strength. :)

---

### Post by Saunatonttu on 2009-09-08
network manager uses GSM (ttyUSB0)

but with gcom:

Can't open GlobeTrotter /dev/ttyUSB0.

---

### Post by duleep on 2009-11-07
my huawei e1552 was not working in 9.04 but it autorun work and show mobile partner icon on Desktop. this is before few week work well. plz help to me

---

### Post by Saunatonttu on 2009-11-09
Hi!

It works fine on ubuntu 9.4. You have to have usbserial and usb-storage modules loaded with modprobe and also that usbmodeswitch program.. set your pincode and all that with networkmanager.

---

### Post by duleep on 2009-11-28
Saunatonttu: ya it may be get like storage device, how do that plz tell me

---

### Post by mohdshakir on 2010-10-14
There's a good tutorial on this one;
[http://www.techrecipes.net/operatingsystem/ubuntu/configure-huawei-e1552](http://www.techrecipes.net/operatingsystem/ubuntu/configure-huawei-e1552)

---

