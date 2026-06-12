---
title: "elp with D-Link DWL-G520+ PCI wireless adapter isn't recognized in Ubuntu 9.10"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by cameronol on 2009-12-21
hi, 
i'm trying to get my Wireless PCI card to work in Ubuntu 9.10 (32 bit) ~with wpa (personal) encryption,i personally think Ubuntu is better then Windoze and would extremely like to migrate over to 9.10.
I could use wireless before 9.1 and cant seem to get it to work after the update(same as everybody else).

Info about card:
Company: D-link
Model: DWL-G520+
Chipset: TI
*Driver: acx1xx

*-I'm pretty sure it uses acx111 but not sure

Right now i'm on my windows xp pro hard drive and the card works perfectly fine (as with the majority). i've tried many guides on how to get it working, but i've never actually gotten the DWL-G520+ to work. 
(note: i also have a temp wired connection in 
ubuntu, but i would not like that to stick)


Please help, if you can
,Cameronol

---

### Post by prshah on 2009-12-21
> **cameronol said:**
> 
Company: D-link
Model: DWL-G520+
Chipset: TI
*Driver: acx1xx
*-I'm pretty sure it uses acx110 but not sure


According to [this wiki]("http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu"):> From Feisty onwards, NetworkManager was included in the main distribution. Since the ACX driver cannot interface correctly with it, NetworkManager might have to be disabled. See the instructions on how to disable it in the Feisty section of this document.  Please see more details in the linked wiki, and post back if you require more specific assistance.

Note that the wiki does not seem "current"; please carefully document your commands and experiences, in case you need to undo any changes you make.

If you would rather not go down this path, you can consider using it's windows driver with ndiswrapper; post back if you want details on this.

---

### Post by cameronol on 2009-12-21
Hello again,

i have tried disabling Network Manager and all i get is
```
root@cameron-ubuntu:/home/cameron# sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo: /etc/dbus-1/event.d/25NetworkManager: command not found
root@cameron-ubuntu:/home/cameron# 

```

i'm guessing this is what you meant by seems not present..

soo in this case, yes i would love for some info on ndiswrapper..
(i think i already have the latest acx2008*.tar.bz2 files, but i can get them again if you want me to! :)..

thank for your ongoing help ,

Cameronol

---

### Post by prshah on 2009-12-21
> **cameronol said:**
> 
```
root@cameron-ubuntu:/home/cameron# sudo /etc/dbus-1/event.d/25NetworkManager stop

```


From 9.10 onwards, please use the "service" command to access services. Eg to stop network-manager, use```
sudo service network-manager stop
```

I always prefer to use the native driver instead of ndiswrapper. I suggest you use ndiswrapper only as a last choice. If it is not urgent, a day or two spent working on this will be more rewarding.

---

### Post by cameronol on 2009-12-22
well instead of doing that, i just disabled it in the startup menu...

i have tried ndiswrapper, got the drivers and everything (tested and worked), and when i install them in the ndis-gui it just says the hardware isn't connected, the drivers install fine, but it can't see my card.

i was looking at the wiki for acx111 and it says i need to like, imbed the firmware into my kernel and the drivers into the actually system?, please correct me if i'm wrong

---

### Post by DaveBG on 2009-12-24
See here -> mine worked with NDISWrapper as these people suggested here:
[http://ubuntuforums.org/showthread.php?t=1341794&highlight=d-link+dwl-g520](http://ubuntuforums.org/showthread.php?t=1341794&highlight=d-link+dwl-g520)

---

### Post by cameronol on 2009-12-31
hmm, cool, i might have a look at your thread..

---

### Post by baram204 on 2010-02-25
Hi i have G520+

I found solution.

From Internet, Download tnet1130 driver.

and Using ndiswraper. install tnet 1130 driver into your Ubuntu machine.

It work!!

Driver from the d-link.. & madwifi ... ath5, ath9 

won't work.. i tried about hundred time..

compile and change over and over.. it won't work..

use Tnet 1130 driver!!

---

### Post by cameronol on 2010-04-11
Where would i get this Tnet 1130 driver from? i've searched but can not find

---

