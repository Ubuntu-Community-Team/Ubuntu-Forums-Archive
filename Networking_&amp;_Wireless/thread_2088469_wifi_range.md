---
title: "wifi range"
date: 2012-11-26
forum: Networking &amp; Wireless
---

### Post by mondom on 2012-11-26
hello 
i've got a pavillion g6 with ubuntu 12.04 and i solved my wifi problems with this solution suggest by Wild man (great man!):
> sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms patch fakeroot unzip
wget [http://media.cdn.ubuntu-de.org/forum/attachments/35/07/3208747-angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip](http://media.cdn.ubuntu-de.org/forum/attachments/35/07/3208747-angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip)
unzip angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/
sudo make
sudo make install
sudo modprobe -v rt5390sta
sudo depmod -a
sudo update-initramfs -uand
> echo "options rt2800pci  nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pcibut the wifi connection works only when i stay close to the router (2 o 3 meters max), when i go in another room the connection fall down and don't reconnect.
it's not an hardware deficit because with win7 the connection is stable in every room of my house.
there is some configuration to solve this problem?

---

### Post by Shuudoushi on 2012-11-26
This may be do to your settings on Ubuntu. make sure you have hooked into the main wifi and not the guest wifi. I have the same issue when i hook into my guest access point.

---

### Post by Shuudoushi on 2012-11-26
Also make sure you have the latest drivers for your wireless card!

---

### Post by mondom on 2012-11-28
> This may be do to your settings on Ubuntu. make sure you have hooked  into the main wifi and not the guest wifi. I have the same issue when i  hook into my guest access point. 

i don't know how i can check if i have hooked into the main wifi...pleae, can you tell me some clue?

> Also make sure you have the latest drivers for your wireless card! 	

i've installed the wifi driver with the help of Wild Man, but i've got not idea if they are the latest and I don't know where he find it

---

### Post by Shuudoushi on 2012-11-28
> **mondom said:**
> i don't know how i can check if i have hooked into the main wifi...pleae, can you tell me some clue?



i've installed the wifi driver with the help of Wild Man, but i've got not idea if they are the latest and I don't know where he find it

The vendor web-site for your wireless card should have the latest drivers (Unless it's and older model card.). When you look at your connection manager it should say if you are hooked into the guest (modem-model.guest) or the main (modem-model). If you can tell us what modem you have I may be able to narrow it down more for you.

---

### Post by mondom on 2012-11-29
my modem/router is a Digicom Michelangelo wave 300c

my wireless card is Ralink corp. Device 539a
i've tried to install the driver downloaded from their main site, but without success
so Wild man suggest me to install this
angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO

---

### Post by mondom on 2012-11-30
i found myself the answer
open the terminal and digit
> sudo iwconfig wlan0 power offI don't know what I have done, but it works!
now i type from my pavillion g6 in wifi from another room
I hope it's helpful to the people with the same problem

tanks anyway to shuudoushi!

---

