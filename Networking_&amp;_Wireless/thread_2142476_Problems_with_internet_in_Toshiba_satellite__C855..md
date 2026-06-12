---
title: "Problems with internet in Toshiba satellite  C855."
date: 2013-05-05
forum: Networking &amp; Wireless
---

### Post by Aziz9902 on 2013-05-05
Hi !!
I'm begginer in ubuntu , but when i want to start using it i found these problems with internet that i don't have in my Laptop . nothing works , no Modem no wireless. i was searching for solutions in internet and i found your Forum so i hope that you help me to start with ubuntu .
 thank you very much  

here are some information that you may need about y laptop :) 

sudo lshw -C network 

*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:c2400000-c2403fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 7c:05:07:05:5e:60
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:c0004000-c0004fff memory:c0000000-c0003fff



~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]

---

### Post by romain.astie on 2013-05-05
Here's a thread that could help you : 
[http://ubuntuforums.org/showthread.php?t=1328011](http://ubuntuforums.org/showthread.php?t=1328011)

It's the same card, just an older version of ubuntu. (9.10, Karmic Koala)

---

### Post by Aziz9902 on 2013-05-05
Hello [COLOR=#000000]romain.astie, [/COLOR] and thank you for your answer :) 


i tryed what you adviced me but i have an other problem with the build-essential package 

this is the message  i got :)

   ~$ sudo apt-get install build-essential linux-headers-`uname -r`
[sudo] password for admin : 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet build-essential  ( this means , impossible to find the package build essential).

waiting for more propositions  thank you :)

---

### Post by varunendra on 2013-05-06
> **Aziz9902 said:**
> 
E: Impossible de trouver le paquet build-essential  ( this means , impossible to find the package build essential).

Hello Aziz, welcome to the forums :)

Please post the outputs of the following -
```
uname -mr
lsb_release -d
```

And can you connect to internet using a wired connection to download some packages? You seem to have correct driver loaded for your ethernet interface, so cable connection should work.

---

### Post by Aziz9902 on 2013-05-06
Hello and thank you for your answer !!

this is the results of the commands :)

> :~$ uname -mr
3.5.0-17-generic i686

:~$ lsb_release -d
Description:	Ubuntu 12.10
 
the wired connection seems working , i tried it between a windows and ubuntu and it works , i could ping between them  but i couldn't connect to internet ..

---

### Post by varunendra on 2013-05-06
Please try what is suggested here : [http://askubuntu.com/a/165002](http://askubuntu.com/a/165002)

However, if you can't get your wired connection to connect to internet, then we'll have to do a little more work. In that case, proceed as follows:

[LIST=1]
[*]To download the packages on a different computer : ```
sudo apt-get install **[COLOR="#800000"]--print-uris[/COLOR]** build-essential linux-headers-generic linux-headers-`uname -r`
```
[*]This command will, among a few other details, give you the download links for each package. Copy them in a text file and use them to download the packages on another computer. Then copy them to your Ubuntu computer and double-click to install.
[*]Download the driver from this link : [http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz](http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz)
[*]Copy the downloaded .tar.gz package to your Ubuntu computer desktop, then "Right-click on the package > Extract here". This will extract the downloaded package to a folder with the same name as the package (rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012).
[*]Once successfully extracted, open a terminal and run the following commands in it (one command at a time > let it finish > run the next command....) :
[/LIST]

```
cd ~/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
make
sudo make install
sudo modprobe -v rtl8723e
```


If, while compiling the driver, you get this error :
> .....**[COLOR="#FF0000"]error: [/COLOR]**‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)
Then you may need to do a little modification in the source code as mentioned here (post #36) : [http://ubuntuforums.org/showthread.php?t=2017622&p=12331931#post12331931](http://ubuntuforums.org/showthread.php?t=2017622&p=12331931#post12331931)

For reference : [http://askubuntu.com/a/154935](http://askubuntu.com/a/154935)

Let us know how it goes.

---

