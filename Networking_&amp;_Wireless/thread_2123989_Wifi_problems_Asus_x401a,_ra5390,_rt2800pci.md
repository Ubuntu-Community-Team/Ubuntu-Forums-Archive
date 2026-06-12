---
title: "Wifi problems: Asus x401a, ra5390, rt2800pci"
date: 2013-03-09
forum: Networking &amp; Wireless
---

### Post by BeardedOne on 2013-03-09
I need help with my wireless connection after my new install of Mint 14 64bit.

Here's my set up:
Asus x401a
Mint 14-64 updated
Ralink 5390
driver rt2800pci
positioned < 8 ft from router

Symptoms:
1. sees my router and neighbors
2. sees my router after startup at 72%, hp next to it shows 98%
3. tries to autoconnect, fails, asks for password, fails, etc. - may repeat endlessly
4. occasionally connects - loads slowly, shows 65% power, then 42%, then 25%, begins to ask for password again, endless repeat
5. hp laptop next to Asus is stable & downloading quickly on same router
6. wired connection is stable
7. no other problems with the install so far

What I've tried:
1. double checked password
2. rebooted router
3. tried 32bit live cd Mint 14
4. tried suggestions from "Ralink 5390 / Compaq persario..." in Networking & Wireless forum to download & install rt2860 driver, that gave better power readings but goes into kernel panic under load - clean re-install afterwards
5. tried OpenSuse 64 which gave higher power readings and more stability, but cuts out at more than 12 ft from router

Using commands from other threads my output is:

bill@Liveoak ~ $ lspci -nn | grep 0280 
02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390] 

bill@Liveoak ~ $ lsmod | grep rt2 
rt2800pci              18528  0 
rt2800lib              58685  1 rt2800pci 
crc_ccitt              12667  1 rt2800lib 
rt2x00pci              14475  1 rt2800pci 
rt2x00lib              54891  3 rt2800pci,rt2800lib,rt2x00pci 
mac80211              539908  3 rt2800lib,rt2x00pci,rt2x00lib 
cfg80211              206566  2 rt2x00lib,mac80211 
eeprom_93cx6           13302  1 rt2800pci 

I'm a regular Linux user, but don't know how to work under the hood. It's more 'monkey see, monkey do'.

Thanks for your help.

---

### Post by chili555 on 2013-03-09
The driver rt2800pci is tricky. The first fix I'd try is in the router. Open the administration pages and change the encryption mode to WPA2 only; many routers offer a WPA and WPA2 mixed mode and many Linux drivers are confused by it.

Next, I'd turn off N speeds. Please see attached. In this example I'd set 802.11-n-mode to OFF. Some other routers offer a choice between 802.11B and G or 802.11B, G and N. We'd love to try B and G only.

Next, I'd temporarily hook up an ethernet cable and install the latest rt2800pci module:```
sudo apt-get install linux-backports-modules-cw-quantal-generic
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci
```Last, you might try a temporary driver parameter:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```It would be helpful to try and report on one at a time so that all of us, including the searchers, learn the shortcut.

---

### Post by BeardedOne on 2013-03-09
Tried the update and got

bill@Liveoak ~ $ sudo apt-get install linux-backports-modules-cw-quantal-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-cw-quantal-generic

---

### Post by BeardedOne on 2013-03-09
Set router to b/g only
Set router to WPA2/PSK only

---

### Post by BeardedOne on 2013-03-09
Tried:
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y

wifi shows 65% (down from 75%), can't connect, asks for password, repeats

---

### Post by BeardedOne on 2013-03-09
Oops, forgot to reboot the router.

Rebooted router, settings taking effect.

wifi shows 61% and is stable

Let's see if this works longterm. It's connected before only to drop out later.

---

### Post by BeardedOne on 2013-03-09
wifi continues to be stable at ~60%. I'll go grab some lunch and see if it holds.

Thanks for your help. I'll let you know how it works out.

---

### Post by fiodev on 2013-03-09
apt-get install wicd

---

### Post by chili555 on 2013-03-09
> **fiodev said:**
> apt-get install wicdIn my opinion, absolutely not. YMMV.

---

### Post by BeardedOne on 2013-03-09
OK, I'm back with the burgers and wifi is still up, showing 67%, and appears stable after more than 30 minutes (a new record). Just ran Youtube so load isn't a problem.

Let's try to figure out what the fix actually was. 
The driver update looked like it didn't go through, so that wasn't it. (Thought I'd love to have the latest driver.)
The parameter commands didn't change the symptoms, so that wasn't it. At least not by itself.
The change seems to have occured after I set the router to b/g only and WPA2/PSK only.

A further problem: This is a laptop. What happens when I take this to work and want to turn off everyone's n speed? (I'm already the weird guy that uses Linux. I really don't want to hear about how this wouldn't be a problem if I was using Windows). Is there a way to set my wifi to only use b/g and WPA2, whether the router is set that way or not?

Thanks.

---

### Post by BeardedOne on 2013-03-09
Just turned off b/g only and set router to b/g/n mixed. My connection dropped immediately. Returned it to b/g only and it connected at 65% and appears stable.

---

### Post by BeardedOne on 2013-03-09
My connection is stable at 65% for over 2 hours now. I think we can call it fixed.
Thanks chili555. You have really saved the day on this one. 

The key seems to be that there is a problem handling b/g/n mixed parameters on a router. Once my router was forced to use b/g only I can get a good connection. 


Is there any way to set the driver to only work at g speed even if the router has n? That would make work and public routers available to this laptop.

---

### Post by chili555 on 2013-03-09
> Is there any way to set the driver to only work at g speed even if the router has n? Some drivers support this but I haven't yet found it for rt2800pci. Still looking.

---

### Post by BeardedOne on 2013-03-09
Thanks chili555. You've been great. There is no support anywhere else that's nearly as good.
Let me know if you find a way to make force rt2800pci into line

---

### Post by mattcsl on 2014-01-09
super big pain in the ass but this 200 dollar laptop flies with a kind of old vertex2 ssd

the wireless absolutely sucked till I got the driver from ralink... there is some retarded file
2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2.bz2.bz2 that you have to search forever to find

then I think you tar -xvf that

then find this file
rt5592sta_fix_64bit_3.8.patch

and put that in the root of the extracted folder

then you 
patch -p1 < rt5592sta_fix_64bit_3.8.patch

then also in the extracted folder
edit os/linux/config.mk and find the line below and make sure it looks like that
 HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

then
sudo make
sudo make install

then add these lines to the bottom of /etc/modprobe.d/blacklist.conf
#asus wireless... do sudo modprobe rt5390sta
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta

then restart... and after you are done with all that your wireless will not disconnect anymore BUT IT WILL BE SLOW AS **** if you have the router i have or something like it... dual band 1200ac linksys. So you need to go into your router and look in the wireless settings on the 24ghz band... look for something like "channel width". Change it from auto to 20mhz only. Once I did this I have a full strength connection and I can scp files at around 7 megs/sec... it used to go at around 800k

I attached the driver source with the patch and config.mk already done. 

Good luck

---

