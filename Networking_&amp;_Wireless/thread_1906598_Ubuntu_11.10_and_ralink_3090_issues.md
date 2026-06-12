---
title: "Ubuntu 11.10 and ralink 3090 issues"
date: 2012-01-09
forum: Networking &amp; Wireless
---

### Post by susan :) on 2012-01-09
I'm having some trouble enabling my wireless - RT3090 on 11.10. I recently installed 11.10 hoping it would fix my internet.

 network-manager says my wireless is disabled, I click  "enable wireless", and, it doesn't enable it. I have  checked my wireless antenna on/off hardware switch - it is on. I have  tried "fn-f5" software switch, this doesn't enable it.

sami@sami-lenovo:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]

sami@sami-lenovo:~$ lsmod | grep -e rt3 -e rt2
rt3090sta             794403  0 

sami@sami-lenovo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA

---

### Post by chili555 on 2012-01-09
What does this tell us?```
rfkill list all
```

---

### Post by susan :) on 2012-01-09
rfkill list all says
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

---

### Post by susan :) on 2012-01-09
I also added this to /etc/modprobe.d/blacklist.conf:

blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
blacklist rt2860

---

### Post by chili555 on 2012-01-09
**acer**-wireless in a Lenovo, eh? Just as the doctor suspected. Please try:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```Did your wireless spring to life? If so, let's blacklist acer-wmi:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by susan :) on 2012-01-09
Yes! it sure did. We got lucky - sudo rfkill unblock all would freeze the computer in 11.04. 11.10 is treating me well.

Now though "Connect" is grayed out in the authentication block, so I can't enter passwords for wireless networks... is this a wpa_supplicant configuration issue?

---

### Post by chili555 on 2012-01-09
Let's get a clean slate and reboot. Now are networks listed? Can you connect? Does it scan? ```
sudo iwlist ra0 scan
```If no, then tell me if you edited config.mk to use Network Manager before you compiled rt3090sta. Yes, no...maybe??> We got lucky I *do* get lucky once in a while.

---

### Post by susan :) on 2012-01-09
mmm, not sure whether I changed the config.mk file. After I upgraded to 11.10, my co-worker went-to-town trying to fix it, and he either installed the driver again with the package manager or installed a patch. If he just installed a patch on the driver I had for 11.04, then WPA_SUPPLICANT and NATIVE should set to Y bc I made sure when I installed it then. If he installed the driver because it was deleted after the upgrade, then I have no clue. How would I check?

Scan completed :
          Cell 01 - Address: 58:6D:8F:22:E5:9A
                    Protocol:802.11b/g/n
                    ESSID:"RedCheetah1"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:100/100  Signal level:-41 dBm  Noise level:-92 dBm
                    Encryption keyn
                    Bit Rates:144 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A0001101044000102104700104DBEFCEC10D0DDEC283F22A83DBF73FB103C000103
          Cell 02 - Address: 00:24:A8:C0:F0:60
                    Protocol:802.11b/g
                    ESSID:"LE-AUS"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:42/100  Signal level:-73 dBm  Noise level:-68 dBm
                    Encryption keyn
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:20:A6:7A:FF:E5
                    Protocol:802.11b/g
                    ESSID:"SIMON WiFi"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:37/100  Signal level:-75 dBm  Noise level:-70 dBm
                    Encryption keyff
                    Bit Rates:54 Mb/s
          Cell 04 - Address: 00:1C:10:1B:49:74
                    Protocol:802.11b/g
                    ESSID:"wifi@right"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:37/100  Signal level:-75 dBm  Noise level:-70 dBm
                    Encryption keyn
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:14:1C:F1:25:C0
                    Protocol:802.11b/g
                    ESSID:"CBUNNW1"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:18/100  Signal level:-83 dBm  Noise level:-78 dBm
                    Encryption keyn
                    Bit Rates:54 Mb/s
          Cell 06 - Address: 00:07:7D:AE:48:40
                    Protocol:802.11b/g/n
                    ESSID:"NAVITUS"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:2/100  Signal level:-89 dBm  Noise level:-84 dBm
                    Encryption keyn
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: 58:6D:8F:22:E5:A4
                    Protocol:802.11b/g/n
                    ESSID:"RedCheetah2"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:78/100  Signal level:-59 dBm  Noise level:-92 dBm
                    Encryption keyn
                    Bit Rates:144 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000110104400010210470010AFA7EEBF8C61BF3AF1508805598133F8103C000103
          Cell 08 - Address: 00:26:F3:E8:71:7B
                    Protocol:802.11b/g
                    ESSID:"SMC8014WG-TWC79"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-80 dBm
                    Encryption keyn
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: E0:46:9A:51:78:8C
                    Protocol:802.11b/g/n
                    ESSID:"Lattice1"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-82 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    IE: Unknown: DD270050F204104A00011010440001021047001000000000000010000000E0469A51788C103C000103
          Cell 10 - Address: DA:33:84:1C:0E:9E
                    Protocol:802.11b
                    ESSID:"Free Public WiFi"
                    Mode:Ad-Hoc
                    Frequency:2.462 GHz (Channel 11)
                    Quality:13/100  Signal level:-85 dBm  Noise level:-86 dBm
                    Encryption keyff
                    Bit Rates:11 Mb/s
          Cell 11 - Address: 00:20:A6:7A:FE:9B
                    Protocol:802.11b/g
                    ESSID:"SIMON WiFi"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-82 dBm
                    Encryption keyff
                    Bit Rates:54 Mb/s
          Cell 12 - Address: 00:0D:67:09:B2:30
                    Protocol:802.11b/g
                    ESSID:"24-c"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:13/100  Signal level:-85 dBm  Noise level:-86 dBm
                    Encryption keyn
                    Bit Rates:54 Mb/s
          Cell 13 - Address: 00:24:6C:0C:F8:C0
                    Protocol:802.11b/g/n
                    ESSID:""
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-49 dBm  Noise level:-92 dBm
                    Encryption keyn
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 14 - Address: 00:24:6C:0C:F8:C1
                    Protocol:802.11b/g/n
                    ESSID:""
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:94/100  Signal level:-53 dBm  Noise level:-92 dBm
                    Encryption keyff
                    Bit Rates:54 Mb/s

---

### Post by chili555 on 2012-01-09
> WPA_SUPPLICANT and NATIVE should set to Y bc I made sure when I installed it then. If he installed the driver because it was deleted after the upgrade, then I have no clue. How would I check?Is the file still on your desktop or in Downloads? Go check the file; it's in os > linux. Are those two lines set to =y? If not, we'll do a quick re-compile.

Man! It scans great! But are there no networks shown when you click the Network Manager icon?> ESSID:"RedCheetah1"
Mode:Managed
Frequency:2.412 GHz (Channel 1)
[COLOR="Red"]Quality:100/100[/COLOR] Signal level:-41 dBm Noise level:-92 dBmI assume this is your network.

---

### Post by susan :) on 2012-01-09
Sounds weird, but everything started working when I got home. Thank you for your help!! I really appreciate it!

---

### Post by chili555 on 2012-01-09
I've seen wierder! I'm glad it's working.

---

### Post by hugoop on 2012-01-10
I've tried another Ubuntu forum, with no success. But I think someone can help me! 


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



lsmod | grep -e rt
parport_pc             36962  0 
parport                46562  3 parport_pc,ppdev,lp


lspci -nn | grep 802
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]


rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


What do I have to do?

---

### Post by chili555 on 2012-01-12
> **hugoop said:**
> I've tried another Ubuntu forum, with no success. But I think someone can help me! 


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



lsmod | grep -e rt
parport_pc             36962  0 
parport                46562  3 parport_pc,ppdev,lp


lspci -nn | grep 802
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]


rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


What do I have to do?In Ubuntu 11.10, your device ought to work with rt2800pci out of the box. Please try:```
sudo modprobe rt2800pci
dmesg | grep rt2
```Please post the results.

---

### Post by hugoop on 2012-01-15
> **chili555 said:**
> In Ubuntu 11.10, your device ought to work with rt2800pci out of the box. Please try:```
sudo modprobe rt2800pci
dmesg | grep rt2
```Please post the results.


sudo modprobe rt2800pci
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

 dmesg | grep rt2
[ 2970.506745] rt2800pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2970.506764] rt2800pci 0000:02:00.0: setting latency timer to 64
[ 2970.541441] Registered led device: rt2800pci-phy0::radio
[ 2970.541490] Registered led device: rt2800pci-phy0::assoc
[ 2970.541546] Registered led device: rt2800pci-phy0::quality
[ 2970.649213] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware


thanks a lot!!!

---

### Post by chili555 on 2012-01-16
Let's try a newer firmware package. First, move the old firmware aside and back it up:```
sudo mv /lib/firmware/rt2860.bin /lib/firmware/rt2860.bak
```Now download the attached package to your desktop. Right-click it and select Extract Here. Now do:```
cd Desktop/RT2860_Firmware_V26
sudo cp rt2860.bin /lib/firmware
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci
dmesg | grep rt2
```Now have we cured this error?> phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardwareDoes it connect?

---

