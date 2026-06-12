---
title: "pcmcia SMC madwifi problem"
date: 2005-12-25
forum: Networking &amp; Wireless
---

### Post by PeRy_SoY on 2005-12-25
hi! i am spanish user and y bought a PCMCIA SMCWCBT-G EU whose chipset is Atheros, I have installed madwifi deb correcty but when i put:
     
iwlist ath0 scan
ath0      Failed to read scan data : Resource temporarily unavailable

but KWifiManager scan correctly.

my lspci

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 11)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:09.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:00:09.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
0000:02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)


my iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11b  ESSID:"Wifi"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



thnx 4 help!!

byyeS!!

---

### Post by firecat53 on 2005-12-25
Try 'sudo iwlist scan'.  Other than just the plain iwconfig or ifconfig to list your connections, all the manipulations (including scanning) of the network interfaces have to use sudo.

Good luck!
Scott

---

### Post by PeRy_SoY on 2005-12-26
when i put sudo iwconfig ath0 mode master or monitor i havent got problems but when the mode is managed the erro come back appear...

thx 4 help!

byeS!

---

### Post by firecat53 on 2005-12-27
I'm not familiar with your particular card, but sometimes compiling the drivers from source will get things working for you. I've made several posts in the past regarding that for Madwifi and WPA...try looking at those and see if that helps.

Scott

---

