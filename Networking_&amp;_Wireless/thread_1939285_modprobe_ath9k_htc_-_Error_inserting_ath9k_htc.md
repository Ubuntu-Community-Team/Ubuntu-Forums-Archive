---
title: "modprobe ath9k_htc - Error inserting ath9k_htc"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by DaMn3d on 2012-03-11
Hello! 
 
I'm running Backtrack 5 R1 32bit GNOME in VMware,.. kernel 2.6.39.4
 
I've been trying to get my **NETGEAR N150 WNA1100 USB** wireless card working which runs on a AR9271 chipset.
 
**supported devices: **
 
[FONT=Times New Roman][[COLOR=windowtext][FONT=Nimbus Sans L][FONT=Verdana][SIZE=1]http://linuxwireless.org/en/users/Drivers/ath9k_htc/devices[/SIZE][/FONT][/FONT][/COLOR]]("http://linuxwireless.org/en/users/Drivers/ath9k_htc/devices")[/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]**I've checked if the ID matches **[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]lsusb[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]the one I have and it does.. **ID 0846:9030**[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]**then I got:**[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]sudo apt-get install linux-headers-$(uname -r)[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Verdana][SIZE=1]sudo apt-get install build-essential[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Verdana][SIZE=1]wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]check out ok got them all [/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]**Downloaded the snapshot:**[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][[FONT=Verdana][SIZE=1]http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree[/SIZE][/FONT]]("http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree") [/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]**Extracted the archives in root directoy:**[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]tar xf compat-wireless-2.6.tar.bz[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Verdana][SIZE=1]tar xf linux-headers <--- whatever name is the newest[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]**went into the compat-wireless directory:**[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]cd compat-wireless..[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]**run the script, made, sudo make install:**[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]./scripts/driver-select ath9k_htc [/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Verdana][SIZE=1]make [/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Verdana][SIZE=1]sudo make install [/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]no errors[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]**replaced the old .fw with new .fw:**[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]cd.. [/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Verdana][SIZE=1]cd linux-firmware..[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Verdana][SIZE=1]sudo cp ar9271.fw /lib/firmware (tryed also manual copy just to make shure)[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]**rebooted (can allso use sudo make unload - same result)**[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=1]**checked & got the following: **[/SIZE][/FONT][/FONT]
 
```
 
root@bt:~/compat-wireless-2012-03-08# modinfo ath9k_htc
filename: /lib/modules/[2.6.39.4/updates/drivers/net/wireless/ath/ath9k/ath9k_htc.ko]("http://2.6.39.4/updates/drivers/net/wireless/ath/ath9k/ath9k_htc.ko")
firmware: htc_9271.fw
firmware: htc_7010.fw
description: Atheros driver 802.11n HTC based wireless devices
license: Dual BSD/GPL
author: Atheros Communications
srcversion: 7A881B98B1F9090F28BFF49
alias: usb:v0CF3p20FFd*dc*dsc*dp*ic*isc*ip*
alias: usb:v0411p017Fd*dc*dsc*dp*ic*isc*ip*
alias: usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*
alias: usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*
alias: usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*
alias: usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*
alias: usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*
alias: usb:v057Cp8403d*dc*dsc*dp*ic*isc*ip*
alias: usb:v0CF3pB003d*dc*dsc*dp*ic*isc*ip*
alias: usb:v040Dp3801d*dc*dsc*dp*ic*isc*ip*
alias: usb:v04CAp4605d*dc*dsc*dp*ic*isc*ip*
alias: usb:v13D3p3350d*dc*dsc*dp*ic*isc*ip*
alias: usb:v13D3p3349d*dc*dsc*dp*ic*isc*ip*
alias: usb:v13D3p3348d*dc*dsc*dp*ic*isc*ip*
alias: usb:v13D3p3346d*dc*dsc*dp*ic*isc*ip*
alias: usb:v13D3p3328d*dc*dsc*dp*ic*isc*ip*
alias: usb:v13D3p3327d*dc*dsc*dp*ic*isc*ip*
alias: usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*
alias: usb:v0846p9030d*dc*dsc*dp*ic*isc*ip*
alias: usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*
alias: usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*
depends: ath9k_hw,ath9k_common,mac80211,ath,cfg80211,compat
vermagic: 2.6.39.4 SMP mod_unload ELAN 
parm: debug:Debugging mask (uint)
parm: nohwcrypt:Disable hardware encryption (int)
 
root@bt:~/compat-wireless-2012-03-08# sudo modprobe ath9k_htc
FATAL: Error inserting ath9k_htc (/lib/modules/[2.6.39.4/updates/drivers/net/wireless/ath/ath9k/ath9k_htc.ko]("http://2.6.39.4/updates/drivers/net/wireless/ath/ath9k/ath9k_htc.ko")): Unknown symbol in module, or unknown parameter (see dmesg)

```
[FONT=Times New Roman][FONT=Verdana][SIZE=1]I cant seem to get my wireless working when I type ifconfig, iwconfig there is no wireless present.. [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=1]honestly I've tryed a lot of things with no success.. what am I doing wrong? if you require any other info. please let me know I'll gladly post it.. I'll be checking back on the forum every 30min or so. Thank you for your anwsers! [/SIZE][/FONT][/FONT]

---

### Post by praseodym on 2012-03-11
Try a later driver version after uninstalling the last one from compat-wireless:

```
sudo rm -r /lib/modules/$(uname -r)/updates/net/
sudo depmod -a
sudo update-initramfs -u
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.2/compat-wireless-3.2-rc1-1.tar.bz2
tar jxvf compat-wireless-3.2-rc1-1.tar.bz2
cd compat*
./scripts/driver-select atheros
make
sudo make install 
wget http://media.cdn.ubuntu-de.org/forum/attachments/44/10/2640681-15888a2-Atheros_Firmware.tar.gz
sudo tar xvf 2640681-15888a2-Atheros_Firmware.tar.gz -C /lib/firmware 
```

---

### Post by DaMn3d on 2012-03-11
> **praseodym said:**
> Try a later driver version after uninstalling the last one from compat-wireless:
 
```
sudo rm -r /lib/modules/$(uname -r)/updates/net/
sudo depmod -a
sudo update-initramfs -u
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.2/compat-wireless-3.2-rc1-1.tar.bz2
tar jxvf compat-wireless-3.2-rc1-1.tar.bz2
cd compat*
./scripts/driver-select atheros
make
sudo make install 
wget http://media.cdn.ubuntu-de.org/forum/attachments/44/10/2640681-15888a2-Atheros_Firmware.tar.gz
sudo tar xvf 2640681-15888a2-Atheros_Firmware.tar.gz -C /lib/firmware 
```
 
Ok I ran the code.. that make & install took 40min :s... but you sir are a genious :D :KS
it works I ran the code:
 
sudo modprobe ath9k_htc  
 
no errors 
 
I can see the the card in iwconfig but.. I cant see it in ifconfig or my wicd manager (it says no wireless networks found, though I think this is somewhat channel, frequency related)any tips on configurations to get it working properly? maybe a thread? 
 
And just one more question: Would this kind of installations stick if.. and when.. I update the backtrack kernel to newever versions? What should I be aware of?

---

### Post by DaMn3d on 2012-03-11
I'm am very greatful for your help sir, I'm realy a newbie & trying to make it work for 2 days now.. thank you so much!

---

### Post by praseodym on 2012-03-11
:popcorn:

Do not remove the folder, you need to compile again after a kernel upgrade. You should install the metapackage of the headers, too, for that, if you wish to use a regular kernel instead of 2.6.39 mainline.

---

### Post by DaMn3d on 2012-03-11
Heh I got it working.. I had it set on wireless interface: wlan0 when in fact it was wlan1 :> d0h.. so now it works like a charm :)!
 
Ok so 1x compile + get the right headers, build essentials :) will do that sir! I'll keep that in mind.. thought :> I think I wont upgrade to 3.6 :D maybe with a nother VMware image and play with the code a bit.. till I undestand the commands u just gave me.. honestly I've worked with windows issues for 10-15years but when I got to linux and the terminal usage 14 days ago.. I felt useless :).. whole new aspect of learning and doing things :)!  So thank you again.. honestly I doubt I would of found the correct mainline drivers :) even if I did I.. didnt know the cleanup commands :), but thanks to people like u I learn smthing new every day ^^! TY again! Cheers ^^!

---

### Post by praseodym on 2012-03-11
Reinstallation with

```
cd compat*
make clean
./scripts/driver-select restore 
./scripts/driver-select atheros
make
sudo make install 
```

---

### Post by DaMn3d on 2012-03-11
Tnx for the tip! Great help! :D

---

