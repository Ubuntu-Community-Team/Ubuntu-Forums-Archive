---
title: "Pentagram Hornet P 6121-L7 drivers"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by robson22 on 2011-01-26
Welcom. 
First thing is sorry about my english.

I buy wifi(pci) card Pentagram Hornet P 6121-L7 but i cant find drivers, they are only drivers for windows (here [HTML]http://download.pentagram.eu/pl/sterowniki/karty_sieciowe/hornet_wifi_n/horNET_802.11n_WIFI_PCI_P6121_L7_Win2K_XP_Vista_7.zip[/HTML])

I cant use ndiswrapper becouse in this drivers is not .inf file is only setup.exe file.

Please help me how i can install this drivers in ubuntu 10.04 or mayby where are drivers for linux?

best regards

---

### Post by chili555 on 2011-01-26
The first step in finding Linux drivers is to know what you have. Please open a terminal and run and post:```
lspci -nn
```Feel free to strip away everything that's not the wireless card.

---

### Post by robson22 on 2011-01-26
ok result lspci -nn is
```
01:07.0 Network controller [0280]: RaLink Device [1814:3060]
```
and what next?

Edit.

Ok I try this advice:
> Ouch! This is actually driven by the often lousy rt2800pci. It's better to get this driver: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Get the driver marked RT3062PCI/etc. Download it to your desktop. Open System > Administration Synaptic and make sure the packages build-essential and kernel-headers-generic are installed.

Now open a terminal and do:cd Desktop
tar -xvf 2010_07_16_RT3062_Linux_STA_v2.4.0.0.tar.bz2
cd 2010_07_16_RT3062_Linux_STA_v2.4.0.0
make
sudo make installNow do the blacklists described here: [http://ubuntuforums.org/showpost.php?p=10071183&postcount=19](http://ubuntuforums.org/showpost.php?p=10071183&postcount=19)

Now do:sudo su
echo rt3562sta >> /etc/modules
exitReboot and tell us if your wireless is working.

and now result iwconfig is:
> ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


but why "Bit rate" is 1Mb/s, card is 802.11n then must be 150Mb/s, im allready try iwconfig ra0 rate 150M,
but nothing change.

Please help

---

### Post by chili555 on 2011-01-26
This is your exact device. Please do: [http://ubuntuforums.org/showpost.php?p=10082871&postcount=7](http://ubuntuforums.org/showpost.php?p=10082871&postcount=7)

You will also need to get an ethernet connection and do:```
sudo apt-get install build-essential linux-headers-generic
```

---

### Post by robson22 on 2011-01-27
Ok drivers are installed, but i cant card configuration i try "Iwconfig", "iwpriv" and Configuration File : RT2860STA.dat, but nothings change, always result of iwconfig is:
```
ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

where is a problem??

---

### Post by chili555 on 2011-01-27
Please reboot with any ethernet cables detached and let's ask the computer what the problem is:```
dmesg | grep -e rt3 -e ra0
dmesg | grep -i rt2
```Thanks.

---

### Post by robson22 on 2011-01-27
result of "dmesg | grep -e rt3 -e ra0" is
```
[   19.160766] The name of the new ra interface is ra0...
[   30.776026] ra0: no IPv6 routers present
```
result of "dmesg | grep -i rt2" is
```
[   19.159593] ===> rt2860_probe
[   19.159839] rt2860 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, high) -> IRQ 16
[   19.273685] @rt2860_probe MAC address: 00:06:4f:97:7f:15
[   19.273687] <=== rt2860_probe
[   19.687237] <==== rt28xx_init, Status=0

```

and what next?

Please help

---

### Post by chili555 on 2011-01-27
> [COLOR="Red"][COLOR="Red"]rt2860[/COLOR][/COLOR] 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, high) -> IRQ 16Not sure I like that. I thought the module we built was rt3562sta. Let's have a look at:```
lsmod | grep -e rt2 -e rt3
```We may need to fine-tune our blacklist.

---

### Post by robson22 on 2011-01-28
result of "lsmod | grep -e rt2 -e rt3" is
```
rt3562sta             908495  1 
```

How i must tune blacklist becouse im allready do something like that```
blacklist rt2800pci
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2800lib

blacklist rt3562pci
blacklist rt3x62lib
blacklist rt3x62pci
blacklist rt3562lib
```

and nothing change.

---

### Post by chili555 on 2011-01-28
> blacklist rt3562pci
blacklist rt3x62lib
blacklist rt3x62pci
blacklist rt3562libThere are no such drivers so it doesn't help anything to blacklist what doesn't exist. However, it also probably doesn't hurt. If you want to be correct, remove those lines. The rt2800 and rt2x00 lines are perfectly correct. I'd like to take a look at your entire dmesg after a fresh boot. Please detach any ethernet cables and reboot. Then do:```
dmesg > robson.txt
lsmod >> robson.txt
iwconfig >> robson.txt
sudo iwlist ra0 scan >> robson.txt
zip robson.zip robson.txt
```In your user directory, you will find a file robson.zip. Please attach it to your reply using the little paperclip at the top of the reply box.

---

### Post by robson22 on 2011-01-28
there is file:

---

