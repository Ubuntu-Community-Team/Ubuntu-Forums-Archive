---
title: "No network connection"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by Alxl on 2009-10-19
Installed Ubuntu 9.04 on an older Dell laptop.  Everything seems fine except that I cannot get online.
I am new to Linux but tried to read about this problem and entered *** lspci*** and also     **lshw -C network**  as was suggested and here is what I got.
Hope somebody can help (I am writing this on another laptop)

:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)


-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:dc:76:84
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:01:2e:1d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ee:20:24:50:4b:5d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
-laptop:~$

---

### Post by Iowan on 2009-10-19
How are you trying to connect - wired, wireless (either)? Attempting to get address via  DHCP?

---

### Post by Alxl on 2009-10-19
this laptop has dual boot XP and Ubuntu 9.04.   No problem getting online in windows.

I can that something is disabled: 

***-network:0 DISABLED  -network:1 DISABLED**

but how do I enable one?

Thanks

---

### Post by Alxl on 2009-10-19
sorry Iowan -  I did not see your post before I posted again.

I am trying to get online wireless . I have cable for the main computer and a router which works for another laptop .

what is  DHCP ?

---

### Post by Iowan on 2009-10-19
[DHCP]("http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol") is Dynamic Host Configuration Protocol. In essence, it means your computer gets an IP address by asking for one - you don't need to manually enter the information. In many (most?) home networks, the router is also a DHCP server.

---

### Post by calrogman on 2009-10-19
Can you post the output of `lsmod` and `dmesg | grep b43`?

---

### Post by Alxl on 2009-10-19
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  0 
nls_cp437              13696  0 
vfat                   18816  0 
fat                    58272  1 vfat
usb_storage            82880  0 
rfkill_input           12800  0 
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
arc4                    9856  2 
ecb                    10752  2 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
b43                   131484  0 
snd_seq_oss            37760  0 
pcmcia                 44748  0 
mac80211              217208  1 b43
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
yenta_socket           32396  1 
cfg80211               38032  1 mac80211
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
rsrc_nonstatic         19328  1 yenta_socket
psmouse                61972  0 
dcdbas                 15264  0 
led_class              12036  1 b43
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                 10496  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw              13316  0 
input_polldev          11912  1 b43
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
btusb                  19608  2 
video                  25360  0 
output                 11008  1 video
usbhid                 42336  0 
b44                    35984  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
ssb                    41220  2 b43,b44
mii                    13312  1 b44
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

:~$ dmesg | grep b43
[    3.743930] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.356384] b43-phy0: Broadcom 4318 WLAN found
[   23.635746] input: b43-phy0 as /devices/virtual/input/input11
[   23.696064] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   23.752148] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   23.752155] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[   23.770938] input: b43-phy0 as /devices/virtual/input/input12
[   23.824064] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   23.827266] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   23.827273] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
laptop:~$

---

### Post by calrogman on 2009-10-19
Please run ```
sudo aptitude install b43-fwcutter
```When prompted whether or not to fetch and install the firmware, enter Yes.

---

### Post by Alxl on 2009-10-19
b43-fwcutter  installed with no problems.
I rebooted and still no connection to the router

---

### Post by calrogman on 2009-10-19
Post the output of `lspci -vnn | grep -i 14E4` please.

---

### Post by calrogman on 2009-10-19
See this thread.

[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by Alxl on 2009-10-20
-laptop:~$ lspci -vnn | grep -i 14E4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:03.0 Network controller [0280]: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)
-laptop:~$

---

### Post by Alxl on 2009-10-20
[calrogman]("http://ubuntuforums.org/member.php?u=674525"), 

I looked at the thread but it refers to version 8.10 and specifically says that it will not work for other versions  (I have 9.04 installed on this laptop).

I also have Ubuntu 8.04 on a USB stick and started the laptop with this USB without installing - works good but still no internet.


Do you think I should try the latest version of Ubuntu still in beta?

Hope that somebody can help
[RIGHT]I
[/RIGHT]

---

### Post by Alxl on 2009-10-25
still no internet.
I was wandering if Ubuntu 9.10 may have new drivers  to get online easier.
Any help appreciated.
Thanks

---

### Post by Alxl on 2009-11-05
As a follow-up,  all that was needed was a driver: " Broadcom B43 wireless driver ".


 I installed Ubuntu 9.10 and it promptly said that the driver is missing. After downloading  same,  machine works fine.


 Thank you all for your input

---

### Post by Iowan on 2009-11-05
[SOLVED]?
(Thread Tools)

---

