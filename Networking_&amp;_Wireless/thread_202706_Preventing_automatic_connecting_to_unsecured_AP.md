---
title: "Preventing automatic connecting to unsecured AP?"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by Genix5 on 2006-06-23
First post here :)

I'm having a small issue with my wireless connection. I tried searching the forums for a solution (like I did with other problems), but I can't seem to find anything for this one. It's not that I can't get a connection, but it's that Ubuntu is automatically connecting to any unsecured AP in range when my own AP gets flakey or looses signal. How can I prevent this from happening? I'm connecting to my AP with 128bit WEP and SSID broadcasting off. I tried using iwconfig as such: "sudo iwconfig eth0 ssid "my network here" key "my key here" and it'll connect to my AP no problem. But unfortunately, these settings don't stay after a reboot. Even with the built in Network tool having the right setup, it still connects to the first unsecured AP it picks up when I'm rebooting. :( I want it setup so it'll connect to my AP, and my AP alone.

Thank you for any suggestions! If any more information is needed about my wireless card or computer setup, let me know. I didn't bother posting it because I'm almost 100% sure it's just something minor I'm overlooking since I'm new to Linux. ;)

---

### Post by queenorych on 2006-06-24
try 
iwconfig ra0 key restricted 

this will disallow ra0 from connected to unsecured networks.  Obviously change ra0 to whatever your wireless card is.

---

### Post by Genix5 on 2006-06-24
Thanks for the very quick reply. That looks like exactly what I was looking for. :-D

---

