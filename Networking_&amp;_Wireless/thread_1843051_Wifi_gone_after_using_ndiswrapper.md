---
title: "Wifi gone after using ndiswrapper"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by Adromir on 2011-09-12
Hello,
i had troubles with the wireless on my eee-PC 701. Although i have a rather good signal strength (using a Router+Repeater), my internet connection was really, really slow and often disconnected. So i tried using the windows drivers for my wireless device via ndiswrapper, but it didnt helped either. 

After uninstalling the Windows Drivers, my wireless isnt recognized any more at all. Even iwconfig tells me, that i dont have any wireless adapters.

I seem to be to stupid to find a solution for it.

thanks for your help

---

### Post by as2000 on 2011-09-13
You are not stupid my friend.

I had the same issues as you because the wireless card Asus uses is not the best. I simply bought a wireless card made by Intel and dropped it into my Eee and no longer had to worry about the wrapper. Ubuntu has native support for those cards. New Egg sells them. Just do a search for mini PCI express and you will find them. You may also try Ebay, but it can be risky.

---

### Post by praseodym on 2011-09-13
Please show:

```
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by Adromir on 2011-09-14
```
lspci -nnk | grep -iA2 net
```
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

```
lsusb
```
No ethernet devices listed
```
iwconfig
```
lo no wireless extensiom
eth0 no wireless extension

```
rfkill list
```
0: eeepc-wlan Wireless LAN
Soft blocked: no
hard blocked: no
```
sudo iwlist scan
```
lo Interface doesnt suppurt scanning
eth0 Interface doesnt support scanning


thanks much for your helps

---

### Post by praseodym on 2011-09-14
You dont need ndiswrapper for this device, remove it and load the driver you need:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo modprobe -v ath5k
sudo service network-manager restart
```
Check:

```
iwconfig
sudo iwlist scan
dmesg | egrep 'ath|ndis'
lsmod
grep ath5k /etc/modprobe.d/*
cat /etc/modules
```

---

### Post by Adromir on 2011-09-14
Thanks, that really helped, wireless is now working again. I just hope its working a bit faster now, without the constant timeouts..

---

### Post by praseodym on 2011-09-14
I recommend WPA2-AES (CCMP) encryption, the network-manager often has problems with mixed exryption.

---

### Post by Adromir on 2011-09-14
thanks for the Advice, i will try that

---

### Post by Adromir on 2011-09-16
Mmh i am really considering switching to windows again :( Today my Wifi doesnt connect at all again (although having max. signal strength). I even tested it with an usb wireless stick, but couldnt connect with it either..

---

### Post by praseodym on 2011-09-16
Please show the outpus of my first posting again, plus

dmesg | egrep 'ath|ndis'

---

### Post by Adromir on 2011-09-27
Hi, sorry i didnt react earlier, but i was on a 8 nights nightshift. 
I really get frustrated in the moment, because its only a case of luck, if my Wifi is working or not. One time i switch on my netbook and Wifi works, next time it doesnt. The only safe way to have it working is plugging in my Smartphone and using its tethering option...

---

