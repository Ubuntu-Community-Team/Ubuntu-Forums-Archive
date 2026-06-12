---
title: "wpa-supplicant / ifplugd"
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by lorenco on 2006-02-22
I have wpa-supplicant configured to use wpa @ home and leap in the office.  @ Home and @ work I get strange behaviour:

wpa starts fine. and then "dies" every couple of (intermittendly different) minutes.

I have also configured ifplugd but this does not really solve my problems as I lose my connections all the time ....

Dapper Testing here so please feel free to comment if this works on Breezy...:-k

Does anyone else have this problem ???

---

### Post by lorenco on 2006-02-23
There seems to be a problem using the madwifi driver.

I disabled the MadWifi drive and used ndiswrapper with the manufacturer supplied driver.
I also had to blacklist madwifi (ath_pci) module otherwise it loads it by default and the ndiswrapper do not load ...

Mini Howto:
> 
/etc/modprobe.d/blacklist ... add "ath_pci"  (any other way?:-k please advise)
modprobe -r ath_pci (remove if loaded)
ndiswrapper -i {location of inf file from manufacturer}
ndiswrapper -l
Installed ndis drivers:
xxxxx         driver present, hardware present
vi /etc/default/wpasupplicant 
Use the following line:
OPTIONS="-w -i ath0 -D ndiswrapper -c /etc/wpa_supplicant.conf
edit your /etc/wpa_supplicant.conf file according to the leap / wpa and off you go!


---

