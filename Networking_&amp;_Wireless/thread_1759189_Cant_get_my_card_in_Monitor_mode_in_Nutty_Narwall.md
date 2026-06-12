---
title: "Cant get my card in Monitor mode in Nutty Narwall"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by 50cool50 on 2011-05-15
[B]Hi 
I upgraded to nutty nawall last week.
great platform guys. congrats.
I had aircrack-ng running on my old version and it worked well in the old version of linux but now when i run the programme and put my card in monitor mode it throws me the following message:[/B]

Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
677    avahi-daemon
678    avahi-daemon
701    NetworkManager
765    wpa_supplicant
2037    dhclient
Process with PID 2037 (dhclient) is running on interface wlan0


anyone got any ideas? is there some bug fixes for the new platform i need to get?

thanks y'all:guitar:

---

### Post by 50cool50 on 2011-05-16
anyone?

---

### Post by josephmills on 2011-05-16
could we see ```
airmon-ng
```

---

### Post by chili555 on 2011-05-16
Have you tried the old school way?```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
aircrack whatever
```

---

### Post by josephmills on 2011-05-16
could you please tell us what kind of card it is also thanks ```
lspci -nn
``` or if it is a usb wifi thingy than ```
lsusb
``` thanks again

---

