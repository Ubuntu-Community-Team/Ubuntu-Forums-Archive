---
title: "Cannot Connect to Wireless Internet! (I am new))"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by Mithokey on 2011-06-23
Hey everyone! I am VERY new to all of this, so if it's possible please use very "babyish" words if that's okay. 

I just installed Ubuntu 11.04 and it works awesome, I love it so much! However, I can't get wireless to work. It works for my Windows Vista which is on the same laptop I installed Ubuntu on... what do I do?? If it's okay, can someone on here talk step by step explaining in newbie terms because I am very very new to computer stuff. I really love Ubuntu so far but need to get internet so I have the full advantages of it. 

Thanks! :)

---

### Post by Mithokey on 2011-06-24
Or, any type of step by step instructions are good too (hopefully easy to understand ones).

---

### Post by nm_geo on 2011-06-24
> **Mithokey said:**
> Or, any type of step by step instructions are good too (hopefully easy to understand ones).
1 step open terminal ctrnl-alt-t

```
lspci -nn
```you can copy paste the above better than typing

Paste results from terminal

---

### Post by Mithokey on 2011-06-24
Thanks for helping me! The output is:

 00:00.0 "0600" "8086" "2a00" -r0c "1028" "022f"
  00:02.0 "0300" "8086" "2a02" -r0c "1028" "022f"
  00:02.1 "0380" "8086" "2a03" -r0c "1028" "022f"
  00:1a.0 "0c03" "8086" "2834" -r02 "1028" "022f"
  00:1a.1 "0c03" "8086" "2835" -r02 "1028" "022f"
  00:1a.7 "0c03" "8086" "283a" -r02 -p20 "1028" "022f"
  00:1b.0 "0403" "8086" "284b" -r02 "1028" "022f"
  00:1c.0 "0604" "8086" "283f" -r02 "" ""
  00:1c.1 "0604" "8086" "2841" -r02 "" ""
  00:1c.4 "0604" "8086" "2847" -r02 "" ""
  00:1d.0 "0c03" "8086" "2830" -r02 "1028" "022f"
  00:1d.1 "0c03" "8086" "2831" -r02 "1028" "022f"
  00:1d.2 "0c03" "8086" "2832" -r02 "1028" "022f"
  00:1d.7 "0c03" "8086" "2836" -r02 -p20 "1028" "022f"
  00:1e.0 "0604" "8086" "2448" -rf2 -p01 "" ""
  00:1f.0 "0601" "8086" "2815" -r02 "1028" "022f"
  00:1f.1 "0101" "8086" "2850" -r02 -p8a "1028" "022f"
  00:1f.2 "0106" "8086" "2829" -r02 -p01 "1028" "022f"
  00:1f.3 "0c05" "8086" "283e" -r02 "1028" "022f"
  02:09.0 "0c00" "1180" "0832" -r05 -p10 "1028" "022f"
  02:09.1 "0805" "1180" "0822" -r22 -p01 "1028" "022f"
  02:09.2 "0880" "1180" "0592" -r12 "1028" "022f"
  02:09.3 "0880" "1180" "0852" -r12 "1028" "022f"
  09:00.0 "0200" "11ab" "4354" -r12 "1028" "022f"
  0b:00.0 "0280" "14e4" "4315" -r01 "1028" "000b"

---

### Post by nm_geo on 2011-06-24
Ok make sure you have both -nn

i think you only had one of the n's

NP

```
lspci -nn
```

```
sudo lshw -C network
```

Paste the results

---

### Post by Mithokey on 2011-06-24
Opps, sorry, I typed in "nm"... the new out put is: 

 00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
  00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
  00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
  00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
  00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
  00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
  00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
  00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
  00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
  00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
  00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
  00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
  00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
  00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
  00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
  00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
  00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
  00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
  00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
  02:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
  02:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
  02:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
  02:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
  09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
  0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

---

### Post by chili555 on 2011-06-24
@nm-geo--

Thar she blows!!> 0b:00.0 "0280" "[COLOR="Red"]14e4[/COLOR]" "[COLOR="Red"]4315[/COLOR]" -r01 "1028" "000b"b43/ssb/firmware or bcmwl??

Sorry, I'm getting post-hungry these days. OK, back to mindin' my own business...

---

### Post by nm_geo on 2011-06-24
> **chili555 said:**
> @nm-geo--

Thar she blows!!b43/ssb/firmware or bcmwl??

Sorry, I'm getting post-hungry these days. OK, back to mindin' my own business...
  No you are the doctor here we all know it... Thanks for any help Chili

---

### Post by nm_geo on 2011-06-24
Ok Mithokey we are in luck that chili is watching this one.

Go to the Synaptic program and install:
b43-fwcutter 
 firmware-b43-lpphy-installer

You have the low power Broadcom chip.

---

### Post by Mithokey on 2011-06-24
And after I type in the 2nd code, I get: 

 *-network               
         description: Ethernet interface
         product: 88E8040 PCI-E Fast Ethernet Controller
         vendor: Marvell Technology Group Ltd.
         physical id: 0
         bus info: pci@0000:09:00.0
         logical name: eth0
         version: 12
         serial: 00:21:9b:d1:f4:a9
         capacity: 100Mbit/s
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
         resources: irq:43 memory:fe8fc000-fe8fffff ioport:de00(size=256)
    *-network
         description: Network controller
         product: BCM4312 802.11b/g LP-PHY
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:0b:00.0
         version: 01
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: driver=b43-pci-bridge latency=0
         resources: irq:17 memory:fe7fc000-fe7fffff
    *-network DISABLED
         description: Wireless interface
         physical id: 2
         logical name: wlan0
         serial: 00:1f:e1:53:9f:12
         capabilities: ethernet physical wireless
         configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by nm_geo on 2011-06-24
Yeah we need the firmware

: broadcast=yes driver=b43 driverversion=2.6.38-8-generic [COLOR=Red]firmware=N/A link[/COLOR]=no multicast=yes wireless=IEEE 802.11bg

---

### Post by Mithokey on 2011-06-24
> **nm_geo said:**
> Ok Mithokey we are in luck that chili is watching this one.

Go to the Synaptic program and install:
b43-fwcutter 
 firmware-b43-lpphy-installer

You have the low power Broadcom chip.

OK, I'm at the package manager but those 2 programs arn't listed.

---

### Post by nm_geo on 2011-06-24
> **Mithokey said:**
> OK, I'm at the package manager but those 2 programs arn't listed.

What is installed? Do a search bcm and see what might be installed.

---

### Post by nm_geo on 2011-06-24
Let's see what is happening.

```
dmesg | egrep 'ound|irmware|eth|ath|wl|ipw|b43|witch|ndiswrapper'
```

Copy that long line and paste in terminal
Paste result

---

### Post by Mithokey on 2011-06-24
Did search, no results anywhere.

EDIT: Okay, am trying the code in terminal ^

---

### Post by Mithokey on 2011-06-24
I get this: 

 [    0.000000] No AGP bridge found
  [    0.000000] No NUMA configuration found
  [    0.000000] No AGP bridge found
  [    0.470215] ACPI: No dock devices found.
  [    0.470223] HEST: Table not found.
  [    0.550107] Switching to clocksource hpet
  [    0.559794] Switched to NOHz mode on CPU #0
  [    0.559875] Switched to NOHz mode on CPU #1
  [    0.582206] pnp: PnP ACPI: found 13 devices
  [    0.613076] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
  [    0.680030] ACPI: Lid Switch [LID]
  [    0.682694] ERST: Table is not found!
  [    0.853638] i2c-core: driver [adp5520] using legacy suspend method
  [    0.853641] i2c-core: driver [adp5520] using legacy resume method
  [    0.880150] hub 1-0:1.0: USB hub found
  [    0.900133] hub 2-0:1.0: USB hub found
  [    0.900536] hub 3-0:1.0: USB hub found
  [    0.900875] hub 4-0:1.0: USB hub found
  [    0.910194] hub 5-0:1.0: USB hub found
  [    0.910515] hub 6-0:1.0: USB hub found
  [    0.910835] hub 7-0:1.0: USB hub found
  [    0.940556] device-mapper: multipath: version 1.2.0 loaded
  [    0.940559] device-mapper: multipath round-robin: version 1.0.0 loaded
  [    0.943393] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
  [    1.297752] sdhci-pci 0000:02:09.1: SDHCI controller found [1180:0822] (rev 22)
  [    1.297843] mmc0: no vmmc regulator found
  [    1.305734] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
  [    1.305753] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
  [    1.326959] sky2 0000:09:00.0: eth0: addr 00:21:9b:d1:f4:a9
  [    1.360275] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
  [    1.360300] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
  [    1.360321] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
  [    1.360347] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
  [    1.451129] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
  [   12.090239] lp: driver loaded but no devices found
  [   12.978325] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
  [   13.172009] Registered led device: b43-phy0::tx
  [   13.172031] Registered led device: b43-phy0::rx
  [   13.172055] Registered led device: b43-phy0::radio
  [   13.172074] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
  [   13.841524] sky2 0000:09:00.0: eth0: enabling interface
  [   13.842536] ADDRCONF(NETDEV_UP): eth0: link is not ready
  [   13.908426] Console: switching to colour frame buffer device 160x50
  [   13.942295] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
  [   13.996430] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
  [   13.996485] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
  [   13.996521] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
  [   15.680297] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
  [   15.680413] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
  [   15.680525] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10

---

### Post by nm_geo on 2011-06-24
I may not have been clear on the "bcm" search in synaptic.

Here is  a snap shot of my installs your will be different slightly.

---

### Post by nm_geo on 2011-06-24
Go back to terminal and do 

```
sudo apt-get update 
```

```
sudo apt-get upgrade
```

it may be a while but then we will try to install the hopefully correct
firmware.. Or maybe Chili will help us out here.

---

### Post by Mithokey on 2011-06-24
Ah okay, I am not connected to any type of internet on Ubuntu so it's saying it can't connect to certain websites. I am using 2 computers at the moment.

---

### Post by nm_geo on 2011-06-24
> **Mithokey said:**
> Ah okay, I am not connected to any type of internet on Ubuntu so it's saying it can't connect to certain websites. I am using 2 computers at the moment.

That does create a problem..
Do you have an ethernet cable to connect to the ubuntu computer?
Sorry i assumed you were connected.

---

### Post by Mithokey on 2011-06-24
Haha, ethernet cable now connected and works. :P

---

### Post by nm_geo on 2011-06-24
> **Mithokey said:**
> Haha, ethernet cable now connected and works. :P

Now you can get the wireless working i after the update & upgrades..

Note to self: Stop assuming things.. check the results from codes LOL

---

### Post by Mithokey on 2011-06-24
> **nm_geo said:**
> Now you can get the wireless working i after the update & upgrades..

Note to self: Stop assuming things.. check the results from codes LOL

:P  Thanks so much for helping, I really appreciate it! So, about 5 minutes left on the upgrade, so I will have wireless internet when it's done, no more I need to do?

---

### Post by nm_geo on 2011-06-24
> **Mithokey said:**
> :P  Thanks so much for helping, I really appreciate it! So, about 5 minutes left on the upgrade, so I will have wireless internet when it's done, no more I need to do?

You still may need the correct firmware .. That I listed above..

**[COLOR=Red]firmware-b43-lpphy-installer[/COLOR]**

It appears you already have the b43 driver working that is different than I recall, but it is a good thing for your installation.

---

### Post by Mithokey on 2011-06-24
> **nm_geo said:**
> Now you can get the wireless working i after the update & upgrades..

Note to self: Stop assuming things.. check the results from codes LOL

> **nm_geo said:**
> You still may need the correct firmware .. That I listed above..

**[COLOR=Red]firmware-b43-lpphy-installer[/COLOR]**

It appears you already have the b43 driver working that is different than I recall, but it is a good thing for your installation.

This may be a stupid question, but how to I connect firmware?

---

### Post by nm_geo on 2011-06-24
> **Mithokey said:**
> This may be a stupid question, but how to I connect firmware?
Not connect but correct firmware.. Since you have the low power chip your firmware is a little different.  It all may be resolved after the update & upgrade, but if not install the firmware I marked above in Synaptic or if you like we can do it in the terminal..  I would probably use the terminal, but I don't always.

Synaptic > search b43
 find the firmware-b43-lpphy-installer   
mark it for install 
then apply

Terminal
```
sudo apt-get install firmware-b43-lpphy-installer
```Then you need to click on the network manager and set up your wireless connection.

---

### Post by Mithokey on 2011-06-24
> **nm_geo said:**
> Then you need to click on the network manager and set up your wireless connection.

How do I do that?

---

### Post by superduperlinuxperson on 2011-06-24
can check and see if two folders named b43 and b43 legacy are in lib/firmware

---

### Post by Mithokey on 2011-06-24
> **superduperlinuxperson said:**
> can check and see if two folders named b43 and b43 legacy are in lib/firmware

B43 in there, but when I click it, it says the folder contects could not be displayed.

---

### Post by nm_geo on 2011-06-24
> **Mithokey said:**
> B43 in there, but when I click it, it says the folder contects could not be displayed.

Just go to Synaptic search on b43
see what is installed

Then reboot the computer 

```
dmesg | egrep 'ound|irmware|eth|ath|wl|ipw|b43|witch|ndiswrapper'
``````

sudo lshw -C network
```Then we will address the network manager wireless setup

---

### Post by Mithokey on 2011-06-24
firmware-b43-installer
firmware-b43-lpphy-installer
b43-fwcutter
firmware-b43legacy-installer

---

### Post by nm_geo on 2011-06-24
> **Mithokey said:**
> firmware-b43-installer
firmware-b43-lpphy-installer
b43-fwcutter
firmware-b43legacy-installer

we may need to remove some of the firmwares, the lppy one and the fwcutter we need.  But let's see the codes after rebooting.

See my previous message on the codes we need to see.

---

### Post by Mithokey on 2011-06-24
Okay, the wireless is listed, I just need to enter my password (which I have written down somewhere :P)

---

### Post by nm_geo on 2011-06-24
> **Mithokey said:**
> Okay, the wireless is listed, I just need to enter my password (which I have written down somewhere :P)

Yeah that would be correct and make sure the security WEP / WAP stuff is right.

---

### Post by Mithokey on 2011-06-24
WEP Key is password?

---

### Post by nm_geo on 2011-06-24
> **Mithokey said:**
> WEP Key is password?

Probably I use WPA 2 personnel and my passphrase is the key.  
Try it..

---

### Post by Mithokey on 2011-06-24
Won't work for some reason

---

### Post by nm_geo on 2011-06-24
> **Mithokey said:**
> Won't work for some reason

```
sudo iwlist scanning
```


Do that and paste please

---

### Post by Mithokey on 2011-06-24
```

 lo        Interface doesn't support scanning.
   
  eth0      Interface doesn't support scanning.
   
  wlan0     Scan completed :
            Cell 01 - Address: 00:1E:C7:78:1B:79
                      Channel:2
                      Frequency:2.417 GHz (Channel 2)
                      Quality=65/70  Signal level=-45 dBm  
                      Encryption key:on
                      ESSID:"BELL784"
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                                11 Mb/s; 12 Mb/s; 18 Mb/s
                      Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                      Mode:Master
                      Extra:tsf=0000000d1410b2d2
                      Extra: Last beacon: 780ms ago
                      IE: Unknown: 000742454C4C373834
                      IE: Unknown: 010882848B0C12961824
                      IE: Unknown: 030102
                      IE: Unknown: 0706555320010B1B
                      IE: WPA Version 1
                          Group Cipher : TKIP
                          Pairwise Ciphers (1) : TKIP
                          Authentication Suites (1) : PSK
                      IE: Unknown: 2A0100
                      IE: Unknown: 32043048606C
            Cell 02 - Address: 74:EA:3A:D4:F0:E9
                      Channel:2
                      Frequency:2.417 GHz (Channel 2)
                      Quality=49/70  Signal level=-61 dBm  
                      Encryption key:on
                      ESSID:"BELL784"
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                9 Mb/s; 12 Mb/s; 18 Mb/s
                      Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                      Mode:Master
                      Extra:tsf=000000065974b4f9
                      Extra: Last beacon: 1120ms ago
                      IE: Unknown: 000742454C4C373834
                      IE: Unknown: 010882848B960C121824
                      IE: Unknown: 030102
                      IE: WPA Version 1
                          Group Cipher : TKIP
                          Pairwise Ciphers (1) : TKIP
                          Authentication Suites (1) : PSK
                      IE: Unknown: 2A0100
                      IE: Unknown: 32043048606C
                      IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                      IE: Unknown: DD0900037F01010000FF7F
                      IE: Unknown: DD0A00037F04010006004000
  
```

---

### Post by nm_geo on 2011-06-24
> **Mithokey said:**
> ```

 lo        Interface doesn't support scanning.
   
  eth0      Interface doesn't support scanning.
   
  wlan0     Scan completed :
            Cell 01 - Address: 00:1E:C7:78:1B:79
                      Channel:2
                      Frequency:2.417 GHz (Channel 2)
                      Quality=65/70  Signal level=-45 dBm  
                      Encryption key:on
                      ESSID:"BELL784"
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                                11 Mb/s; 12 Mb/s; 18 Mb/s
                      Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                      Mode:Master
                      Extra:tsf=0000000d1410b2d2
                      Extra: Last beacon: 780ms ago
                      IE: Unknown: 000742454C4C373834
                      IE: Unknown: 010882848B0C12961824
                      IE: Unknown: 030102
                      IE: Unknown: 0706555320010B1B
                      IE: WPA Version 1
                          Group Cipher : TKIP
                          Pairwise Ciphers (1) : TKIP
                          Authentication Suites (1) : PSK
                      IE: Unknown: 2A0100
                      IE: Unknown: 32043048606C
            Cell 02 - Address: 74:EA:3A:D4:F0:E9
                      Channel:2
                      Frequency:2.417 GHz (Channel 2)
                      Quality=49/70  Signal level=-61 dBm  
                      Encryption key:on
                      ESSID:"BELL784"
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                9 Mb/s; 12 Mb/s; 18 Mb/s
                      Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                      Mode:Master
                      Extra:tsf=000000065974b4f9
                      Extra: Last beacon: 1120ms ago
                      IE: Unknown: 000742454C4C373834
                      IE: Unknown: 010882848B960C121824
                      IE: Unknown: 030102
                      IE: WPA Version 1
                          Group Cipher : TKIP
                          Pairwise Ciphers (1) : TKIP
                          Authentication Suites (1) : PSK
                      IE: Unknown: 2A0100
                      IE: Unknown: 32043048606C
                      IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                      IE: Unknown: DD0900037F01010000FF7F
                      IE: Unknown: DD0A00037F04010006004000
  
```
  I assume your SSID id BELL784

Looks like WPA protection to me.

Then you need the passphase ..

I would make auto connect and check all users unless you want to provide passwords everytime.

Sorry but I have to go now and don't know the passphase anyway.
But you have wireless working ..
Oh be sure to remove cable when you think the wireless is ok, and reboot to be absolutely sure.
I will check back later to see how it is going.

---

### Post by Mithokey on 2011-06-24
Thanks, I need to go for a bit to and I'll post the outcome on here when I get it working/not working.

---

### Post by nm_geo on 2011-06-24
> **Mithokey said:**
> Thanks, I need to go for a bit to and I'll post the outcome on here when I get it working/not working.

Just got back from a wedding and wonder how it went. Good luck..

---

### Post by Homakee on 2011-06-25
I am also new to this and have the same problem. I dont know how to identify what the terminal is saying so i cant tell what type of wireless card i have can you please help me? :)

---

### Post by Mithokey on 2011-07-17
Hey! Sorry for long reply! 

My wireless network is up, but when I enter the password it stops for a minute, then redirects me to re-type my password again and the same thing goes on and on... cannot get it to work. :(

---

### Post by nm_geo on 2011-07-17
> **Mithokey said:**
> Hey! Sorry for long reply! 

My wireless network is up, but when I enter the password it stops for a minute, then redirects me to re-type my password again and the same thing goes on and on... cannot get it to work. :(

Let's check a few things

```
lsmod
```

and 
```

sudo iwlist scanning
```

Again and tell me your router name "ESSID"

---

### Post by Mithokey on 2011-07-28
Sorry, my ubuntu crashed after installing something... will try to get it (hopefully tonight) and get back to you right away!

---

### Post by Mithokey on 2011-08-16
For the first code I get:

```
Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_idt      71137  1 
snd_hda_codec_hdmi     28167  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
arc4                   12529  2 
i915                  514975  3 
joydev                 17606  0 
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
b43                   318638  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
drm_kms_helper         42136  1 i915
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
r852                   18246  0 
drm                   227495  4 i915,drm_kms_helper
snd_timer              29602  2 snd_pcm,snd_seq
sm_common              16817  1 r852
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
nand                   55112  2 r852,sm_common
mac80211              294370  1 b43
nand_ids               12723  1 nand
psmouse                73535  0 
nand_ecc               13230  1 nand
dell_laptop            13827  0 
dell_wmi               12681  0 
i2c_algo_bit           13400  1 i915
snd                    67382  14 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
mtd                    27900  2 sm_common,nand
lp                     17825  0 
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              178528  2 b43,mac80211
video                  19438  1 i915
sparse_keymap          13898  1 dell_wmi
dcdbas                 14438  1 dell_laptop
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  1 
firewire_ohci          40370  0 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
libahci                26642  1 ahci
ssb                    51945  1 b43
sky2                   58509  0 
```

For the second code I get:

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 74:EA:3A:D4:F0:E9
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"BELL784"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000054327fd80
                    Extra: Last beacon: 1020ms ago
                    IE: Unknown: 000742454C4C373834
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018A0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
          Cell 02 - Address: 00:1E:C7:78:1B:79
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"BELL784"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014985fd52ab
                    Extra: Last beacon: 780ms ago
                    IE: Unknown: 000742454C4C373834
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C


```

---

### Post by nm_geo on 2011-08-16
The thing that strikes me is that there are two cells with the same ESSID:"BELL784" on the same channel. If one of those is not your 
wireless access points we can try to solve that by changing the ESSID name and channel provided you have access.  You could also temporarily turn the security off and see if you get a stable connection.    

What it looks like to me is that your provider setup the wireless access router at your house and you next door neighbor has the same wireless name and channel.  However I am not a wireless router expert by far, but both do have different addresses.

Do you have access to this wireless access point?

Think about how confusing it must be for the computer wireless chip to decide which one it should try to connect to, and if the signal changes it might disconnect and start trying the other cell.

Be sure your passphase is correct and that you have selected WPA in the network manager security tab.  

please do the following commands 

```
dmesg | grep -e b43 -e firmware

``````
sudo lshw -C network

```Your driver and firmware look ok to me but those will give us more information. Copy and paste in the thread.

---

### Post by Mithokey on 2011-08-16
Okay, let me try that now

---

### Post by Mithokey on 2011-08-16
First one:

```

[    1.276950] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.276969] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[   19.431053] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   19.690592] Registered led device: b43-phy0::tx
[   19.690615] Registered led device: b43-phy0::rx
[   19.690639] Registered led device: b43-phy0::radio
[   20.590117] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)

```

Second one:


```
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:d1:f4:a9
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe7fc000-fe7fffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:e1:53:9f:12
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-10-generic firmware=478.104 link=no multicast=yes wireless=IEEE 802.11bg

```

---

### Post by nm_geo on 2011-08-16
Those look good ..
How about the wireless router information?

---

### Post by Mithokey on 2011-08-16
What do you mean? Like my password and stuff? The password is the right one but doesn't work. When I type it in, the thing starts connecting (so the password must have worked), but after a few minutes the same window pops up asking for the password again.

---

### Post by nm_geo on 2011-08-16
Is there a wireless router in your home?
Did Bell set it up?
Can you change any settings in the wireless?
Does your neighbor have a wireless router too?

---

### Post by Mithokey on 2011-08-16
Yes to all questions

---

### Post by nm_geo on 2011-08-16
> **Mithokey said:**
> Yes to all questions

You are a person of few words i see.. Read my first message today..

---

### Post by Mithokey on 2011-08-16
Meh, it's okay. Ubuntu is too much work, back to Windows.

---

