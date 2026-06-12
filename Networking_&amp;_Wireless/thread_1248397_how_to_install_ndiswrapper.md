---
title: "how to install ndiswrapper"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by tonjaa on 2009-08-24
[COLOR=DarkOrange]i use Ubuntu 9.04 Kernel 2.6.28-15-generic
motherboard Asus P5K-E with wifi-AP Solo / Realtek RTL8187 wireless adapter.[/COLOR]
i try to install driver for wireless adapter at first time i think i do wrong way i can't use wireless i remove ndiswrapper . now i download file ndiswrapper .tar.gz version 1.55but i don't know this correct version or not .
i want to know correct command to install and correct way to install about driver please guide me.

---

### Post by ajgreeny on 2009-08-24
Just use the version in the repositories, ```
sudo apt-get install ndisgtk
```which will also pull in ndiswrapper-common and you should be good to go, though this assumes that the wireless card you have is supported by the ndiswrapper package; not all are.

When you have installed this, there is a menu item in *System >Administration >Windows Wireless Drivers* or something similar, which should allow you to use the .inf file from your card's windows driver files, usually found on a CD with the card, or if not from a web search.  You should have no need to use a tar.gz archive to install ndiswrapper.

---

### Post by tonjaa on 2009-08-24
i try to install ndiswrapper-1.55 i see the way install  from this 
 [http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper)
i can installed but it have problem i can't see folder ndiswrapper at  folder etc .
and at system >administration not show windows wireless driver 
when i install it has folder ndiswrapper-1.55 on Desktop
i try to use command sudo modprobe ndiswrapper i got this
[COLOR=SeaGreen]
tonjaa@tonjaa-desktop:~$ sudo modprobe ndiswrapper
[sudo] password for tonjaa: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.[/COLOR]

and use command dmesg | grep -e wlan 

[COLOR=SeaGreen]tonjaa@tonjaa-desktop:~$ dmesg | grep -e ndis -e wlan
[   14.257959] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.281469] usbcore: registered new interface driver ndiswrapper
[   43.441693] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/COLOR]

what's wrong how i can do it?  this correct ndiswrapper or not ?

---

### Post by ajgreeny on 2009-08-24
Have you actually tried the ndis-gtk I suggested in the previous post, it really is the easiest way to install and use ndiswrapper in jaunty, it is certainly the way I did it for two laptops in the household.

---

### Post by tonjaa on 2009-08-25
i reinstall  ndiswrapper by command  [COLOR=SeaGreen]sudo apt-get install ndisgtk[/COLOR]
i try add driver.inf  from> Windows wireless driver but it has some  message when i add driver
[COLOR=Red]" unable to see if hardware is present "[/COLOR]  at  box of currentry installed Windows drivers show
[COLOR=Green]Hardware present Yes.[/COLOR] 
what it mean ?  and how i can use wireless ?

---

### Post by ajgreeny on 2009-08-25
It seems to be a bug when that error message appears, as the same thing happened on my machine, though the wireless connection was working fine.

Just click on the ok button when you see that error, then go to the network icon (two screens together) in your notification area, and the wireless networks detected should show.  Click against the one you want to connect to, enter the password or whatever, and it should work OK.

---

### Post by tonjaa on 2009-08-26
[COLOR=Blue]OK. now i can use Wireless that first time i confuse after i try to reinstall ndiswrapper and i add driver again
i wrong that i think my wifi card is PCI but i find spec from web [http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)
my chip is Realtek RTL8187 it's USB type and i can download correct driver .
then i find program for manage wireless from synaptic package manager i use RutiIT Wlan Manager 
and i read manual book for Asus Wifi-AP-Solo i can use in mode ad-hoc 
thank you very much for guide me.
for human being[/COLOR] :)

---

### Post by ajgreeny on 2009-08-26
You are very welcome.  I'm happy it now works for you.

---

