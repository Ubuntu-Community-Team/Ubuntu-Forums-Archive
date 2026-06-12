---
title: "Laptop only detects networks for a few seconds after booting"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by shivers222 on 2011-09-02
Hello! I'm having a weird issue with my wireless connection. The wireless card is only able to detect networks for a few seconds after it boots into the OS. After that, they all disappear and won't reappear unless I restart and then they only appear for a few seconds again. I'm using WICD but iwlist eth1 scan confirms that the card isn't detecting any networks.

Thanks a lot for any help with solving this mystery!

Information on my system:
T30 Thinkpad
Ubuntu 11.04
Cisco Aironet Wireless Card 802.11b

---

### Post by wildmanne39 on 2011-09-02
Hi, please run these commands in a terminal:
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nn 
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by nm_geo on 2011-09-02
Let me ask first of all your wireless router what kind of security do you have setup?

WPA?  

```
rfkill list all
iwconfig 
dmesg | grep airo
```

---

### Post by shivers222 on 2011-09-05
Ok, here's the results. Sorry for the late reply. I don't have network manager installed so the nm-tool doesn't work. I've tried connecting to unsecured and WEP networks and was successful with both of them. Whenever I try a WPA2 network I get a "Bad Password" error message. As you will see, I was able to connect to a network with ESSID "Wifi" successfully by doing it right when the OS boot. And it's stayed connected long enough to make this post. But as soon as I disconnect from this network my card will most likely stop detecting any networks and I will have to restart again.

```


nk@HNK:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:b0:f2:4b
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:11 memory:c0220000-c023ffff memory:c0200000-c020ffff ioport:8400(size=64) memory:c0240000-c024ffff
  *-network:1 DISABLED
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:02:8a:fc:eb:27
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=airo ip=192.168.2.105 latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:8000(size=256) memory:c0210000-c0213fff memory:c0400000-c07fffff memory:c0800000-c09fffff
hnk@HNK:~$ nm-tool
The program 'nm-tool' is currently not installed.  You can install it by typing:
sudo apt-get install network-manager
hnk@HNK:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:00.1 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:01.0 Ethernet controller [0200]: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) [8086:101e] (rev 03)
02:02.0 Network controller [0280]: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]
hnk@HNK:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"Wifi"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:9C:D1:67:8B   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/100  Signal level=-56 dBm  Noise level=-90 dBm
          Rx invalid nwid:4906  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24831   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"Wifi"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:9C:D1:67:8B   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/100  Signal level=-56 dBm  Noise level=-90 dBm
          Rx invalid nwid:4906  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24831   Missed beacon:0

hnk@HNK:~$ rfkill list all
hnk@HNK:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
dm_crypt               22463  0 
pcmcia                 39671  0 
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
thinkpad_acpi          73750  0 
joydev                 17322  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
nsc_ircc               23199  0 
ppdev                  12849  0 
snd_timer              28659  2 snd_pcm,snd_seq
yenta_socket           27230  0 
irda                  185091  1 nsc_ircc
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_rsrc            18292  1 yenta_socket
airo                   73165  0 
psmouse                73312  0 
snd                    55295  12 snd_intel8x0,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
parport_pc             32111  1 
nvram                  14035  1 thinkpad_acpi
shpchp                 32345  0 
serio_raw              12990  0 
crc_ccitt              12595  1 irda
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
radeon                900494  2 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
drm                   184164  4 radeon,ttm,drm_kms_helper
e1000                 101089  0 
video                  18951  0 
floppy                 60032  0 
i2c_algo_bit           13184  1 radeon


```And the code nm_geo requested:

```


hnk@HNK:~$ rfkill list all
hnk@HNK:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"Wifi"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:9C:D1:67:8B   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/100  Signal level=-56 dBm  Noise level=-91 dBm
          Rx invalid nwid:6763  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:43739   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"Wifi"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:9C:D1:67:8B   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/100  Signal level=-56 dBm  Noise level=-91 dBm
          Rx invalid nwid:6763  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:43739   Missed beacon:0

hnk@HNK:~$ dmesg | grep airo
[   22.607702] airo(): Probing for PCI adapters
[   22.607772] airo 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   22.607798] airo(): Found an MPI350 card
[   23.616483] airo(eth1): Firmware version 5.41.00
[   23.616488] airo(eth1): WPA supported.
[   23.616493] airo(eth1): MAC enabled 00:02:8a:fc:eb:27
[   23.621450] airo(): Finished probing for PCI adapters
[  438.450555] airo(eth1): link lost (local choice)
[  446.452154] airo(eth1): link lost (local choice)
[  454.456333] airo(eth1): link lost (local choice)
[  462.459962] airo(eth1): link lost (local choice)
[  470.458171] airo(eth1): link lost (local choice)


```

Thanks for the help so far!

---

### Post by praseodym on 2011-09-05
Hi,

this card doesnt support WPA or WPA2 encryption, choose WEP instead.

Oh, sorry:

> ```
[   23.616483] airo(eth1): Firmware version 5.41.00
[   23.616488] airo(eth1): WPA supported.
```
Obviously this firmware version does support WPA, but imho no WPA2.

---

### Post by shivers222 on 2011-09-05
That explains why I can't connect to the WPA2 network. Any idea about why my card seems to stop being able to detect any network it's not connected to shortly after booting?

---

### Post by wildmanne39 on 2011-09-05
Hi, try resetting your router then we will go from there.
Thank you

---

### Post by shivers222 on 2011-09-05
This is an issue that I've had in various locations and with multiple networks so I don't believe it's a problem with my router... My other computers are detecting the wireless networks normally, it's just this one that is having issues.

If I get it connected to the network then it stays connected until I tell it to disconnect so I'm not sure what's going on.

---

### Post by wildmanne39 on 2011-09-05
Hi, install nm-tool and see if it will tell us anything.
Thank you

---

### Post by wildmanne39 on 2011-09-05
Hi, also try
```
sudo modprobe airo_cs
```
don't restart your computer afterwards this is a one time only command if it works we will need to make it persistent.

I am in new territory here so we are experimenting but if it does not work the changes will go away when you reboot.
Thank you

---

### Post by vycas on 2011-10-10
Hey all, I am having the similiar problem on my itronix IX260. Its a old system. I am running XP and Natty on it. Wireless is working flawlessly on XP and no issues of any kind.

In natty my wireless is enabled and i can see my network. But when i try to connect it, it tries for like 30 seconds and then says disconnected. My network stays there whole time, just that every time i try to connect to it, it tries for 30 seconds and then says wireless disconnected.

Following is the output of basic commands:


```
vycas@vycas-IX260:~$ sudo lshw -C network
```
[sudo] password for vycas: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: *************
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.8 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 ioport:ac00(size=256) memory:dfefff00-dfefffff
  *-network:1 DISABLED
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth1
       version: 00
       serial: ****************
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=32 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:a800(size=256) memory:dfef8000-dfefbfff memory:df800000-dfbfffff memory:dfc00000-dfdfffff
```
vycas@vycas-IX260:~$ nm-tool
```

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        **************

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.8
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             10.0.0.1


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            airo
  State:             disconnected
  Default:           no
  HW Address:        **************

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes

  Wireless Access Points 
    Vycas:           Infra, ***************, Freq 2412 MHz, Rate 11 Mb/s, Strength 100


```
vycas@vycas-IX260:~$ lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #2 [8086:2484] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801CA/CAM SMBus Controller [8086:2483] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M6 LY [1002:4c59]
03:05.0 CardBus bridge [0607]: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972]
03:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
03:07.0 CardBus bridge [0607]: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972]
03:08.0 Network controller [0280]: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]
```
vycas@vycas-IX260:~$ iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-101 dBm  Noise level=-95 dBm
          Rx invalid nwid:420  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:731   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-101 dBm  Noise level=-95 dBm
          Rx invalid nwid:420  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:731   Missed beacon:0

```
vycas@vycas-IX260:~$ rfkill list all
```
```
vycas@vycas-IX260:~$ lsmod
```
Module                  Size  Used by
binfmt_misc            13213  1 
snd_intel8x0           33213  2 
radeon                900494  3 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
ppdev                  12849  0 
pcmcia                 39671  0 
snd_timer              28659  2 snd_pcm,snd_seq
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
drm                   184164  5 radeon,ttm,drm_kms_helper
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
yenta_socket           27230  0 
parport_pc             32111  1 
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
airo                   73165  0 
video                  18951  0 
i2c_scmi               12885  0 
serio_raw              12990  0 
i2c_algo_bit           13184  1 radeon
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
8139too                23208  0 
8139cp                 22497  0 
```
vycas@vycas-IX260:~$ dmesg | grep airo
```
[   15.306456] airo(): Probing for PCI adapters
[   15.306823] airo 0000:03:08.0: PCI INT A -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[   15.306870] airo(): Found an MPI350 card
[   17.172370] airo(eth1): Firmware version 5.41.00
[   17.172377] airo(eth1): WPA supported.
[   17.172384] airo(eth1): MAC enabled ****************
[   17.219813] airo(): Finished probing for PCI adapters

Please advise.

Vycas

---

### Post by praseodym on 2011-10-10
Hi vycas,

which kind of encryption do you use? This Cisco device obviously only supports WPA, not mixed WPA/WPA2 or pure WPA2:

> [ 17.172377] airo(eth1): WPA supported.
depending on the firmware version. Try this, or WEP

---

### Post by praseodym on 2011-10-10
P.S.: There are 2 LAN drivers loaded:

```
echo "blacklist 8139cp" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

and reboot.

---

### Post by vycas on 2011-10-10
> **praseodym said:**
> P.S.: There are 2 LAN drivers loaded:

```
echo "blacklist 8139cp" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

and reboot.

Thanks for helping me. I am not using any encryption. I am using MAC address filtering on my router. Tried blacklisting. Still same issue.

Vycas

---

### Post by praseodym on 2011-10-11
Maybe the address filtering causes the problem.

---

### Post by vycas on 2011-10-11
> **praseodym said:**
> Maybe the address filtering causes the problem.

This is a dual boot machine with XP and NATTY and network works perfectly fine in XP. Only in NATTY its giving me issues.

Vycas

---

### Post by praseodym on 2011-10-11
Try Wicd instead of the network-manager:

```
wget [http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz](http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz)
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Choose **wifi0** as wireless interface and **wext** as driver. Try no, WEP, and WPA encryption. Deactivate "connect automatically" in the NM and the applet in "autostart". Maybe it has to be uninstalled _completely_.

---

