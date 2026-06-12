---
title: "Ath5k just my device not connecting"
date: 2012-12-28
forum: Networking &amp; Wireless
---

### Post by soiled skivvies on 2012-12-28
Been searching for days with no answer but a lot of things to get a head start. I typed in a ton of commands from other forums and here's my results.  
First off, let me state that this is ONLY effected when I try to connect to my network out of about 12.  I have no other problems connecting to any other network or device. I've tried hotspots around town and they all worked.  My neighbor said I could use his to figure mine out. The password type WPA/WPA2 is used on both networks. Only mine keeps disconnecting and reconnecting.   
 

 Here's some stuff that might help you:

The wireless device I am trying to connect to is a Verizon SCH-LC11 7b7d  and the network name is the same with the word “secure” addd on.  The password is stamped on the back of the device and it works on everything else, so I know it isn't that.
 

 Toshiba Satellite A105
 

 ```
  
 uname -a 
 Linux daniela105 3.2.0-35-generic-pae #55-Ubuntu SMP Wed Dec 5 18:04:39 UTC 2012 i686 i686 i386 GNU/Linux 
 

 lspci 
 00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Device 5a31 (rev 01) 
 00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge 
 00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80) 
 00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80) 
 00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80) 
 00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80) 
 00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 82) 
 00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80) 
 00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01) 
 00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80) 
 00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80) 
 01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RC410 [Radeon Xpress 200M] 
 02:04.0 Ethernet controller: Atheros Communications Inc. AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] (rev 01) 
 02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01) 
 02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
 

 

 rfkill list all 
 0: phy0: Wireless LAN 
     Soft blocked: no 
     Hard blocked: no 
 

 dmesg | grep ath 
 [   25.094837] ath5k 0000:02:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
 [   25.094931] ath5k 0000:02:04.0: registered as 'phy0' 
 [   25.701145] ath: EEPROM regdomain: 0x64 
 [   25.701150] ath: EEPROM indicates we should expect a direct regpair map 
 [   25.701157] ath: Country alpha2 being used: 00 
 [   25.701159] ath: Regpair used: 0x64 
 [   25.772270] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45) 
 

 

 only pasting my network:
 

 sudo ifconfig 
 eth0      Link encap:Ethernet  HWaddr 00:a0:d1:37:61:97   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
           Interrupt:20 Base address:0xa000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:709 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:709 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:60318 (60.3 KB)  TX bytes:60318 (60.3 KB) 
  
 wlan0     Link encap:Ethernet  HWaddr 00:16:e3:04:22:97   
           inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: fe80::216:e3ff:fe04:2297/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:3720 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:3482 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:4238707 (4.2 MB)  TX bytes:474239 (474.2 KB) 
 

 sudo iwlist wlan0 scan
           Cell 03 - Address: D0:DF:C7:C8:7B:7D 
                     Channel:2 
                     Frequency:2.417 GHz (Channel 2) 
                     Quality=39/70  Signal level=-71 dBm   
                     Encryption key:on 
                     ESSID:"Verizon SCH-LC11 7b7d Secure" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s 
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                               36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=000000005c4a9188 
                     Extra: Last beacon: 100ms ago 
                     IE: Unknown: 001C566572697A6F6E205343482D4C433131203762376420536563757265 
                     IE: Unknown: 010482848B96 
                     IE: Unknown: 030102 
                     IE: Unknown: 072455532001010B0201170301170401170501170601170701170801170901170A01160B010B 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 32080C1218243048606C 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (1) : TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00 
                     IE: Unknown: DD920050F204104A0001101044000102103B000103104700105175616C636F6D6D5F575053520000001021000C5175616C636F6D6D20496E63102300105750535265676973747261723132333410240009343432332D343433331042000D51434F4D2D575053522D3132331054000800060050F204000110110013534F465441502D57505352656769737472617210080002008C 
 

 sudo modprobe ath5k  <--- does nothing
 

 

 iwconfig 
 lo        no wireless extensions. 
  
 wlan0     IEEE 802.11bg  ESSID:"Verizon SCH-LC11 7b7d Secure"   
           Mode:Managed  Frequency:2.417 GHz  Access Point: D0:DF:C7:C8:7B:7D    
           Bit Rate=1 Mb/s   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off 
           Encryption key:off 
           Power Management:off 
           Link Quality=67/70  Signal level=-43 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
  
 eth0      no wireless extensions. 
  That was for my network right before it disconnected again.   
 

 

 gedit /etc/modprobe.d/blacklist-ath_pci.conf
 # For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
 # correctly initialize the hardware, leaving it in a state from
 # which ath5k cannot recover. To prevent this condition, stop
 # madwifi from loading by default. Use Jockey to select one driver
 # or the other. (Ubuntu: #315056, #323830)
 blacklist ath_pci
 

 (Is madwifi important since it's not in synaptic and I've never heard of it???)
 
``` I added the file “ath5k.conf” in “/etc/modeprobe.d/” with the “options ath5k nohwcrypt=1”
 I have rebooted several times.  I changed the channel manually using “sudo iwconfig wlan0 channel 2”
 I have tried deleting and adding it manually in the edit connections on the dropdown menu.
 I tried the following from another forum:
   
 
```

 sudo ifconfig wlan0 down sudo rmmod -r ath5k sudo modprobe ath5k nohwcrypt=1 sudo ifconfig wlan0 up 

 The last command is pointless as the one before it makes the wifi come back on. I still did it anyways.
 
```
 NOTE:  THIS ONLY HAPPENS ON JUST MY DEVICE. ALL OTHER NETWORK ACTIVITY ON ANY NETWORK IS PERFECTLY NORMAL AND SANE AND STABLE.  It just won't connect to the Verizon 4g box thingy they gave me where I can't go into it like a normal router and play with options and I'm too lazy to try to break into it. The “connected” LED blinks all the time, going from blue (good to go) and green (standby)  My Android phone and my other Ubuntu 12.04 64 bit laptop with a Broadcom (that was hell getting to work) driver connect to it just fine every try, as does my neighbor who let me use his connection to post this connected to my little box just fine with no problems from his house with a desktop and an iPhone.   
 

 Thank you. :)
 

 P.S. Every Ubuntuforums thread marked “solved” had no solutions, so if I didn't post it in here believe me I tried. I checked multiple websites and threads and all the solutions are pretty much the same, starting most recent and  ghosting back to 2008/9. I moved the Verizon box to another room thinking it was way too close (almost touching laptop) and no results.
 

 I have 5 days to fix this as I am visiting and it's 2.5 hours from home.

---

### Post by praseodym on 2012-12-28
Try to update the driver via the backported linux-wireless drivers:
```

sudo apt-get install --reinstall linux-headers-generic-pae build-essential dkms linux-backports-modules-cw-3.6-precise-generic-pae
```
Reboot.

Alternatively, you should be able to install the madwifi-driver via "additional drivers"?!

---

### Post by steeldriver on 2012-12-28
don't know if it will make a difference but the ath**5**k nohwcrypt option type is bool not int

```

$ modinfo ath9k | grep nohwcrypt
parm:           nohwcrypt:Disable hardware encryption (int)
$
$ modinfo [COLOR=Red]ath5k [/COLOR]| grep nohwcrypt
parm:           nohwcrypt:Disable hardware encryption. ([COLOR=Red]bool[/COLOR])
$

```hence I believe the correct forms are 

```
options nohwcrypt=Y 
```or

```
modprobe ath5k nohwcrypt=Y
```

---

