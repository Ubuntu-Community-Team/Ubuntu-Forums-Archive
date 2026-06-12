---
title: "noob help w/ Linksys WMP54G v4.1"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by donteatsoap7 on 2010-05-30
I need to set up my wireless card and have tried ndiswrapper but I did something wrong at first or something, idk really. But I followed other threads until I found this one: [http://ubuntuforums.org/showthread.php?t=653179&highlight=WMP54G+Drive](http://ubuntuforums.org/showthread.php?t=653179&highlight=WMP54G+Drive)
I get the same outputs until "matt@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:66:FC:87
                    ESSID:"phi tau court"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-74 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000002b0da576567
          Cell 02 - Address: 9E:44:99:94:CF:5F
                    ESSID:"Free Public WiFi"
                    Mode:Ad-Hoc
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-62 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=0000000226ee4d46
          Cell 03 - Address: 00:14:6C:3F:95:DE
                    ESSID:"FONZARELLI"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-62 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000a386d268f8



I don't get that last part. I'm getting real frustrated because I don't remember it being this hard in the past. Could anyone help me out?

---

### Post by donteatsoap7 on 2010-05-30
bumpo

---

### Post by chili555 on 2010-05-30
I don't see what you think is wrong. It looks fine to me. Can you click the Network Manager icon, see your network and connect?

---

### Post by donteatsoap7 on 2010-05-31
No, when I type in that last code, I do not get that message. That was from another thread

---

### Post by chili555 on 2010-06-01
Let's troubleshoot. Please post:```
lsmod | grep -e ndis -e rt
ls /etc/modprobe.d | grep black
```Thanks.

---

### Post by donteatsoap7 on 2010-06-03
> **chili555 said:**
> Let's troubleshoot. Please post:```
lsmod | grep -e ndis -e rt
ls /etc/modprobe.d | grep black
```Thanks.


lsmod | grep -e ndis -e rt

rt61pci                20632  0 
crc_itu_t               1844  1 rt61pci
ndiswrapper           189868  0 
rt2x00pci               7892  1 rt61pci
rt2x00lib              29812  2 rt61pci,rt2x00pci
led_class               4088  1 rt2x00lib
input_polldev           3772  1 rt2x00lib
mac80211              183272  2 rt2x00pci,rt2x00lib
parport                35976  2 ppdev,lp
cfg80211               93508  2 rt2x00lib,mac80211
eeprom_93cx6            1908  1 rt61pci
agpgart                35440  2 intel_agp,nvidia



ls /etc/modprobe.d | grep black

blacklist
blacklist-ath_pci.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf

---

### Post by chili555 on 2010-06-03
You have *both* ndiswrapper and the native driver rt61pci loaded. Let's see how healthy your ndiswrapper installation is before we decide on a fix. Please post:```
ndiswrapper -l
cat /etc/modprobe.d/blacklist
```Thanks.

---

### Post by donteatsoap7 on 2010-06-05
> **chili555 said:**
> You have *both* ndiswrapper and the native driver rt61pci loaded. Let's see how healthy your ndiswrapper installation is before we decide on a fix. Please post:```
ndiswrapper -l
cat /etc/modprobe.d/blacklist
```Thanks.

Thank you :)

ndiswrapper -l


bcmwl5 : driver installed
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
rt61 : driver installed
	device (1814:0301) present (alternate driver: rt61pci)

cat /etc/modprobe.d/blacklist


blacklist bcm43xx
blacklist wl
blacklist rt2561
blacklist rt61

---

### Post by chili555 on 2010-06-05
Your ndiswrapper installation looks pretty solid. Let's do a few things and see if we can get the wireless going. Open a terminal and do:```
sudo su
rm /etc/modprobe.d/blacklist
echo "blacklist rt61pci" >> /etc/modprobe.d/blacklist.conf
reboot
```Now, how about the scanning?```
sudo iwlist wlan0 scan
```

---

### Post by donteatsoap7 on 2010-06-05
This is mine:

         Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:1C:10:B5:19:40
                    ESSID:"DRaZTiK"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:98/100  Signal level:-33 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:19:E4:8A:BA:99


Now how would I connect to it?

---

### Post by chili555 on 2010-06-05
> Now how would I connect to it?Click the Network Manager icon at the upper right and see your network, click 'Connect' and supply your WEP key and enjoy!

---

### Post by donteatsoap7 on 2010-06-15
> **chili555 said:**
> Click the Network Manager icon at the upper right and see your network, click 'Connect' and supply your WEP key and enjoy!

I have wicd installed and it doesn't show wireless networks

---

