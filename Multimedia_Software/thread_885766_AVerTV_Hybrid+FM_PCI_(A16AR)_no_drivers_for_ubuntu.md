---
title: "AVerTV Hybrid+FM PCI (A16AR) no drivers for ubuntu"
date: 2008-08-10
forum: Multimedia Software
---

### Post by Phantomas on 2008-08-10
Hello i have the mentioned card but when i open tvtime it shows no signal...
I gave to the terminal these commands 

```
sudo rmmod saa7134_alsa
sudo rmmod saa7134_dvb
sudo rmmod saa7134
sudo modprobe saa7134 card=99

```

but still no signal... 

At the site of Avermedia it has drivers only for mandrica and suse... can anyone help me make this card work?

Thanks in advance

---

### Post by xc3RnbFO8P on 2008-08-10
Try:
> modprobe saa7134 card=85
[http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_777_(A16AR)]("http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_777_(A16AR)")

---

### Post by Phantomas on 2008-08-10
Thank you for your reply
but this is a different card it is AVerTV DVB-T 777

---

### Post by xc3RnbFO8P on 2008-08-10
Sorry wrong site:
[http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_Hybrid%2BFM_PCI]("http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_Hybrid%2BFM_PCI")

---

### Post by Phantomas on 2008-08-10
Ringi this is what i am doing but still says no signal :(

---

### Post by xc3RnbFO8P on 2008-08-11
Read this (in Spanish):
[http://zonabuologica.wordpress.com/2007/12/04/configurar-avermedia-avertv-hybrid-fm-pci-chip-saa7134/]("http://zonabuologica.wordpress.com/2007/12/04/configurar-avermedia-avertv-hybrid-fm-pci-chip-saa7134/")
Or you can Google it if you want to translate it:
[+Configurar+AverMedia+AverTV+Hybrid%2BFM+PC&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a"]http://www.google.dk/search?q=[COMO]+Configurar+AverMedia+AverTV+Hybrid%2BFM+PC&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a]("http://www.google.dk/search?q=[COMO)

---

### Post by Phantomas on 2008-08-11
I read it... i did all he said but no signal with tvtime....

keep in mind that i am talking about analogue tv and fm radio

any other ideas?  

:(

---

### Post by xc3RnbFO8P on 2008-08-11
It says on the bottom on the page:
> There is two thing missing to get full use of this card, lirc and analog suport

---

