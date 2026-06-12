---
title: "Surprise!  Help with Broadcom 4318/Ubuntu 9.10/Compaq Presario V2000 laptop..."
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by ivyclarice on 2009-12-03
I first installed Karmic about a month ago.  Although my laptop is older, I wiped the entire drive and kissed XP goodbye.  I used a wired connection to get b43-fwcutter and had no problems connecting to my wireless.  Then a couple weeks later, I suddenly started having intermittent wireless connection problems (the machine could see my wireless network just fine, but wouldn't connect to it).  

I tried to repair it using ndiswrapper, and at first, that worked better than ever (faster, more reliable connection), then the whole thing failed and I couldn't connect wirelessly again, no matter what I tried.  There was no rhyme or reason that I could detect.  It seemed to work fine one night, and then not at all after that.  My wireless networking enabling disappeared, and the WiFi 'light' on my computer went out.

Frustrated, I did a completely fresh install of Karmic again on 12/01, which restored my wireless light and ability to enable wireless networking, but I haven't been able to get a wireless connection yet.  I've seen other posters complain about the possibility of an update around 11/29 causing similar problems, so I'm not sure if that's to blame.  I'm partly tempted to try yet another fresh install, and not allow any updates.

At any rate, here is the output for my machine (I'm sorry it's so long - I tried to cut it as short as I felt I could).  Can anyone suggest some things to try?

                                 **1 ) Machine Brand and Model (PC/Laptop)**:
 Compaq Presario V2000, Laptop (purchased March 2006)
 

 **2 ) Wireless Brand, Model and Wireless Chipset:**
  Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
 

 ~$ sudo lshw -C network; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -C usb; uname -a; dmesg | grep ound; dmesg | grep b43; dmesg | grep iwl; iwconfig; sudo /etc/init.d/networking restart  
   *-network:0              
        description: Ethernet interface  
        product: RTL-8139/8139C/8139C+  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:05:00.0  
        logical name: eth0  
        version: 10  
        serial: 00:16:36:23:0c:45  
        size: 100MB/s  
        capacity: 100MB/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.5 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s  
        resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff  
   *-network:1  
        description: Network controller  
        product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller  
        vendor: Broadcom Corporation  
        physical id: 2  
        bus info: pci@0000:05:02.0  
        version: 02  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master  
        configuration: driver=b43-pci-bridge latency=64  
        resources: irq:20 memory:c0204000-c0205fff 



   *-network  
        description: Wireless interface  
        physical id: 1  
        logical name: wlan0  
        serial: 00:14:a5:6e:cd:06  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg  
 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 wmaster0  Interface doesn't support scanning.  
 

 wlan0     Scan completed :  
                 Cell 02 - Address: 00:1C:DF:BD:44:F3  
                     Channel:6  
                     Frequency:2.437 GHz (Channel 6)  
                     Quality=45/70  Signal level=-65 dBm   
                     Encryption key:on  
                     ESSID:"Ryleh" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s  
                               12 Mb/s; 24 Mb/s; 36 Mb/s  
                     Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s  
                     Mode:Master  
                     Extra:tsf=000001d7a4023181  
                     Extra: Last beacon: 700ms ago  
                     IE: Unknown: 000552796C6568  
                     IE: Unknown: 010882848B960C183048  
                     IE: Unknown: 030106 
                     IE: Unknown: 0706555320010B1B  
                     IE: Unknown: 2A0100 
                     IE: Unknown: 32041224606C  
                     IE: IEEE 802.11i/WPA2 Version 1  
                         Group Cipher : TKIP  
                         Pairwise Ciphers (1) : CCMP  
                         Authentication Suites (1) : PSK  
                        Preauthentication Supported  
                     IE: WPA Version 1  
                         Group Cipher : TKIP  
                         Pairwise Ciphers (2) : TKIP CCMP  
                         Authentication Suites (1) : PSK  
                     IE: Unknown: DD180050F2020101000003A4000027A4000041435E0061211A01  
                     IE: Unknown: DD9D0050F204104A00011010440001021041000100103B0001031047001000000000000000011000001CDFBD44F31021001242656C6B696E20436F72706F726174696F6E1023000C463544373233342D3420763310240007332E30302E30331042000B42453730323033343830341054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020004 
 

 auto lo  
 iface lo inet loopback  
 

 DISTRIB_ID=Ubuntu  
 DISTRIB_RELEASE=9.10  
 DISTRIB_CODENAME=karmic  
 DISTRIB_DESCRIPTION="Ubuntu 9.10" 
 00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)  
 00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]  
 00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)  
 00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)  
 00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)  
 00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 82)  
 00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)  
 00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)  
 00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)  
 00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 80)  
 00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 80)  
 00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]  
 00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]  
 00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102] 
 00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]  
 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]  
 05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)  
 05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)  
 05:09.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]  
 05:09.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]  
 05:09.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]  
 05:09.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]  
 Bus 001 Device 002: ID 12f7:1c00 Memorex Products, Inc.  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Linux ivyclarice-laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux  
 [    0.000000] found SMP MP-table at [c00f80f0] f80f0  
 [    0.036001] ..... (found apic 0 pin 0) ...  
 [    0.096627] ACPI: No dock devices found.  
 [    0.109574] pnp: PnP ACPI: found 10 devices  
 [    1.578491] isapnp: No Plug & Play device found  
 [    1.596156] hub 1-0:1.0: USB hub found  
 [    1.656117] hub 2-0:1.0: USB hub found  
 [    1.716115] hub 3-0:1.0: USB hub found  
 [    1.718781] device-mapper: multipath round-robin: version 1.0.0 loaded  
 [    1.720726] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-32 processors (1 cpu cores) (version 2.20.00)  
 [    1.721155] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  
 [    3.689710] usb-storage: device found at 2  
 [    3.768093] ssb: Sonics Silicon Backplane found on PCI device 0000:05:02.0  
 [   17.612150] sdhci-pci 0000:05:09.4: SDHCI controller found [104c:8034] (rev 0)  
 [   17.662002] yenta_cardbus 0000:05:09.0: CardBus bridge found [103c:3091]  
 [   17.709598] b43-phy0: Broadcom 4318 WLAN found (core revision 9)  
 [   18.303947] lp: driver loaded but no devices found  
 [   23.192095] ssb: Sonics Silicon Backplane found on PCI device 0000:05:02.0  
 [   23.207880] b43-phy1: Broadcom 4318 WLAN found (core revision 9)  
 [    3.708390] b43-pci-bridge 0000:05:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20  
 [   17.709598] b43-phy0: Broadcom 4318 WLAN found (core revision 9)  
 [   20.204062] b43 ssb0:0: firmware: requesting b43/ucode5.fw  
 [   20.421912] b43 ssb0:0: firmware: requesting b43/pcm5.fw  
 [   20.483594] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw  
 [   20.506277] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw  
 [   20.668102] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)  
 [   20.704780] Registered led device: b43-phy0::radio  
 [   23.062351] b43-pci-bridge 0000:05:02.0: PCI INT A disabled  
 [   23.134325] b43-pci-bridge 0000:05:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20  
 [   23.207880] b43-phy1: Broadcom 4318 WLAN found (core revision 9)  
 [   23.344084] b43 ssb0:0: firmware: requesting b43/ucode5.fw  
 [   23.348036] b43 ssb0:0: firmware: requesting b43/pcm5.fw  
 [   23.353976] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw  
 [   23.359768] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw  
 [   23.484043] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)  
 [   23.524415] Registered led device: b43-phy1::radio  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wmaster0  no wireless extensions.  
 

 wlan0     IEEE 802.11bg  ESSID:""   
           Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
           Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
           Link Quality:0  Signal level:0  Noise level:0  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

  * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.

---

### Post by ivyclarice on 2009-12-10
I didn't want to hijack someone else's thread, but wanted to bump this back up to see if anyone reading now might be able to lend a hand?

I'm sure I left out pertinent details, but I'm just at an utter loss and don't have any other OS to fall back on, so would love to get my wireless working again.

Thanks for any help you might have.  :)

---

### Post by bkratz on 2009-12-10
Have you been here yet? They specifically mention your card.  Here's hoping it helps you.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)



Also here, just a couple of threads below yours


[http://ubuntuforums.org/showthread.php?t=1347487](http://ubuntuforums.org/showthread.php?t=1347487)

---

