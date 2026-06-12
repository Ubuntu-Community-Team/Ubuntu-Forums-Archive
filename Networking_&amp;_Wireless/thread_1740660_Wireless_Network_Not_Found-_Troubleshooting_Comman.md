---
title: "Wireless Network Not Found- Troubleshooting Commands Not Helping"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by Rych on 2011-04-27
So there is no wireless network showing up for me to connect to, and thus I have no internet on my laptop which is kind of redundant.

So I hit up this troubleshooting "Official Ubuntu Document" that instructed me to type in a few commands to make sure I had the correct driver installed. Makes sense.

Only the commands were not found and I was totally unable to follow any of the directions according to the actual documentation. 

Still no wireless networks showing up for me to connect to, and I'm sitting next to the router. 

Worst of all my husband has Windows installed on a partition with the laptop and it crashes every 5 minutes, so I really want to get ubuntu online so I can tell him to STFU and use an OS that WORKS. 

He thinks windows will run better if we take off world of warcraft and other games we don't use...*Sigh* and *pause* for ignorant windows users in respect for their unfortunate disposition of being mislead into the world of Microsoft, please help.

Thanks


Here is the documentation I used that did NOT work
[https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html)

---

### Post by chili555 on 2011-04-27
That's a pretty solid troubleshooting document. Let's try again. Please try the commands again and either copy and paste the output to a text document and transfer it on a USB key so you can post it here or, worst case, jot it down with a pencil and post it here.

In the commands lshw and lspci, be sure the first character is L and not one. lshw means *list hardware*; lspci means *list the pci devices*. Feel free to omit all the non-wireless lines.

---

### Post by Rych on 2011-04-27
Yes! The font did mislead me into typing 1 instead of L, Thank You, Trying it now!

Here is my output from the first part of the troubleshooting page. So I'm lost now, guide me oh wise ubuntu users with far greater experience and knowledge than I!

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)

---

### Post by chili555 on 2011-04-27
I think your device is supposed to work with the module r8187se. Let's load it and cross our fingers:```
sudo modprobe r8187se
iwconfig
```Now do you have a wireless interface, wlan0 perhaps? Can you connect? If not, please run and post:```
dmesg | grep 8187
lspci -nn | grep -i 10ec
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by Rych on 2011-04-27
bastarache@bastarache-U90-U100:~$ sudo modprobe r8187se
[sudo] password for bastarache: 
bastarache@bastarache-U90-U100:~$ dmesg | grep 8187
[   12.322090] r8187se: module is from the staging directory, the quality is unknown, you have been warned.
[   12.372443] r8180: MAC controller is a RTL8187SE b/g
bastarache@bastarache-U90-U100:~$ lspci -nn | grep -i 10ec
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)

---

### Post by chili555 on 2011-04-27
Looks great so far. How about:```
iwconfig
```Do you have a wireless interface, wlan0 perhaps? Can you click the Network Manager icon and connect?

What brand and model laptop is it? Please show us:```
rfkill list all
```We're getting there.

---

