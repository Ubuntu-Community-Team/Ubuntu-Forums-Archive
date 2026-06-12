---
title: "Atheros network help....."
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by openation1 on 2013-05-26
hello everyone,,,,, I need help with this issue,.... atheros is what I'm using and it doesn't work please help me........ thank you I am using 10.04 and this is what I have.hi everyone, I just install the 12.04 in my laptop but the wifi doesnt work please help me.... this is what it says...
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)



openation@compaq:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
[sudo] password for openation: 
options ath9k nohwcrypt=1
openation@compaq:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
openation@compaq:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
openation@compaq:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

openation@compaq:~$ dmesg | grep ath
[    0.811321] device-mapper: multipath: version 1.1.0 loaded
[    0.811324] device-mapper: multipath round-robin: version 1.0.0 loaded
[    7.721333] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.721345] ath9k 0000:02:00.0: setting latency timer to 64
[    7.770801] ath: EEPROM regdomain: 0x60
[    7.770803] ath: EEPROM indicates we should expect a direct regpair map
[    7.770807] ath: Country alpha2 being used: 00
[    7.770808] ath: Regpair used: 0x60
[    8.751536] phy0: Selected rate control algorithm 'ath9k_rate_control'
[    8.752167] Registered led device: ath9k-phy0::radio
[    8.752180] Registered led device: ath9k-phy0::assoc
[    8.752193] Registered led device: ath9k-phy0::tx
[    8.752204] Registered led device: ath9k-phy0::rx

---

