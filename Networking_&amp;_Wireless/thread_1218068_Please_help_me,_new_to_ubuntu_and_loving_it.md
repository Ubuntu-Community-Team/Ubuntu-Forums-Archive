---
title: "Please help me, new to ubuntu and loving it"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by psycho81 on 2009-07-20
Hi people got a "Little" problem with my wireless networking under Ubuntu 9.04. 

The on board Wlan was detected straight away "Good job Ubuntu" and is working ok, however I also have a Linksys WUSB300N USB dongle, I managed to get that working using "Windown Wireless Drivers" another brilliant job Ubuntu.  

So now I have both on board and external Wlan adapters working, the problem is I cannot shut the onboard Wlan off when I have my WUSB300N plugged in.  I tried the Wlan switch on my Laptop "Toshiba Satelite" and it shuts the whole wireless of for both devices. 

I have tried the Bios settings and there is no option to turn off Wlan.  Normally under windows I would I would just hit "FN+F8" and it shuts the onboard Wlan off. 

Sometimes I preffer to use the WUSB300N as it has a better range, the problem with both working at the same time is "They conflict" and  make the internet run slow.  
I would be really greatful if anyone could work this one out for me, sick of going to bed at 3am :confused:

---

### Post by jamest09 on 2009-07-20
```
sudo ifconfig wlan0 down
```

On whatever wireless interface you want shutdown

---

