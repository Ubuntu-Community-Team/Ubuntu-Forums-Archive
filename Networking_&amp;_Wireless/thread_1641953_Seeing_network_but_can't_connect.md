---
title: "Seeing network but can't connect"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by Exentric90 on 2010-12-09
Hello all.

*Before I explain my problem:*
This is my first post so I do apologize if this post is in the wrong category. Also I would like to apologize for my bad English because my native language is Dutch. I know there are allot of the same topics. but I can't find a right solution for my problem

*My problem:*
After using Ubuntu 10.04 for a while I decided to upgrade to Ubuntu 10.10. After the upgrade and restart the problems started. I wasn't able to connect to my WPA secured network. This was because there was no network in the list to connect to. I installed ndiswrapper, and installed a Windows driver. Blacklisted the old one and yes.  This worked. Then the next morning exactly the same problem. I tried to repeat the same process. To bad. This time it didn't worked. I removed the old driver from the blacklist. and tried to update. No luck at all.
I searched the forums. I figured to get a list with networks. but when I click mine and enter the pass-phrase it says it's connecting but keeps asking for the pass-phrase, then eventually disconnect.

**lsmod**
```
michael@michael-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_via82xx            20058  2 
gameport                9089  1 snd_via82xx
snd_via82xx_modem       8486  5 
snd_ac97_codec        100646  2 snd_via82xx,snd_via82xx_modem
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
vga16fb                11385  0 
snd_mpu401_uart         5617  1 snd_via82xx
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  6 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
vgastate                8961  1 vga16fb
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
pcmcia                 30784  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
arc4                    1153  2 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                676897  3 
snd_timer              19098  2 snd_pcm,snd_seq
i2c_viapro              5573  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
rtl8180                26378  0 
joydev                  8708  0 
via_ircc               21745  0 
drm_kms_helper         29329  1 radeon
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    54180  24 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mpu401_uart,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              205402  1 rtl8180
eeprom_93cx6            1333  1 rtl8180
drm                   162409  5 radeon,ttm,drm_kms_helper
via_agp                 5310  1 
snd_page_alloc          7076  3 snd_via82xx,snd_via82xx_modem,snd_pcm
irda                  186556  1 via_ircc
video                  17375  0 
ppdev                   5259  0 
soundcore               6620  1 snd
rndis_host              5756  0 
psmouse                63245  0 
agpgart                31724  3 ttm,drm,via_agp
i2c_algo_bit            5028  1 radeon
cfg80211              126528  2 rtl8180,mac80211
lp                      7028  0 
crc_ccitt               1339  1 irda
output                  1871  1 video
cdc_ether               3541  1 rndis_host
parport_pc             25962  1 
usbnet                 14943  2 rndis_host,cdc_ether
serio_raw               3978  0 
shpchp                 28820  0 
parport                32635  3 ppdev,lp,parport_pc
led_class               2864  0 
firewire_ohci          21002  0 
via_rhine              19154  0 
floppy                 53016  0 
pata_via                7272  3 
mii                     4381  2 usbnet,via_rhine
firewire_core          44510  1 firewire_ohci
crc_itu_t               1371  1 firewire_core
```

**lshw**
```
michael@michael-laptop:~$ sudo lshw
[sudo] password for michael: 
michael-laptop            
    description: Notebook
    product: Aspire 1350
    vendor: Acer,Inc.
    version: 3A25
    serial: LXA100559343301AC9EF15
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=oem-specific chassis=notebook uuid=60A72397-5CED-D811-9F9A-00C09F408A39
  *-core
       description: Motherboard
       product: Aspire 1350
       vendor: Acer,Inc.
       physical id: 0
       version: Rev.A
       serial: None
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: 3A29 (07/29/2004)
          size: 117KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect edd int13floppy1200 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile AMD Athlon(tm) XP 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: U23
          size: 796MHz
          capacity: 796MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back unified
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 256MiB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: M3
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:e0000000-efffffff(prefetchable)
        *-pci
             description: PCI bridge
             product: VT8235 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:d0100000-d01fffff memory:d8000000-dfffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: M9+ 5C61 [Radeon Mobility 9200 (AGP)]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:4 memory:d8000000-dfffffff(prefetchable) ioport:9000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff(prefetchable)
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:5 memory:28000000-28000fff ioport:2400(size=256) ioport:2800(size=256) memory:20000000-23ffffff(prefetchable) memory:24000000-27ffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
             resources: irq:5 memory:d0004000-d00047ff memory:d0000000-d0003fff
        *-network:0 DISABLED
             description: Wireless interface
             product: RTL8180L 802.11b MAC
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: wlan0
             version: 20
             serial: 00:0b:6b:29:50:89
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11b
             resources: irq:9 ioport:1000(size=256) memory:d0004800-d00048ff
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:4 ioport:2000(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:5 ioport:2020(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:9 ioport:2040(size=32)
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:11 memory:d0004c00-d0004cff
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=64
             resources: irq:4 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:2060(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG HM080HC
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: AM10
                serial: S0CCJD0P754396
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000e13c5
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 9a1ddace-c002-4f8d-9364-0e94631273ee
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-12-07 02:28:11 filesystem=ext4 lastmountpoint=/5&#65533;&#65533;&#65533;|&#1928;P&#1984;6&#65533;&#1488;]1&#2037;m &#65533;]l/&#65533;&#65533;]1&#2030;!&#65533;&#65533;sT&#2040;sT&#65533;|&#65533;&#65533;]1&#2028;]1&#65533;]p modified=2010-12-09 22:55:19 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-12-10 01:25:19 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /usr
                      capacity: 35GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1953MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: UJ-840D
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:9 ioport:1400(size=256)
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0
             resources: irq:9 ioport:1800(size=256)
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:c0:9f:40:8a:39
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
             resources: irq:4 ioport:1c00(size=256) memory:d0005000-d00050ff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 2a:96:fc:b5:46:ba
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.77.136 link=yes multicast=yes

```

**nm-tool**
```
michael@michael-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8180
  State:             unavailable
  Default:           no
  HW Address:        00:0B:6B:29:50:89

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             unavailable
  Default:           no
  HW Address:        00:C0:9F:40:8A:39

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: usb0  [Auto usb0] ----------------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        2A:96:FC:B5:46:BA

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.77.136
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.77.254

    DNS:             192.168.77.254


```

I did check for updates. And I did check the blacklist file. I think this is a easy one for U all. But I can't really figure it out. If you need more info please do ask :)

Thanks in advance :)

---

### Post by azwar on 2010-12-09
Looking at your lshw, your wlan0 state is DISABLED (which is not turn on) and the driver rtl8180 is loaded and okay.

Just try to remove Ndis driver (you can easily restore them later) then run in terminal > sudo modprobe rtl8180 && sudo ifconfig wlan0 up

Then try to scan a network with this command to check your wireless card scanning result
> sudo iwlist wlan0 scan

---

### Post by Exentric90 on 2010-12-10
> **azwar said:**
> Looking at your lshw, your wlan0 state is DISABLED (which is not turn on) and the driver rtl8180 is loaded and okay.

Just try to remove Ndis driver (you can easily restore them later) then run in terminal 

Then try to scan a network with this command to check your wireless card scanning result


Okay I disabled the Ndis driver. I executed both commands after that. When I execute the sudo wlan0 scan command it gives me a list of current networks where I can connect to. Still when I try, it keeps trying to connect but doesnt actually connect.

*This is what it says by the way:*
> michael@michael-laptop:~$ sudo modprobe rtl8180 && sudo ifconfig wlan0 up
michael@michael-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:24:17:DB:DE:4F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=195/100  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"ThomsonB25911"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002438391141
                    Extra: Last beacon: 1588ms ago
                    IE: Unknown: 000D54686F6D736F6E423235393131
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010E86594902D6651B6812BEB979A4D2EF2103C000101
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          [B]Cell 02 - Address: 00:0C:F6:4C:0E:34
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=193/100  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"Sitecom4C0E34"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=0000015de8ce8161
                    Extra: Last beacon: 312ms ago
                    IE: Unknown: 000D53697465636F6D344330453334
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880000CF64C0E34103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010015127A
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000[/B]
          Cell 03 - Address: C0:3F:0E:50:56:84
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=195/100  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Ziggo258582"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003fd2b68c183
                    Extra: Last beacon: 948ms ago
                    IE: Unknown: 000B5A6967676F323538353832
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1606071300000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406071300000000000000000000000000000000000000
          Cell 04 - Address: 00:1D:19:D8:B8:0D
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=195/100  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"WLAN_D8B80B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000088c123132d
                    Extra: Last beacon: 640ms ago
                    IE: Unknown: 000B574C414E5F443842383042
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 07064E4C20010D14
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
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000001D19D8B80D021D19D8B80D64002C010808


The bold one is mine.

---

### Post by Exentric90 on 2010-12-10
Now my lshw doesn't say it's Disabled.

```

michael@michael-laptop:~$ sudo lshw
michael-laptop            
    description: Notebook
    product: Aspire 1350
    vendor: Acer,Inc.
    version: 3A25
    serial: LXA100559343301AC9EF15
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=oem-specific chassis=notebook uuid=60A72397-5CED-D811-9F9A-00C09F408A39
  *-core
       description: Motherboard
       product: Aspire 1350
       vendor: Acer,Inc.
       physical id: 0
       version: Rev.A
       serial: None
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: 3A29 (07/29/2004)
          size: 117KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect edd int13floppy1200 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile AMD Athlon(tm) XP 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: U23
          size: 796MHz
          capacity: 796MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back unified
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 256MiB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: M3
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:e0000000-efffffff(prefetchable)
        *-pci
             description: PCI bridge
             product: VT8235 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:d0100000-d01fffff memory:d8000000-dfffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: M9+ 5C61 [Radeon Mobility 9200 (AGP)]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:4 memory:d8000000-dfffffff(prefetchable) ioport:9000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff(prefetchable)
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:5 memory:28000000-28000fff ioport:2400(size=256) ioport:2800(size=256) memory:20000000-23ffffff(prefetchable) memory:24000000-27ffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
             resources: irq:5 memory:d0004000-d00047ff memory:d0000000-d0003fff
        *-network:0
             description: Wireless interface
             product: RTL8180L 802.11b MAC
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: wlan0
             version: 20
             serial: 00:0b:6b:29:50:89
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11b
             resources: irq:9 ioport:1000(size=256) memory:d0004800-d00048ff
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:4 ioport:2000(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:5 ioport:2020(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:9 ioport:2040(size=32)
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:11 memory:d0004c00-d0004cff
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=64
             resources: irq:4 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:2060(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG HM080HC
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: AM10
                serial: S0CCJD0P754396
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000e13c5
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 9a1ddace-c002-4f8d-9364-0e94631273ee
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-12-07 02:28:11 filesystem=ext4 lastmountpoint=/&#65533;z&#65533;&#770;s&#1928;&#65533;J&#65533;&#65533;&#65533;&#1492;^t&#1973;m &#65533;]l/&#65533;&#65533;^t&#1966;!&#65533;`6m&#65533;`6m&#1986;s&#65533;&#65533;^t&#1968;^t&#65533;]p modified=2010-12-09 22:55:19 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,commit=600,barrier=1,data=ordered mounted=2010-12-10 12:41:22 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /usr
                      capacity: 35GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,commit=600,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1953MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: UJ-840D
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:9 ioport:1400(size=256)
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0
             resources: irq:9 ioport:1800(size=256)
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:c0:9f:40:8a:39
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
             resources: irq:4 ioport:1c00(size=256) memory:d0005000-d00050ff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 2a:96:fc:b5:46:ba
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.77.136 link=yes multicast=yes

```

But still I can't connect. Also it's weird because I can't seem to find my wlan-chip in my lspci. I can only find my Ethernet adapter.

*lspci:*
```


michael@michael-laptop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)

```

---

### Post by grahammechanical on 2010-12-10
Your wlan-chip is in lspci. It is the bit that says:
> 00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)Are you sure that you are entering the correct pass-phrase? Have you re-booted? Sometimes a re-boot is needed so that changes to configuration files are acted on.

regards.

---

### Post by Exentric90 on 2010-12-10
> **grahammechanical said:**
> Your wlan-chip is in lspci. It is the bit that says:
Are you sure that you are entering the correct pass-phrase? Have you re-booted? Sometimes a re-boot is needed so that changes to configuration files are acted on.

regards.

Ah okay if that is the line it is in lspci. And yes i'm 100% sure it is the correct pass-phrase. I did rebooted several times when changing configurations. It still won't connect. It just keeps asking for a pass-phrase. An I enter the same one on my phone. Which I'm using for tethering right now, So the pass-phrase is correct. Any sugestions?

---

### Post by Exentric90 on 2010-12-10
You guys won't believe this. It was hard-blocked. So the problem is a bit less complicated now. When I pushed the button to unblock it. It connected. But the disconnected. I tried to connect again, and it connected. Then it shows there was no signal. (then again I'm 2 meters away from it.) and it disconnects again. Any solution?

---

### Post by Exentric90 on 2010-12-10
Hmm, I think I fixed it. Thanks for helping anyways. This is what I did:

I removed all old drivers and ndiswrapper. Then I rebooted. Did ```
sudo apt-get build-essential
``` Did ```
sudo apt-get update
``` and downloaded the Realtek RTL8180L drivers. Compiled them. And did ```
sudo make install
``` I rebooted. And viola it works!

---

