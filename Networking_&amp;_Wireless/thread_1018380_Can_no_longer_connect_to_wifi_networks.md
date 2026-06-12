---
title: "Can no longer connect to wifi networks"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by H0L7 on 2008-12-22
Ok this is probably a really easy fix and i feel fairly retarded for allowing this to happen in the first place.

I have been customizing my desktop toolbar and now the wifi icon is gone.

I already tried connecting using the network manage but apparently that doesn't work.

running ubuntu intrepid
gnome 2.24.1
kernel 2.6.27-9-generic
lenovo t61 with a intel pro/wireless 4965 agn though i have the sneaking suspicion my hardware has nothing to do with this.


please someone tell me how to fix this

---

### Post by H0L7 on 2008-12-23
I apologize for my stupidity.

with holding that i must note that almost all of the related FAQs refer to a system applet that is not installed by default under intrepid specifically system>administration>network-settings

---

### Post by superprash2003 on 2008-12-23
post outpt of iwlist scanning from the terminal.,

---

### Post by jmmy73 on 2008-12-23
jimmy@ubuntu:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
jimmy@ubuntu:~$ 


I cannot use WIFI but i can use my 3G Modem???

---

### Post by superprash2003 on 2008-12-24
the command is **iwlist scanning**

---

