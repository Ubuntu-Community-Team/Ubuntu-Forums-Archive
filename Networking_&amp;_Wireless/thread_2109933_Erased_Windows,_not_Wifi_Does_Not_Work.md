---
title: "Erased Windows, not Wifi Does Not Work"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by coldnovember on 2013-01-28
I brought an HP 2000 Notebook PC on black friday in '12.
it had windows 8 preinstalled so swapped it for 64 bit ubuntu 11.04 and ungraded it to  to 12.10 using a wired connection. The wireless has not been working since i installed Ubuntu initially and it had been working with windows 8.Please help. My terminal window is saying:

cam@cam-HP-2000-Notebook-PC:~$ lspci -nn | grep 0280
06:00.0 Network controller [0280]: Ralink corp. Device [1814:539b]
cam@cam-HP-2000-Notebook-PC:~$

Can someone please help me on this issue as I have been trying to fix this for days and am stuck spinning my gears. Thanks in advance

---

### Post by coldnovember on 2013-01-28
I have tried the following commands.

lspci -nnk lsusb lsmod iwconfig rfkill list

and this is what was returned...


cam@cam-HP-2000-Notebook-PC:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 14h Processor Root Complex [1022:1510]
	Subsystem: Hewlett-Packard Company Device [103c:169a]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310] [1002:9802]
	Subsystem: Hewlett-Packard Company Device [103c:169a]
	Kernel driver in use: radeon
	Kernel modules: radeon
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4394]
	Subsystem: Hewlett-Packard Company Device [103c:169a]
	Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Subsystem: Hewlett-Packard Company Device [103c:169a]
	Kernel driver in use: ohci_hcd
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Subsystem: Hewlett-Packard Company Device [103c:169a]
	Kernel driver in use: ehci_hcd
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Subsystem: Hewlett-Packard Company Device [103c:169a]
	Kernel driver in use: ohci_hcd
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Subsystem: Hewlett-Packard Company Device [103c:169a]
	Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 42)
	Subsystem: Hewlett-Packard Company Device [103c:169a]
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
	Subsystem: Hewlett-Packard Company Device [103c:169a]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
	Subsystem: Hewlett-Packard Company Device [103c:169a]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:15.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:15.1 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) [1002:43a1]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:15.2 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2) [1002:43a2]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3 [1022:1703]
	Kernel driver in use: k10temp
	Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7 [1022:1719]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:169a]
	Kernel driver in use: r8169
	Kernel modules: r8169
06:00.0 Network controller [0280]: Ralink corp. Device [1814:539b]
	Subsystem: Hewlett-Packard Company Device [103c:18ed]
	Kernel modules: wl
07:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:169a]
	Kernel driver in use: rts_pstor
	Kernel modules: rts_pstor
cam@cam-HP-2000-Notebook-PC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05c8:0348 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
cam@cam-HP-2000-Notebook-PC:~$ lsmod
Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180153  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_codec_idt      70795  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
radeon                804518  3 
ttm                    76949  1 radeon
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
joydev                 17693  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   3074895  0 
drm_kms_helper         46978  1 radeon
snd                    79041  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
drm                   241971  5 radeon,ttm,drm_kms_helper
hp_wmi                 18092  0 
v4l2_compat_ioctl32    17128  1 videodev
rts_pstor             445241  0 
sparse_keymap          13890  1 hp_wmi
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sp5100_tco             13791  0 
psmouse                97485  0 
lib80211               14381  1 wl
serio_raw              13211  0 
k10temp                13166  0 
i2c_piix4              13301  0 
mac_hid                13253  0 
i2c_algo_bit           13423  1 radeon
wmi                    19256  1 hp_wmi
video                  19596  0 
rt2800pci              18715  0 
rt2800lib              58967  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55326  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506862  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205774  3 wl,rt2x00lib,mac80211
eeprom_93cx6           12767  1 rt2800pci
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62154  0 
cam@cam-HP-2000-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

cam@cam-HP-2000-Notebook-PC:~$ rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
cam@cam-HP-2000-Notebook-PC:~$ 


I am stuck guys. Please help!

---

### Post by Bucky Ball on 2013-01-28
Now try:
```

sudo lshw -C network
```... and post the output.

Have you tried looking in Additional Drivers?

PS: Please use code tags [] at the beginning with 'code' inside and [/] at the end, ditto. It is easier to read. You can also click 'Go Advanced', mark out the code and click the # icon. Also, please divide the output from the different commands with code tags. Some potential helpers will simply move along when faced with a huge blob of terminal output like that above so you will improve your chances of help. Thanks.

---

### Post by coldnovember on 2013-01-28
Sorry, this my first day posting here! Thanks! Here is the output that i got:



```


[/cam@cam-HP-2000-Notebook-PC:~$ sudo lshw -C network
[sudo] password for cam: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: c8:cb:b8:00:a8:8d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=10.80.55.50 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f020ffff
cam@cam-HP-2000-Notebook-PC:~$ 



```

---

### Post by Bucky Ball on 2013-01-28
All good. Much easier on the eye and welcome to the forums.

Have you checked Additional Drivers? If there is a driver in there for the card, enable it. You may need to restart after that. You should do an update with a cable if you haven't done already (presuming the cable works as it looks like it should). You can use Update Manager or, in a terminal, run these two commands one after the next:

```
sudo apt-get update
sudo apt-get upgrade
```This will only upgrade what you have installed, if required, NOT the current release of Ubuntu to the next. ;)

Odd that it is giving no info on your card apart from: Ralink corp. Device and 
product: Ralink corp.        vendor: Ralink corp.

The driver is missing but hard to know which you need when won't give us the model.

---

### Post by coldnovember on 2013-01-28
Does this help??

```


cam@cam-HP-2000-Notebook-PC:~$ lspci -nn | grep 0280
06:00.0 Network controller [0280]: Ralink corp. Device [1814:539b]
cam@cam-HP-2000-Notebook-PC:~$ 


```

---

### Post by coldnovember on 2013-01-28
I have tried additional drivers. Nothing.

---

### Post by Bucky Ball on 2013-01-28
> **coldnovember said:**
> Does this help??

```


cam@cam-HP-2000-Notebook-PC:~$ lspci -nn | grep 0280
06:00.0 Network controller [0280]: Ralink corp. Device [1814:539b]
cam@cam-HP-2000-Notebook-PC:~$ 


```

Nope. No model. What is the make/model of your laptop?

EDIT: Actually, yes. It appears the last four digits, 539b, are it. Still digging ...

---

### Post by coldnovember on 2013-01-28
HP 2000-bf69WM

---

### Post by Bucky Ball on 2013-01-29
This is the driver you need:

[http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001)

Stick in any details and you will be offered the driver for download.

---

### Post by coldnovember on 2013-01-29
thanks. now how do i go about installing it? Once again, im not that good with terminal. im still used to .exe files lol.

---

### Post by chili555 on 2013-01-29
Hey, Bucky, what do you think about this??> 06:00.0 Network controller [0280]: Ralink corp. Device [1814:539b]
Subsystem: Hewlett-Packard Company Device [103c:18ed]
[COLOR="Red"]Kernel modules: wl[/COLOR]Yikes!

I suggest you do:```
sudo apt-get remove --purge bcmwl-kernel-source
```Reboot and tell us if there is any improvement.

I actually think the correct driver is loaded:> rt2800pci 18715 0
rt2800lib 58967 1 [COLOR="Red"]rt2800pci[/COLOR]
crc_ccitt 12707 1 rt2800lib
rt2x00pci 14577 1 rt2800pci
rt2x00lib 55326 3 rt2800pci,rt2800lib,rt2x00pci
mac80211 506862 3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211 205774 3 wl,rt2x00lib,mac80211
eeprom_93cx6 12767 1 rt2800pciHowever, the incorrect wl is evidently interfering.

---

### Post by Bucky Ball on 2013-01-29
I think nicely spotted and, as is common with these things, you are probably right. wl would make a difference and wl would be getting in the way.

---

### Post by coldnovember on 2013-01-29
Thanks guys, but no change. i did the reinstallation of the wl but it still isnt working. checked to see if it was blocked and it says unblocked hard and soft. im completely losst as to what to do now.

---

### Post by coldnovember on 2013-01-29
under network, does there need to be anything other than wired and network proxy showing?

---

### Post by coldnovember on 2013-01-29
Just an attemp to give you guy asmuch info possible to make it easier for you to help me...

HP 2000-bf69WM

```


cam@cam-HP-2000-Notebook-PC:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 14h Processor Root Complex [1022:1510]
    Subsystem: Hewlett-Packard Company Device [103c:169a]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310] [1002:9802]
    Subsystem: Hewlett-Packard Company Device [103c:169a]
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_experimental_9, radeon
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4394]
    Subsystem: Hewlett-Packard Company Device [103c:169a]
    Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Hewlett-Packard Company Device [103c:169a]
    Kernel driver in use: ohci_hcd
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Hewlett-Packard Company Device [103c:169a]
    Kernel driver in use: ehci_hcd
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Hewlett-Packard Company Device [103c:169a]
    Kernel driver in use: ohci_hcd
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Hewlett-Packard Company Device [103c:169a]
    Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 42)
    Subsystem: Hewlett-Packard Company Device [103c:169a]
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: Hewlett-Packard Company Device [103c:169a]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: Hewlett-Packard Company Device [103c:169a]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:15.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:15.1 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) [1002:43a1]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:15.2 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2) [1002:43a2]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3 [1022:1703]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7 [1022:1719]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:169a]
    Kernel driver in use: r8169
    Kernel modules: r8169
06:00.0 Network controller [0280]: Ralink corp. Device [1814:539b]
    Subsystem: Hewlett-Packard Company Device [103c:18ed]
07:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:169a]
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor
cam@cam-HP-2000-Notebook-PC:~$ 


```
```


cam@cam-HP-2000-Notebook-PC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05c8:0348 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 1058:0748 Western Digital Technologies, Inc. 
Bus 001 Device 006: ID 04e8:681d Samsung Electronics Co., Ltd Galaxy Portal/Spica Android Phone
cam@cam-HP-2000-Notebook-PC:~$ 


```
```

cam@cam-HP-2000-Notebook-PC:~$ lsmod
Module                  Size  Used by
rndis_host             13848  0 
cdc_ether              13536  1 rndis_host
usbnet                 26212  2 rndis_host,cdc_ether
ses                    17417  0 
enclosure              15312  1 ses
uas                    18180  0 
usb_storage            49198  1 
joydev                 17693  0 
parport_pc             32866  0 
ppdev                  17113  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180153  10 bnep,rfcomm
binfmt_misc            17540  1 
snd_hda_codec_idt      70795  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rts_pstor             445241  0 
psmouse                97485  0 
serio_raw              13211  0 
snd                    79041  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k10temp                13166  0 
v4l2_compat_ioctl32    17128  1 videodev
vfat                   17585  1 
fat                    61512  1 vfat
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sp5100_tco             13791  0 
i2c_piix4              13301  0 
fglrx                5190126  156 
video                  19596  0 
wmi                    19256  1 hp_wmi
mac_hid                13253  0 
rt3290sta            1182379  0 
rt2800pci              18715  0 
rt2800lib              58967  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55326  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506862  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205774  2 rt2x00lib,mac80211
eeprom_93cx6           12767  1 rt2800pci
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62154  0 
cam@cam-HP-2000-Notebook-PC:~$ 


```
```

cam@cam-HP-2000-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

eth0      no wireless extensions.


```
```

cam@cam-HP-2000-Notebook-PC:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
cam@cam-HP-2000-Notebook-PC:~$ 


```


Also. tried removing wl, no help. all the function keys work, but the wifi one, but it isnt hard block. additional drivers does not pull up anything relevant. Im so lost.

---

### Post by chili555 on 2013-01-29
>  i did the reinstallation of the wl but it still isnt working. We didn't ask you to reinstall wl. We requested:> sudo apt-get **remove --purge** bcmwl-kernel-source...which *REMOVES* wl. Also, where did this come from? Have you been busy trying a few other solutions???> [COLOR="Red"]rt3290sta[/COLOR]            1182379  0 
rt2800pci              18715  0 
rt2800lib              58967  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55326  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506862  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205774  2 rt2x00lib,mac80211
eeprom_93cx6           12767  1 rt2800pciYou don't want or need rt3290sta. Until we can get rt2800pci and its cousins *ONLY*, we are unlikely to make any progress.

---

