---
title: "3Com 3CRWE154G72 wifi card still not work in kernel 26"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by petoro on 2006-07-11
I have just updated the kernel to 2.6.15.26 but the wifi card still not works.

The last kernel where it works is 2.6.15.19  (prior kernels worked as well).

Is there any prevision to make it work again in future kernels?

Do you know a way (step by step) to make it work in this 26 kernel?


Petoro

---

### Post by awaldram on 2006-07-13
Hi yes

make sure you black list all the islsm stuff as this is a beta driver and doesn't work very well on v1 prism54 cards.

load module prism54 and check whether it works (It didnt' post 2.5.15-19)but ymmv

If it doesn't then go with ndiswrapper.

If your ability quite high you could compile 2.6.16 as this does work (prism54)

---

### Post by llondru on 2006-07-13
Hi, just have the same wireless card.
I'm a total newbie, just installed ubuntu 6.06 from scratch on an old laptop.

I'm totally lost with this instructions, if someone could just explain it for noob's ...
Other thing, I can't install wireless or network manager, just says it has to find new catalog software from the internet, the problem is I just don't have internet on ubuntu :s

Any help will be greatly appreciated.

---

### Post by awaldram on 2006-07-13
Ok
it'll be difficult/impossible without a network connection as some packages are required that are not on the cd.

in /etc/modprobe.d/blacklist

add

#blacklist prism54
blacklist islsm_usb
blacklist islsm_pci
blacklist islsm_device
blacklist islsm_pci

this will allow you to try the prism54 driver .

reboot then insert the card type

iwconfig

and see what youve got if nothing 

try sudo modprobe prism54
 then try again

if still nothing the dmesg and lsmod should give you a clue

lsmod should have none of the blacklisted drivers present

and dmesg should report  the prism54 driver 

if it doesn't work (which prior to 26 it didn't) then you will need an internet connection.

you'll need to install

ndisgtk and ndiswrapper-utils

from system administration  'windows wireless drivers' install new driver (windows disk required)

modprobe ndiswrapper and you should be in bussiness.

you'll need to add ndiswrapper to /etc/modules to survive a reboot so the module is automaticaly loaded.

of cause this only get the driver working you'll still need to configure the network for you wifi setup ssid wep or wpa

---

### Post by awaldram on 2006-07-13
whoops you'll also need to blacklist prism54 to use ndiswrapper 

(remove the #)

---

### Post by llondru on 2006-07-13
> **awaldram said:**
> Ok
it'll be difficult/impossible without a network connection as some packages are required that are not on the cd.

in /etc/modprobe.d/blacklist

add

#blacklist prism54
blacklist islsm_usb
blacklist islsm_pci
blacklist islsm_device
blacklist islsm_pci

this will allow you to try the prism54 driver .

reboot then insert the card type

iwconfig

and see what youve got if nothing 

try sudo modprobe prism54
 then try again

if still nothing the dmesg and lsmod should give you a clue

lsmod should have none of the blacklisted drivers present

and dmesg should report  the prism54 driver 


So, it dosen't work,  dmesg and lsmod act as you describe

> **awaldram said:**
> if it doesn't work (which prior to 26 it didn't) then you will need an internet connection.

you'll need to install

ndisgtk and ndiswrapper-utils

from system administration  'windows wireless drivers' install new driver (windows disk required)

modprobe ndiswrapper and you should be in bussiness.

you'll need to add ndiswrapper to /etc/modules to survive a reboot so the module is automaticaly loaded.

of cause this only get the driver working you'll still need to configure the network for you wifi setup ssid wep or wpa

Ok, I just try to download from the MAC, and transfering to the laptop via usb key (hope it works)

Is there a web page for the donwload? thanks!!

---

### Post by awaldram on 2006-07-13
[http://archive.ubuntu.com/ubuntu/pool/main/n/](http://archive.ubuntu.com/ubuntu/pool/main/n/)

will get you ndiswrapper 

[http://archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/](http://archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/)

you'll have to check in synaptic which is the right version

---

### Post by petoro on 2006-07-14
Eureka!  With this help it worked at last in kernel 26!

These are the steps that worked for me:

as you said, in 
/etc/modprobe.d/blacklist
add:
blacklist prism54
blacklist islsm_usb
blacklist islsm_pci
blacklist islsm_device
blacklist islsm_pci
reboot

cd "/home/juan/Desktop/wifi3Com/Driver"
(or wathever directory where you have the 3Com Windows drivers)
ndiswrapper -i 3C154G72.INF

ndiswrapper -l   
(to see if the driver has been loaded succesfully)

sudo modprobe ndiswrapper
(to activate it)

and it worked at last!!!
to survive in the next boots you have to add this line:
ndiswrapper
to the 
/etc/modules 
file

Thanks,


Josechu


> **awaldram said:**
> Ok
it'll be difficult/impossible without a network connection as some packages are required that are not on the cd.

in /etc/modprobe.d/blacklist

add

#blacklist prism54
blacklist islsm_usb
blacklist islsm_pci
blacklist islsm_device
blacklist islsm_pci

this will allow you to try the prism54 driver .

reboot then insert the card type

iwconfig

and see what youve got if nothing 

try sudo modprobe prism54
 then try again

if still nothing the dmesg and lsmod should give you a clue

lsmod should have none of the blacklisted drivers present

and dmesg should report  the prism54 driver 

if it doesn't work (which prior to 26 it didn't) then you will need an internet connection.

you'll need to install

ndisgtk and ndiswrapper-utils

from system administration  'windows wireless drivers' install new driver (windows disk required)

modprobe ndiswrapper and you should be in bussiness.

you'll need to add ndiswrapper to /etc/modules to survive a reboot so the module is automaticaly loaded.

of cause this only get the driver working you'll still need to configure the network for you wifi setup ssid wep or wpa

---

### Post by llondru on 2006-07-14
> **petoro said:**
> Eureka!  With this help it worked at last in kernel 26!

These are the steps that worked for me:

as you said, in 
/etc/modprobe.d/blacklist
add:
blacklist prism54
blacklist islsm_usb
blacklist islsm_pci
blacklist islsm_device
blacklist islsm_pci
reboot

cd "/home/juan/Desktop/wifi3Com/Driver"
(or wathever directory where you have the 3Com Windows drivers)
ndiswrapper -i 3C154G72.INF

ndiswrapper -l   
(to see if the driver has been loaded succesfully)

sudo modprobe ndiswrapper
(to activate it)

and it worked at last!!!
to survive in the next boots you have to add this line:
ndiswrapper
to the 
/etc/modules 
file

Thanks,


Josechu


done all the steps, I see the card in "Windows Wireless Drivers"... and then, what am I suposed to do? I don't see the interface anymore in " network tools" ....
](*,)

---

### Post by petoro on 2006-07-14
I think you should go to System --> Administration --> Networking to configure the ip, dns, wep key....


Josechu

---

### Post by awaldram on 2006-07-15
or install netowork manager if you reuire wpa - search in these threads for help on configuring.

or install wifi-radar if you reuire wpa - wep - open all from the same config

now must dash seem to have lost my q key ;-)

best of luck

iwconfig will tell you if the drivers working
iwlist scan will show if the radio's up an running

well done Petoro

---

### Post by llondru on 2006-07-15
> **petoro said:**
> I think you should go to System --> Administration --> Networking to configure the ip, dns, wep key....


Josechu

I only have "loopback" interface... so that's the problem. I don't have the wifi-card as a network interface....

> **awaldram said:**
> or install netowork manager if you reuire wpa - search in these threads for help on configuring.

or install wifi-radar if you reuire wpa - wep - open all from the same config

now must dash seem to have lost my q key ;-)

best of luck

iwconfig will tell you if the drivers working
iwlist scan will show if the radio's up an running

well done Petoro


iwconfig:

lo            no wireless extensions
sito         no wireless extensions


Sure I'm missing something but I don't get it ](*,)

---

### Post by Flumuxed on 2006-12-08
I had my 3Com card working with ndiswrapper under Ubuntu 6.06, since 'upgrading' to 6.10 the wretched thing won't work.  ndiswrapper -l confirms its' installed and hardware ready, but can't see wireless device under Sys/Admin/Network, just wired etho and modem.

Any suggestions?

---

