---
title: "No Wifi Ubuntu 11.10 on Hp dv9700"
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by EssJohnson on 2012-01-04
**[COLOR=DarkSlateBlue]I have not been able to fix this problem. I did a few things to try on my own that I read on similar threads. I don't really understand what I'm doing as such. I looked at Additional Drivers and messed around with synaptic package manager. Yesterday it was working for a few hours, but after coming back home found that it was again not working and haven't been able to get it to. As such I can not remember the steps I took to get it working for the short time that it was. Please help me. [/COLOR]**


```
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:fa:29:e7  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fefa:29e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1609 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1463665 (1.4 MB)  TX bytes:304951 (304.9 KB)
          Interrupt:41 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:314743 (314.7 KB)  TX bytes:314743 (314.7 KB)

birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.HP-Pavilion-dv9700-Notebook-PC:~$ 

birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ lsmod
Module                  Size  Used by
usb_storage            44173  0 
uas                    17699  0 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
nvidia              10390874  32 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_conexant    52418  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
binfmt_misc            17292  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
mtd                    35852  2 sm_common,nand
k8temp                 12905  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
r592                   17808  0 
psmouse                73673  0 
serio_raw              12990  0 
memstick               15857  1 r592
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 hp_wmi
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
forcedeth              58103  0 
ahci                   21634  1 
libahci                25727  1 ahci
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ lsmod
Module                  Size  Used by
usb_storage            44173  0 
uas                    17699  0 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
nvidia              10390874  32 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_conexant    52418  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
binfmt_misc            17292  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
mtd                    35852  2 sm_common,nand
k8temp                 12905  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
r592                   17808  0 
psmouse                73673  0 
serio_raw              12990  0 
memstick               15857  1 r592
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 hp_wmi
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
forcedeth              58103  0 
ahci                   21634  1 
libahci                25727  1 ahci
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ 
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ sudo lshw -C network
[sudo] password for birdy: 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:fa:29:e7
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.2.3 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 memory:f6388000-f6388fff ioport:30f8(size=8) memory:f6389c00-f6389cff memory:f6389800-f638980f

birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ lsb_release -d
Description:    Ubuntu 11.10

birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ uname -mr
3.0.0-14-generic i686
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$  sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ 

```

---

### Post by praseodym on 2012-01-04
Hi,

there is no device listed in "lspci". Check your BIOS settings if it can be activated there. Dont hesitate to reset the BIOS to manufacturer settings. Show after that:

```
lspci -nnk | grep -iA2 net
lsusb
pccardctl info
rfkill list
lsmod
```

---

### Post by EssJohnson on 2012-01-04
> **praseodym said:**
> Hi,

there is no device listed in "lspci". Check your BIOS settings if it can be activated there. Dont hesitate to reset the BIOS to manufacturer settings. Show after that:

```
lspci -nnk | grep -iA2 net
lsusb
pccardctl info
rfkill list
lsmod
```

In Bios I pressed F9 to reset defaults. I assume I did what you said right. Here is terminal.

```
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:30cf]
    Kernel driver in use: forcedeth
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ pccardctl info
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ pccardctl info
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ rfkill list
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ rfkill list
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
nvidia              10390874  32 
snd_hda_codec_conexant    52418  1 
binfmt_misc            17292  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
r592                   17808  0 
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
mtd                    35852  2 sm_common,nand
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
serio_raw              12990  0 
memstick               15857  1 r592
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
k8temp                 12905  0 
wmi                    18744  1 hp_wmi
i2c_nforce2            12906  0 
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
sdhci_pci              13658  0 
hid                    77367  1 usbhid
sdhci                  27360  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
forcedeth              58103  0 
ahci                   21634  1 
libahci                25727  1 ahci
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ 

```

---

### Post by TBABill on 2012-01-04
There is no wireless device listed in those outputs. It's possible it's an internal usb device. Could you run ```
lsusb
```and see if it shows a wireless device?

---

### Post by EssJohnson on 2012-01-04
> **TBABill said:**
> There is no wireless device listed in those outputs. It's possible it's an internal usb device. Could you run ```
lsusb
```and see if it shows a wireless device?

[COLOR=Navy]I don't understand because wireless worked fine..some times finnicky up until 8 days ago. 
[/COLOR]```
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ l susb
ls: cannot access susb: No such file or directory
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ 


```

---

### Post by wildmanne39 on 2012-01-04
Hi, I asked the same questions from you in this thread.
[http://ubuntuforums.org/showthread.php?p=11585269#post11585269](http://ubuntuforums.org/showthread.php?p=11585269#post11585269)
The way it looks is like the wireless card is going out because it did not show up in the information you posted for me in the other thread either.

I am going to let the people that started helping you here finish helping you because they may have more solutions .
Thanks

---

### Post by TBABill on 2012-01-04
Looks like the system is not seeing the device, which indicates it is probably faulty (not a driver issue, but a problem or failure in the device itself). I just had this happen on the wired NIC on my older laptop. It quit working and was no longer seen in my lspci output either.

---

### Post by praseodym on 2012-01-05
Check another slot (if there is a card inside)

---

### Post by EssJohnson on 2012-01-06
> **praseodym said:**
> Check another slot (if there is a card inside)

Slot???

---

### Post by Basher101 on 2012-01-06
what he means is a mini-pci slot that some laptops have at the side (it is about 6 mm high and 5 cm long)

---

