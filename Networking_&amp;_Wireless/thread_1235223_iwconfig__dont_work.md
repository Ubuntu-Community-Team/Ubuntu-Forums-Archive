---
title: "iwconfig  dont work"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by samibhfr on 2009-08-08
i have  ubunto 8.10 problem :
when i execute  sudo airman-ng   or iwconfig   i have not any information about my wireless card ?! (NB: internet work fine with this ubunto)

thx

---

### Post by kerry_s on 2009-08-08
do you have wireless-tools installed ?
look in synaptic package manager you'll have to have them installed before you can use them.

---

### Post by samibhfr on 2009-08-09
> **kerry_s said:**
> do you have wireless-tools installed ?
look in synaptic package manager you'll have to have them installed before you can use them.


synaptic package manager is istalled, and im connected to wireless netework and internet but:

-when i do sudo airmon-ng  he write :  interface     chipset      Driver        without any information about them!!!! why ?

-when i do iwconfig he write:  
          lo         No wireless extensions
          eth0     No wireless extensions
          pan0    No wireless extensions

---

### Post by kerry_s on 2009-08-09
airmon-ng has nothing to do with setting up your wireless.

check if you have "wireless-tools" in synaptic. see pic 1

if you do have wireless-tools then you can do "sudo iwconfig". see pic 2

if it does not show your wifi, then you probably need to install some kind of firmware or driver. 
to tell you which one we need to see the output of "lspci" if it is a card, use "lsusb" if it is a usb wifi device.

---

### Post by samibhfr on 2009-08-09
> **kerry_s said:**
> airmon-ng has nothing to do with setting up your wireless.

check if you have "wireless-tools" in synaptic. see pic 1

if you do have wireless-tools then you can do "sudo iwconfig". see pic 2

if it does not show your wifi, then you probably need to install some kind of firmware or driver. 
to tell you which one we need to see the output of "lspci" if it is a card, use "lsusb" if it is a usb wifi device.

-my wireless-tools is installed

-i do "sudo iwconfig" but dont show my wifi   i have just this:
lo         No wireless extensions
          eth0     No wireless extensions
          pan0    No wireless extensions

-when i do lspci i have this:
[http://img9.imageshack.us/i/ubnuto2.jpg/](http://img9.imageshack.us/i/ubnuto2.jpg/)

[IMG]http://img9.imageshack.us/i/ubnuto2.jpg/[/IMG][IMG]http://ubuntuforums.org/%5Burl=http://img9.imageshack.us/i/ubnuto2.jpg/%5D%5Bimg=http://img9.imageshack.us/img9/8426/ubnuto2.jpg%5D%5B/url%5D[/IMG][IMG]http://img9.imageshack.us/i/ubnuto2.jpg/[/IMG]

---

### Post by kerry_s on 2009-08-09
your using vmware, i don't think that does wifi & there's no wifi listed in your lspci.

---

### Post by samibhfr on 2009-08-09
> **kerry_s said:**
> your using vmware, i don't think that does wifi & there's no wifi listed in your lspci.

ok thank you Kerry_s

---

