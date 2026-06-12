---
title: "wifi dialup conflict"
date: 2011-12-09
forum: Networking &amp; Wireless
---

### Post by uh-huh on 2011-12-09
Hi forum,

No high-speed internet here, so have to use dialup. But I can't use dialup and talk to my wifi router at the same time. I have to rmmod ath9k before dialup connects. And once connected can't modprobe ath9k or dialup stops. There's no error message and the modem lights still flicker but I can't ping the web.

---

### Post by gordintoronto on 2011-12-10
To confirm: you have a dial-up modem, with a wireless router attached to it? If so, your computer should only worry about the wifi, and the router should make the modem dial and connect.

---

### Post by uh-huh on 2011-12-10
> **gordintoronto said:**
> To confirm: you have a dial-up modem, with a wireless router attached to it? If so, your computer should only worry about the wifi, and the router should make the modem dial and connect.

Not quite. 

Modem is old USR attached to PC via usb/serial connector. Strictly analog dialup. I use $sudo pon <isp> to connect to web. 

Router is Linksys WRT. It connects via wlan0 to the PC and via eth0 to my laptop.

web<->(ppp0)PC(wlan0)<->WiFi Router<->(eth0)laptop

Ideally, it would be nice to be able to reach the laptop while surfing the web. But that's not possible so far.

---

### Post by gordintoronto on 2011-12-10
> **uh-huh said:**
> Modem is old USR attached to PC via usb/serial connector. Strictly analog dialup. I use $sudo pon <isp> to connect to web. 

Router is Linksys WRT. It connects via wlan0 to the PC and via eth0 to my laptop.

web<->(ppp0)PC(wlan0)<->WiFi Router<->(eth0)laptop

Ideally, it would be nice to be able to reach the laptop while surfing the web. But that's not possible so far.

I'm not sure what you mean by "reach the laptop."

---

### Post by uh-huh on 2011-12-11
> **gordintoronto said:**
> I'm not sure what you mean by "reach the laptop."

Well, ping it, copy to/from it etc. At the same time the PC is "reaching" the internet. It's quite simple, really.

---

