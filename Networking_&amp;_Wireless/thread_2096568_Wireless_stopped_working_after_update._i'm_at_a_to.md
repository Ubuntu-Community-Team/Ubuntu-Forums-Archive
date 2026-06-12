---
title: "Wireless stopped working after update. i'm at a total loss :("
date: 2012-12-20
forum: Networking &amp; Wireless
---

### Post by jomasdf on 2012-12-20
Hello.

I'm useing a netgear WNA 3100 USB adapter. I got it to work after alot of work and everything was fine.

But yesterday there was some kind of update and i'm sure it said something about ndiswrapper.. and after reboot it was messed up.

ndiswrapper -l gives me

> bcmwlhigh5 : driver installed
	device (0846:9020) present


But iwconfig gives me

> lo        no wireless extensions.

eth0      no wireless extensions.

I have no idea what to do, I keep getting FATAL: Module ndiswrapper not found. And cant fix it.

Can somebody PLEASE help me with this! :cry:

---

### Post by Pjotr123 on 2012-12-20
Broadcom wireless cards should be able to run on a native Linux driver, so maybe you don't need ndiswrapper at all. Try this:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Install-drivers](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Install-drivers)

---

### Post by jomasdf on 2012-12-20
> **Pjotr123 said:**
> Broadcom wireless cards should be able to run on a native Linux driver, so maybe you don't need ndiswrapper at all. Try this:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Install-drivers](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Install-drivers)

Do you reffer to this ?

> Ubuntu 12.10:
Click on the grey Ubuntu logo (Dash home). Query: software. 
Click on Software Sources - tab Additional Drivers.

I do not see any wireless firmware options there, only graphic cards.

EDIT:


Ok, so I got the stupid thing working again.

$ sudo apt-get --purge remove ndiswrapper-*
after I went [http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)
and I downloaded it.
I unpack the file and copy the directory in my home user /home/joma
now with bash I reach the directory
$ cd /home/luca/ndiswrapper
do the command :
$ make distclean
$ make -C driver clean
now install with commands
$ make
$ sudo make install
now reach the windows files
$ sudo ndiswrapper -i location to file.inf
I check 
$ ndiswrapper -l
bcmwlhigh5 : driver installed
	device (0846:9020) present
I mount the drivers
$ sudo depmod -a
(was here the error Fatal etc.)
$ sudo modprobe ndiswrapper
now my wifi card is lighting and connecting to my network


I did this from a guide I found, to get ndiswrapper working seems to be a bit of a mystery. This way worked for me, maby it will help someone else to.

---

