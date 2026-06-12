---
title: "WPA2 Problem"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by Whisp3r on 2009-04-09
Good morning. Thank you all in advance for your past help, and help which you continue to provide. I'm completely new to Linux, and bumbling around like crazy. :)

After getting Ubuntu installed, I've had a heck of a time trying to get it to log into my wireless network. I'm running WPA-PSK. I can connect find to my router via ethernet, and under windows XP. however, whenever I try to connect Ubuntu to it, it fails after a short while and says the password is invalid. I've confirmed the password is correct, as is the hash value for my WPA password. I'm just trying to go through the Wireless manager right now.

What am I doing wrong?

Update:
I am further confused. The wlan0 is managed mode, and I turned off the WPA on the router to see . that would help. Still no go?

---

### Post by mazato on 2009-04-09
what version of Ubuntu are you using?
I used to have this problem in 7.04 I think and upgraded and that solved the problem
I think there were some bugs with the supplicant in my instalation!!
DO you have the right modules for your card?!

---

### Post by Whisp3r on 2009-04-09
I'm on 8.10. My wireless card is seeing (through the wireless manager) all the local networks, identifies them and their encryption properly.. Using iwl3945 as the driver... it just doesn't wanna connect to nobody.. :(

Update: I dida little research, and came across the command "dhclient wlan0" Did that, and now I connected to my unsecured network and under WPA security. What do I need to do to avoid having to manualy run dhclient every time I want to connect? Hmm. Hmm. What the heck am I doing wrong? :) 


This is quite the learning experience!

---

