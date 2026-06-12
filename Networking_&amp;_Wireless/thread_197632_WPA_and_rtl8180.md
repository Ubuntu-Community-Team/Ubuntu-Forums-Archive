---
title: "WPA and rtl8180"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by Huubke! on 2006-06-16
Does anyone know how to get WPA working on a Realtek rtl8180 card? I'm using the driver shipped with dapper. I've tried some things with iwconfig, but it looks like the driver just doesn't support WPA. Any ideas? (Thanks!)
(The last thing that keeps me from switching completely from "that other OS".)

---

### Post by costoa on 2006-06-16
Well, it could be something like 

(I'll assume your is ra0)

```

iface ra0 inet dhcp 
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "myssid"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set Channel=1
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="A shared key"
        pre-up ifconfig ra0 up

```

Lot's of questions like are you using WPA/WPA2, TKIP/AES, channel, etc. Try modding the above and post results. Remember to bring the interface up/down via "sudo ifup ra0" and "sudo ifdown ra0".

costoa

---

### Post by Kosmonaut on 2006-11-11
Hey!

Did you have any positiv results with your RTL8180 card using WPA? I am currently trying to get it working, but I am sort of stuck...

---

