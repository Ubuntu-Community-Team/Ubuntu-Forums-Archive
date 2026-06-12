---
title: "Commands for wireless connection in root prompt...."
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by trust-no-one on 2011-03-12
Hi everyone,
I have been reduced to a root shell and need to get updates. I know the commands for this, but cannot connect to my wireless n network. My card has worked on previous Ubuntu releases (i'm on 11.04 A3 now) and it uses WPA2 for the key. Can anyone tell me the required commands?
TIA,
tno

---

### Post by spiky001 on 2011-03-12
See if this helps ```
ifconfig wlan0 down
``` ```
iwconfig wlan0 mode managed
``` ```
iwconfig wlan0 key "Key"
``` ```
iwconfig wlan0 channel "Channel"
``` ```
iwconfig wlan0 essid "Essid"
``` ```
dhclient wlan0
```

---

### Post by Joe of loath on 2011-03-12
Spiky, that won't work for WPA.

OP, you'll need to use wpa_supplicant. check man wpa_supplicant.conf for details of how to write a config file (I use WPA-TKIP, so I can't help you), and run:

wpa_supplicant -i (interface) -c /etc/wpa_supplicant.conf -d wext

And if it works and connects, add -B to the end, wait for 10 seconds or so, then run dhclient.

---

### Post by spiky001 on 2011-03-12
My mistake thought it did as well thks for info

---

### Post by trust-no-one on 2011-03-12
> **spiky001 said:**
> See if this helps ```
ifconfig wlan0 down
```...
```
dhclient wlan0
```

Yeah, after I do the down command, I can't do anything else, and if I don't do it it says I am connected to "" when I run iwconfig at the end. Will try the other method, though (arrrgh I have to reboot again!!!)

tno

---

