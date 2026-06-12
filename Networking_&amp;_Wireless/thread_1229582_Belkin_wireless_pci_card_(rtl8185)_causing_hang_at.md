---
title: "Belkin wireless pci card (rtl8185) causing hang at startup"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by mish78 on 2009-08-02
Hi,
Everytime i put in my Belkin wireless pci card (rtl8185) Ubuntu 9.04 will hang on startup ( two seconds into the timer icon ).

I have tried pasting # Bad rtl818x linux drivers
blacklist rtl818x
blacklist rtl8185
blacklist r818x
blacklist r818 
into gedit /etc/modprobe.d/blacklist ( i had to create it as it didnt exist )
I did the same in into gedit /etc/modprobe.d/blacklist.conf
the annoyying part is  i can figure out how to remove the driver and i cant load ubunto with the card in the system as it will hang. When i did a fresh install of Ubunto it works fine whith the card but then hangs on reboot.
Can any one throw some suggestions my way as I am really struggling to get anywhere at all

---

