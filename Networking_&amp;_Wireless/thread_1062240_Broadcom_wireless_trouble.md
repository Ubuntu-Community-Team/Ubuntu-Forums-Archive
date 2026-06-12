---
title: "Broadcom wireless trouble"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by epqr on 2009-02-06
Ok so i have some trouble with my wireless card. It is a broadcom B43-series. I've installed a driver, and the light is blue and everything, but i just can't connect to the Internet. The "circle" with two green dots keeps spinning around for a while, with both dots green, and then it stop's and says it's disconnected. The same network works fine with my windows installation. 

The thing is it worked before. Actuality it work earlier today. I have installed a fresh copy of ubuntu 8.10, on my computer which i recently got back from service. It has a new HD so all data is gone. It stoped working after a day or two. I decided to do another clean install, because i messed up with the partitioning of the HD. After the second installation wireless hasn't worked at all.  On my previously installation of ubuntu, wireless worked perfectly. I think i had 8.04 before, so im going to try and install that. 

and another thing. I can only seem to find one of my two routers. Only the one furthers away is showing up in ubuntu. both have wpa2 security, or perhaps one of them has just wpa. So this one im having trouble with is not really the one i want to be connected with. I've tried to connect to the other router "manually" but it can't seem to find it at all. Again this works fine with all other computer and the windows partition.

thanks for all help :)



Solved! I don't know why it didn't work with the "Broadcom BC43 wireless driver", but it didn't. But the reason it didn't work with the  " Broadcom STA wireless driver" was because the SSID contained a space. That way it didn't show up with the STA driver installed (can't say i know why tho).

Moral: Use the STA wireless driver, and never but a space in your SSID :p

---

### Post by epqr on 2009-02-07
So i installed a copy of 8.04 instead. If i install the free B43x wireless driver both networks show up, but im not able to connevt to either of them. Both dots are gray. If i install the STA driver, which is a pr** driver, only the one network shows, but im not able to connect to that one either. The connection status then gets one green dot.

anyone?

---

### Post by kevdog on 2009-02-07
Can you post a few things for me

lshw -C network
lspci -nnm
iwlist scan

Thanks.

---

### Post by epqr on 2009-02-07
lshw -C network :
```
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:2f:b6:0e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

lspci -nnm :
```
jonesu1@e-ubuntu2:~$ sudo lspci -nnm
[sudo] password for jonesu1: 
00:00.0 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Host Bridge [02f0]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:00.1 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 0 [02fa]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:00.2 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 1 [02fe]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:00.3 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 5 [02f8]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:00.4 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 4 [02f9]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:00.5 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Host Bridge [02ff]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:00.6 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 3 [027f]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:00.7 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 2 [027e]" -ra2 "" ""
00:02.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "C51 PCI Express Bridge [02fc]" -ra1 "" ""
00:03.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "C51 PCI Express Bridge [02fd]" -ra1 "" ""
00:05.0 "VGA compatible controller [0300]" "nVidia Corporation [10de]" "C51 [Geforce 6150 Go] [0244]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:09.0 "RAM memory [0500]" "nVidia Corporation [10de]" "MCP51 Host Bridge [0270]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:0a.0 "ISA bridge [0601]" "nVidia Corporation [10de]" "MCP51 LPC Bridge [0260]" -ra3 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:0a.1 "SMBus [0c05]" "nVidia Corporation [10de]" "MCP51 SMBus [0264]" -ra3 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:0a.3 "Co-processor [0b40]" "nVidia Corporation [10de]" "MCP51 PMU [0271]" -ra3 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:0b.0 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP51 USB Controller [026d]" -ra3 -p10 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:0b.1 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP51 USB Controller [026e]" -ra3 -p20 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:0d.0 "IDE interface [0101]" "nVidia Corporation [10de]" "MCP51 IDE [0265]" -rf1 -p8a "Unknown vendor [f03c]" "Unknown device [30b7]"
00:0e.0 "IDE interface [0101]" "nVidia Corporation [10de]" "MCP51 Serial ATA Controller [0266]" -rf1 -p85 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:10.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "MCP51 PCI Bridge [026f]" -ra2 -p01 "" ""
00:10.1 "Audio device [0403]" "nVidia Corporation [10de]" "MCP51 High Definition Audio [026c]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:14.0 "Bridge [0680]" "nVidia Corporation [10de]" "MCP51 Ethernet Controller [0269]" -ra3 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
03:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4311 802.11b/g WLAN [4311]" -r01 "Hewlett-Packard Company [103c]" "BCM4311 802.11b/g Wireless LAN Controller [1364]"
07:05.0 "FireWire (IEEE 1394) [0c00]" "Ricoh Co Ltd [1180]" "R5C832 IEEE 1394 Controller [0832]" -p10 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
07:05.1 "SD Host controller [0805]" "Ricoh Co Ltd [1180]" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [0822]" -r19 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
07:05.2 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C843 MMC Host Controller [0843]" -r0a "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
07:05.3 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C592 Memory Stick Bus Host Adapter [0592]" -r05 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
07:05.4 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "xD-Picture Card Controller [0852]" -rff -pff "" ""

```

iwlist scan :
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

I am now connected with en ethernet-cabel, and I have the Broadcom B43 wireless driver installed (not the STA one).

Thanks!

---

### Post by Ayuthia on 2009-02-07
Can you post the results of:
```
dmesg|grep b43
```

---

### Post by epqr on 2009-02-07
```

[   37.981309] b43-phy0: Broadcom 4311 WLAN found
[   38.025128] b43-phy0 debug: Found PHY: Analog 4, Type 2, Revision 8
[   38.025149] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   45.063608] input: b43-phy0 as /devices/virtual/input/input12
[   45.250628] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   46.076525] b43-phy0 debug: Chip initialized
[   46.076978] b43-phy0 debug: 32-bit DMA initialized
[   46.100421] Registered led device: b43-phy0:tx
[   46.100709] Registered led device: b43-phy0:rx
[   46.100878] Registered led device: b43-phy0:radio
[   46.100915] b43-phy0 debug: Wireless interface started
[   46.101194] b43-phy0 debug: Adding Interface type 2

```

---

### Post by Ayuthia on 2009-02-07
Are you able to bring up wlan0?

```
sudo ifconfig wlan0 up
sudo iwlist scan
```

---

### Post by epqr on 2009-02-07
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:01:E3:E1:1A:00
                    ESSID:"JonesOppe"
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=50/100  Signal level=-76 dBm  Noise level=-62 dBm
                    Encryption key:on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001214a5e9580
          Cell 02 - Address: 00:22:B0:B4:D9:64
                    ESSID:"Hald nede"
                    Mode:Master
                    Channel:13
                    Frequency:2.472 GHz
                    Quality=83/100  Signal level=-46 dBm  Noise level=-62 dBm
                    Encryption key:on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001f9b73ea180

```

Looks like I do..?

---

### Post by Ayuthia on 2009-02-07
You might try kevdog's link for manually connecting.  It has worked well for me with my HP Pavilion dv6338se.  It has the same wireless card as yours (I am guessing that you are using an HP laptop).

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Just make sure that the group ciphers and pairwise ciphers match with what is listed from the scan.  At least that is how I have done it.

---

### Post by epqr on 2009-02-07
> **Ayuthia said:**
> You might try kevdog's link for manually connecting.  It has worked well for me with my HP Pavilion dv6338se.  It has the same wireless card as yours (I am guessing that you are using an HP laptop).

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Just make sure that the group ciphers and pairwise ciphers match with what is listed from the scan.  At least that is how I have done it.

Yup I have an HP dv6000. I'll try out the guide now. 

Thanks!

---

### Post by mpl34 on 2009-02-07
I have a BCM4328 and had problems with the b43 driver I would suggest installing the broadcom STA driver given [here]("http://www.broadcom.com/support/802.11/linux_sta.php").

Download this file into any given directory. Then in the terminal navigate you way to this directory and untar the file by ```
tar -xzf hybrid*.tar.gz
``` 

To make sure the source as not been pre-compiled use the following.```
make  -C /lib/modules/`uname -r`/build M=`pwd` clean
```

Compile the source with the following```
make -C /lib/modules/`uname -r`/build M=`pwd`
```

Remove any current wireless modules```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
```

Load the necessary modules```
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko
sudo modprobe b44
```

Restart your network
```
sudo /etc/init.d/networking restart
```
now this wireless should be running, after this i had no problems and was able to connect to my wireless network

However you will also need to edit the rc.local file so that the correct modules are loaded correctly on boot, this is a simple process just use the following,
```
sudo nano /etc/rc.local
```
Then add the following anywhere into the script
```
modprobe -r b43 b44 ssb ndiswrapper wl
modprobe ieee80211_crypt_tkip
insmod wl.ko
modprobe b44
/etc/init.d/networking restart
```

I hope this helps it seemed to sort out my problems

---

### Post by epqr on 2009-02-07
OK i got it work now. I don't know why it didn't work with the BC43 driver ( the free driver), but it just didn't. The guide Ayuthia provided me didn't work for me either.

As i mentioned before i network i needed to connect to didn't show up while i had the STA driver installed. Then I realized that my one router had a space in it. It was called "Hald nede". Thats why it didn't show up with the STA driver. So i removed the space, and boom!; it worked perfectly.

Thanks for all the help :)

---

