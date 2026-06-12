---
title: "Can't connect to my wireless network"
date: 2013-08-04
forum: Networking &amp; Wireless
---

### Post by JLeite on 2013-08-04
Greetings,
I've just bought a new laptop and installed Ubuntu 12.04 in it.
My problem is that I can make a wired connection but not a wireless one.
The wireless network is working ok with other computers but not with the new one.
The new laptop can't detect it.
Can anyone help me?
Thank you

---

### Post by ibjsb4 on 2013-08-04
Sounds like you need drivers, but can't tell you what drivers since you didn't post what kind of wireless you have.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=wireless+drivers&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=wireless+drivers&sa=Search&cof=FORID:9)

---

### Post by JLeite on 2013-08-04
On a terminal, typing lspci the output is 
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)

Inspecting the drivers installed the one for the Network controller: Realtek Semiconductor Co., Ltd. Device 8723 is not there. How do I do for install it?

---

### Post by wildmanne39 on 2013-08-04
*Thread moved to **Networking & Wireless**.*

---

### Post by wildmanne39 on 2013-08-04
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz or netinfo.txt in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz or netinfo.txt file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by JLeite on 2013-08-04
Thank you for your reply.

---

### Post by wildmanne39 on 2013-08-04
Please do ```
sudo modprobe rtl8723ae
```
Then
```
modinfo rtl8723ae
dmesg | grep rtl
```
and post the results here.
Thanks

---

### Post by JLeite on 2013-08-05
On a terminal I've typed 
sudo modprobe rtl8723ae
and the output was:
FATAL: Module rtl8723ae not found.

---

### Post by wildmanne39 on 2013-08-05
I am looking into this, I have been away from my computer, I am checking to see if the driver exixts with your kernel version which I believe the answer is no, but I will get back to you soon.

---

### Post by wildmanne39 on 2013-08-05
Okay you will have to compile the driver, here are the directions.
```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms
sudo su
wget -O- http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz | tar -xz
cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
make
sudo make install
sudo modprobe rtl8723e
```

When there is an update to the kernel you will have to do:
```
sudo su
make clean
make
make install
modprobe rtl8723e
```
Thanks

---

### Post by JLeite on 2013-08-06
Every thing was going Ok until I typed make (the first one).
The output was:
make -C /lib/modules/3.5.0-38-generic/build M=/home/jleite/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-38-generic'
  CC [M]  /home/jleite/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/jleite/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#8216;_rtl_init_mac80211&#8217;:
/home/jleite/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: &#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared (first use in this function)
/home/jleite/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/jleite/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/jleite/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-38-generic'
make: *** [all] Error 2

---

### Post by wildmanne39 on 2013-08-06
Okay that driver is the problem, I have found two newer one's and both make fine on my system with no errors or warnings.

Please do:
```
sudo su
make clean
```
Then download the driver:
[https://dl.dropbox.com/u/58267392/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz](https://dl.dropbox.com/u/58267392/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz)
Move the driver to the desktop, right click on it and select extract here.
cd Desktop
```
sudo su
make
sudo make install
sudo modprobe rtl8723e
exit
```
Thanks

---

### Post by felichas on 2013-08-06
Wild Man, why would you want that *`sudo su`* before *make*?
can't you *make* as an unprivileged user? You still need *sudo* to *make install* and to *modprobe*, of course.
Plus, if your ar root you never need to *sudo* at all.
Following my thinking, that final *exit* is not needed if you don't *`sudo su`* before.

---

### Post by JLeite on 2013-08-06
You've done it Wild Man.
Thank you.

---

### Post by wildmanne39 on 2013-08-06
Hi, glad it is working! a big thanks to chili555 for having posted the driver.:)

---

