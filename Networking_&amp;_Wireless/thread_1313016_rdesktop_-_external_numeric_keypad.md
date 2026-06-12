---
title: "rdesktop - external numeric keypad"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by broche on 2009-11-03
Crunchbang 9.0
I used a Belgian Keyboard (azerty)
I have also an external numeric pad plugged in usb on my laptop
I use the following command
rdesktop -u jlwallen -p password -g 1224x1024 -a 16 192.168.1.100

When I use this command no problem with the usb numeric keyboard but my normal keyboard response in qwerty
so I added the -k parameter
rdesktop -u jlwallen -p password -g 1224x1024 -k be -a 16 192.168.1.100
The normal keyboard is OK now, but when I use the external one no response except the *
What can I do??

---

