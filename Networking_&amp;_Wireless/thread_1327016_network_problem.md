---
title: "network problem"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by retsel25 on 2009-11-15
Hello, i'm new here and new to linux ubuntu.  I purchased this awhile back as used.  Worked fine after starting the laptop.  Wireless was working fine.  I was surfing until an update was available, so I pushed update. After the update, it seems the network is disabled after I installed the update.  Now I can't go on-line.  Wireless network is disabled and I tried using the wired network with no success.

The wireless LAN communication indicator does not light up. How can I enable the wireless network, or turn on the the LAN communication indicator.

Acer, Aspire One, Intel Atom, Model:ZG5

---

### Post by Tsquad on 2009-11-15
not sure if this is the case for you but i know alot of the newer laptops have a little switch on them that will turn off the wireless adaptor and do exactly what your saying. Might want to check to see if yours has one that might have gotten turned off by accident.

---

### Post by retsel25 on 2009-11-15
thanks for that fast response.  Yes there is a switch on the front, and I tried turning it on, but it does not work. It worked Ok before the update.

I was thinking, maybe there is away I uninstalled, or disabled  it by accident with the update? I'm not sure.

---

### Post by Tsquad on 2009-11-15
yea im not sure, iv only been using ubuntu for 3-4 days now myself so im not much help.

---

### Post by hal10000 on 2009-11-15
> Yes there is a switch on the front, and I tried turning it on, but it does not work. It worked Ok before the update.
Is there a led indicating that wireless is turned on or off?
If the switch is turned to on and the light does'nt indicate that it's turned on, then you might have a hardware problem.
Turn the switch on, then reboot, open a terminal window and perform:
```
lspci
lsusb
```
Post the output of the commands so we can see if your wireless card is detected by ubuntu.
(You can mark the output with your mouse and paste it with the middle mouse button)

---

### Post by retsel25 on 2009-11-15
I'm not sure I did this right, but I ran those commands and here is what I got:

user@useraao:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
user@useraao:~$ lsusb
Bus 005 Device 002: ID 064e:d101 Suyin Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
user@useraao:~$

---

### Post by hal10000 on 2009-11-15
> 03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

This line indicates that your wireless card id recognized by ubuntu.

Now we should verify wether the driver is already loaded. On a terminal window perform:
```
lsmod | grep ath
```

if you get an answer,then your driver is loaded. If you get no answer, then we should try to load it manually. I'm not absolutely sure, but i think the driver for your card is called ath_pci, so do:
```
sudo modprobe ath_pci
```
Then do ```
lsmod | grep ath
``` again to see if it is loaded now.

Then do
```
sudo /etc/init.d/networking restart
```
and clock your network-manager icon. Look if your connection is activated (and if not, activate it)

Btw., removing the crappy network-manager and installing **wicd** instead can make your wireless much smoother.

[EDIT]
if you still have problems, maybe [this thread]("http://ubuntuforums.org/showthread.php?t=902860") can help you out.

---

### Post by retsel25 on 2009-11-15
Here is what I got:

ath5k     97412  0
mac80211  171352 1 ath5k
led_class 3676   2 ath5k, acer_wmi
cfg80211  32184  2 ath5k, mac80211

---

### Post by hal10000 on 2009-11-15
I'm not sure if the ath5k driver is the correvt one for your card.
The **modinfo** command
```
modinfo ath5k
```
says this is the driver for atheros 802.11 wireless LAN cards **5xxx series**
If your card is activated in your network manager and you are sure you have made the correct settings (essid, wireless-key, encryption, ip-address, gateway, DNS), but you can't get connected, then try to unload the ath5k driver:
```
sudo rmmod ath5k
```
and load the ath_pci driver:
```
sudo modprobe ath_pci
```
Then restart your network:
```
sudo /etc/init.d/networking restart
```
and see if it works.

p.s: you should really replace network-manager with wicd

---

### Post by retsel25 on 2009-11-15
here's what I found. If I have to, how do I  replace the network-manager with wicd?

user@useraao:~$ modinfo ath5k
filename:       /lib/modules/2.6.29-1-netbook/kernel/drivers/net/wireless/ath5k/ath5k.ko
version:        0.6.0 (EXPERIMENTAL)
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     EDDF16DABDC8BF0FD5DD1BF
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        led-class,cfg80211,mac80211
vermagic:       2.6.29-1-netbook SMP mod_unload modversions 586 
parm:           nohwcrypt:Disable hardware encryption. (int)
user@useraao:~$ sudo rmmod ath5k
ERROR: Module ath5k does not exist in /proc/modules
user@useraao:~$ sudo modprobe ath_pci
FATAL: Module ath_pci not found.
user@useraao:~$

---

### Post by hal10000 on 2009-11-15
> user@useraao:~$ sudo rmmod ath5k
ERROR: Module ath5k does not exist in /proc/modules
user@useraao:~$ sudo modprobe ath_pci
FATAL: Module ath_pci not found.
This error messages are strange, because (at least the ath5k) the module acually is loaded, which it could not be according to the error message.
You should rebuild the modules dependencies with
```
sudo depmod -a
```

and try to do the upper steps again.

---

### Post by retsel25 on 2009-11-15
user@useraao:~$ sudo depmod -a
[sudo] password for user: 
user@useraao:~$ sudo rmmod ath5k
user@useraao:~$ sudo modprobe ath_pci
FATAL: Module ath_pci not found.
user@useraao:~$

---

