---
title: "Frozen"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by MOBAUS on 2009-01-12
Hi , 
I have installed 8.10 ubuntu onto my machine. but i have a problem with connecting to a network. It can detect other networks and my wireless card (TP-Link  TL-WN951N). After typing in the WEP key it asks for authorization or something (just type in account password). once i do that it starts to connect then ubuntu freezes , forcing me to reboot. 

I have looked around the forums and i have tried a few things .. boot from live and re-install ect . but nothing works. can anyone help me?

---

### Post by dmizer on 2009-01-13
What is the output of:
```
lshw -C network
```

---

### Post by alxchar on 2009-07-15
Hello everyone..I have exactly the same problem with MOBAUS with ubuntu 9.04..I also have the same wirelles adapter..I put the code that dmizer suggested and the output was the print screen i have attached...

i.m sorry for my english...and for the attachment..

thank you for every help..):P

---

### Post by dmizer on 2009-07-15
Install wicd and uninstall network-manager. The card should work then.

---

### Post by alxchar on 2009-07-16
I have already done this but as soon as i did my pc froze and then i could never load ubuntu..it was freezing just after the loading...:(:(:(:confused::confused:

---

