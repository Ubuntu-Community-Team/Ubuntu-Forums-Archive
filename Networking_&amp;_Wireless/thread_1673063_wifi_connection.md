---
title: "wifi connection"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by slixz85 on 2011-01-21
hi my wifi connection works decent right now. it is off of my friends signal, however i tried tellin them to check any kind of settings with their system or somethin to speed it up because it does seem slow sometimes and lag. the signal will drop every so often but only on my side in my house. my friends connection is always fine. is there any kind of settings i need to change on just my laptop and if not is their optimization i can do anyway? and my friends wifi is all default setup as well. nothing has been changed to it?

his runs windows, mine linux

---

### Post by sml156 on 2011-01-21
The further away from the wireless acces point you are the slower the connection will be.

---

### Post by slixz85 on 2011-01-21
yeah i got that but its right next door. apt's

---

### Post by sml156 on 2011-01-21
There might be a concreat wall between apts
You could try connecting at a different speed. Im not on my linix box right now but here is how I start my wireless because im in the same boat 
 
>  
ifconfig wlan0 down
ifconfig wlan0 up
iwconfig wlan0 rate 5.5M auto
 
>  
I dont know offhand the different settings but if you google.com/linux 
[QUOTE] 
iwconfig wlan0 rate 5.5M auto
[/QUOTE]
you shoud find them

---

