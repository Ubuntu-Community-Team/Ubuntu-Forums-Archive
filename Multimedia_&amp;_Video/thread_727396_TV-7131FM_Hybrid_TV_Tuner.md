---
title: "TV-7131/FM Hybrid TV Tuner"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by sdalgl72 on 2008-03-17
Hi I have this model in my Packard bell and was wondering whether it was compatible with Ubuntu and if so how do I check that it is installed properly?

As you can probably tell I am a complete noob.  So any help would be appreciated as I really do like this OS and would like to make the switch from XP MCE.

---

### Post by xc3RnbFO8P on 2008-03-17
If you want help on this you have to tell us more
has this tuner a name 
in terminal **> lspci**

---

### Post by sdalgl72 on 2008-03-18
Hi sorry realised was a bit brief 

Tried your code in terminal it didn't seem to work.

Here are the details for the tunner:

	TV-7131/FM Hybrid TV Tuner
Name: TV-7131/FM Hybrid TV Tuner
Type: Hybrid (analogue/digital) TV Tuner
Manufacturer Chipset: NXP
Manufacturer Board: ASUSTek
18-05-2005

---

### Post by xc3RnbFO8P on 2008-03-19
I dont know if this is your card:
It got this problem in Linux:
> DVB, VDR, (***unstable*** causes random memory corruption and crashes)
Take a look at the images.
[http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Asus]("http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Asus")
On this site is a download link to a driver needed (dvb-fe-tda10046.fw).
[http://www.linuxtv.org/wiki/index.php/Asus_My_Cinema-P7131_Hybrid]("http://www.linuxtv.org/wiki/index.php/Asus_My_Cinema-P7131_Hybrid")
You have to install v4ldvb first.
[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers]("http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers")

---

### Post by sdalgl72 on 2008-03-19
Dont think it is but I will give it ago see what happens Cheers for the help

---

