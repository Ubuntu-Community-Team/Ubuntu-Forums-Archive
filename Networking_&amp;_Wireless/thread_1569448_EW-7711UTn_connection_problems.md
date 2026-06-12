---
title: "EW-7711UTn connection problems"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by Medroon on 2010-09-06
Just started using Ubuntu tonight, but I'm having problem getting my Edimax EW-7711UTn to work (I'm stuck with using the ethernet cable for now). The light flashes on it and it picks up wireless networks, but when I'm connecting to them, I put in the key, it tries to connect, but the wireless key window pops up again and again and again. I've looked up other threads about this, but none of the suggested methods have worked for me :( *(I've checked to see if it's compatible, apparently it isn't, but people seem to have got it working before...)* I'm using a Toshiba Satellite M40 laptop.
$lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

```$lsusb
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 7392:7711  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```$iwconfig wlan0
```
wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 00:24:2C:79:2A:2D   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```$ lsmod|grep rt2870sta
```

rt2870sta             461811  1

```$dmes|grep rt2870sta
```

[   15.868117] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   15.938046] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.

```$sudo lshw -C network
```
*-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:be:a4:9a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2  driverversion=1.25 duplex=full firmware=N/A latency=0 link=no  multicast=yes port=twisted pair speed=100MB/s
       resources: irq:11 memory:bc000000-bc003fff ioport:a000(size=256)
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1f:1f:46:72:5b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RTxx70 Wireless

```$iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:2C:79:2A:2D
                    Protocol:802.11b/g/n
                    ESSID:"BTHomeHub2-N8K9"
                    Mode:Managed
                    Channel:1
                    Quality:100/100  Signal level:-45 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```$lsb_release -d
```
Description:    Ubuntu 10.04.1 LTS
```$uname -mr
```
2.6.32-24-generic i686
```

---

### Post by KSC2-303 on 2010-09-14
I was wondering if you got it working now. Because I have the same problem with my ew-7711 usn.
In the beginning it didn't detect any networks. After blacklisting rt2800usb it did detected some networks, but when I try to connect to a secured network it keeps asking me for the wpa key. And I'm not sitting on a dead spot or something because in windows it works just fine.

---

### Post by Psyprian on 2010-09-20
I'm guilty of not actually reading the pop-up window. I kept entering my WPA key, but Ubuntu really just wanted my default keyring password. 

As a separate gripe. My ew-7711usn will NOT hold a steady connection. Good for surfing, but terrible dor downloading or streaming media.

---

### Post by Fearsome_mork on 2010-09-22
try this link

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)

Follow the instructions, you need to run the "make" from the downloaded file directory within a Terminal window.

This worked for me and I have an EW-7711 UTn

---

