---
title: "Ubuntu 12.10 freezes on connecting to wireless network. D-Link DWA-548 PCIe adapter."
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by Korejora on 2013-02-17
I installed a wireless adapter in my desktop the other day, and installed a driver for it, and got it to work. Unfortunately, whenever it connects to the wi-fi network, everything freezes and I have to reset. (I tried connecting to my phone as a wi-fi hotspot, and it stayed connected without freezing, but that didn't have any internet connection.) How can I figure out what's going wrong? 


Adapter:
D-Link DWA-548 Wireless N 300 PCI Express Desktop Adapter

Driver:
[http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001)

```

  

$ lspci
03:00.0 Network controller: Ralink corp. Device 5392


$ ifconfig
ra0       Link encap:Ethernet  HWaddr c8:be:19:06:dd:5b  
          inet6 addr: fe80::cabe:19ff:fe06:dd5b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:438079 (438.0 KB)  TX bytes:0 (0.0 B)
          Interrupt:18


$ iwconfig
ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated  
          Bit Rate:1 Mb/s  
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


$ lsmod | grep rt
parport_pc             32689  0
rt5390sta            1456547  1
rt2800pci              18529  0
rt2800lib              58731  1 rt2800pci
crc_ccitt              12708  1 rt2800lib
rt2x00pci              14476  1 rt2800pci
rt2x00lib              54939  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              539958  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              206797  2 rt2x00lib,mac80211
eeprom_93cx6           13345  1 rt2800pci
parport                46346  3 parport_pc,ppdev,lp


$ dmesg | grep rt5
[   25.884409]  [<ffffffffa0f9b710>] RtmpAsicSendCommandToMcu+0x780/0x8b0 [rt5390sta]
[   25.884416]  [<ffffffffa0f9af90>] ? RtmpAsicLoadFirmware+0x170/0x170 [rt5390sta]
[   25.884425]  [<ffffffffa0f1bb59>] AsicSendCommandToMcuBBP+0x29/0x30 [rt5390sta]
[   25.884431]  [<ffffffffa0eef3e9>] NICInitBBP+0x12c9/0x2b10 [rt5390sta]
[   25.884439]  [<ffffffffa0ef12eb>] NICInitializeAsic+0x30b/0x5b0 [rt5390sta]
[   25.884444]  [<ffffffffa0ef1729>] NICInitializeAdapter+0x199/0x6b0 [rt5390sta]
[   25.884450]  [<ffffffffa0ef8b14>] rt28xx_init+0x2a4/0x710 [rt5390sta]
[   25.884458]  [<ffffffffa0f775c5>] rt28xx_open+0x95/0x100 [rt5390sta]
[   25.884466]  [<ffffffffa0f08ef3>] RTMP_COM_IoctlHandle+0x543/0x5a0 [rt5390sta]
[   25.884475]  [<ffffffffa0f76fe7>] MainVirtualIF_open+0x47/0xe0 [rt5390sta]
[   25.884482]  [<ffffffffa0f77530>] ? RtmpOSIRQRequest+0xe0/0xe0 [rt5390sta]
[   25.884488]  [<ffffffffa0f76f10>] ? RtmpNetEthConvertDevSearch+0x90/0x90 [rt5390sta]


$ dmesg | grep rt2 
[   23.708897] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x5392 detected.
[   23.708959] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   23.809258] register rt2860
[   25.884450]  [<ffffffffa0ef8b14>] rt28xx_init+0x2a4/0x710 [rt5390sta]
[   25.884458]  [<ffffffffa0f775c5>] rt28xx_open+0x95/0x100 [rt5390sta]
[   26.003685] <==== rt28xx_init, Status=0
[   26.037551] <==== rt28xx_init, Status=0
[   26.218885] <==== rt28xx_init, Status=0
[   26.244215] <==== rt28xx_init, Status=0


$ sudo lshw -C network
  *-network              
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: ra0
       version: 00
       serial: c8:be:19:06:dd:5b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN latency=0 multicast=yes wireless=Ralink STA
       resources: irq:18 memory:f7300000-f730ffff


$ iwlist scan
          Cell 01 - Address: 5C:D9:98:6B:90:DA
                    Protocol:802.11b/g/n
                    ESSID:"Network"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality=83/100  Signal level=-57 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000110104400010210470010000000000000100000005CD9986B90DA103C000103


$ lsb_release -d
Description:    Ubuntu 12.10


$ uname -mr
3.5.0-23-generic x86_64


-

```

---

### Post by praseodym on 2013-02-18
You didnt blacklist the old module:
```

echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -rfv rt5390sta
sudo modprobe -v rt5390sta
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by Korejora on 2013-02-18
After inputting your commands, the old module no longer gives errors, but the wireless connecting to the internet still freezes everything. 

```
 
$ lsmod | grep rt
parport_pc             32689  0 
rt5390sta            1456547  0 
parport                46346  3 parport_pc,ppdev,lp

$ dmesg | grep rt2
[   20.278133] register rt2860
[   29.045187]  [<ffffffffa0dbeb14>] rt28xx_init+0x2a4/0x710 [rt5390sta]
[   29.045195]  [<ffffffffa0e3d5c5>] rt28xx_open+0x95/0x100 [rt5390sta]
[   29.106130] <==== rt28xx_init, Status=0
[   29.214030] <==== rt28xx_init, Status=0
[  246.755238] <==== rt28xx_init, Status=0

```

---

### Post by praseodym on 2013-02-19
Maybe a VGA driver issue? What card is shown with:
```

lspci -nnk | grep VGA
lsmod
cat /etc/X11/xorg.conf
```
Do you use proprietary VGA drivers?

---

### Post by Korejora on 2013-02-19
Yes, as far as I know. So far I've just activated whatever jockey decided to list. 

Thanks for your help with this, by the way. 

```
$ lspci -nnk | grep VGA
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:11c0] (rev a1)


$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory


$ lsmod
Module                  Size  Used by
nls_utf8               12558  1 
udf                    89521  1 
crc_itu_t              12708  1 udf
pci_stub               12623  1 
vboxpci                23195  0 
vboxnetadp             25671  0 
vboxnetflt             23480  0 
vboxdrv               287190  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18141  2 
rfcomm                 46620  12 
parport_pc             32689  0 
ppdev                  17074  0 
binfmt_misc            17501  1 
snd_hda_codec_hdmi     32049  1 
rt5390sta            1456547  1 
eeepc_wmi              13110  0 
asus_wmi               24089  1 eeepc_wmi
sparse_keymap          13891  1 asus_wmi
btusb                  22475  0 
mxm_wmi                13022  0 
coretemp               13401  0 
snd_hda_codec_realtek    78048  1 
bluetooth             209249  22 bnep,rfcomm,btusb
kvm                   414071  0 
ghash_clmulni_intel    13221  0 
snd_usb_audio         130468  1 
snd_usbmidi_lib        24954  1 snd_usb_audio
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
joydev                 17458  0 
microcode              22804  0 
snd_hda_intel          33492  5 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  2 snd_usb_audio,snd_hda_codec
ndiswrapper           283324  0 
snd_seq_midi           13325  0 
snd_pcm                96668  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_rawmidi            30513  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13206  0 
video                  19336  0 
snd                    78921  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia              11263008  41 
wmi                    19071  2 asus_wmi,mxm_wmi
psmouse                95595  0 
serio_raw              13216  0 
lpc_ich                17062  0 
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
mei                    40691  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
r8169                  61651  0 
```

---

### Post by praseodym on 2013-02-19
```
ndiswrapper           283324  0 
```
Uninstall ndiswrapper completely:
```

sudo modprobe -rfv ndiswrapper
sudo modprobe -rfv rt5390sta
sudo modprobe -v rt5390sta
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper/*
```

---

### Post by Korejora on 2013-02-19
Connecting still froze after removing ndiswrapper.

Also, ndiswrapper reappears there whenever I restart. Is that normal? 

```
$ sudo modprobe -rfv ndiswrapper
rmmod /lib/modules/3.5.0-23-generic/misc/ndiswrapper.ko


$ sudo modprobe -rfv rt5390sta
rmmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/rt5390sta.ko


$ sudo modprobe -v rt5390sta
insmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/rt5390sta.ko


$ sudo apt-get remove --purge ndisgtk ndiswrapper*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'ndiswrapper-modules-1.9' for regex 'ndiswrapper*'
Note, selecting 'ndiswrapper-utils' for regex 'ndiswrapper*'
Note, selecting 'ndiswrapper-common' for regex 'ndiswrapper*'
Note, selecting 'ndiswrapper-source' for regex 'ndiswrapper*'
Note, selecting 'ndiswrapper-utils-1.9' for regex 'ndiswrapper*'
Note, selecting 'ndiswrapper-dkms' for regex 'ndiswrapper*'
Package 'ndiswrapper-utils' is not installed, so not removed
Package 'ndisgtk' is not installed, so not removed
Package 'ndiswrapper-common' is not installed, so not removed
Package 'ndiswrapper-utils-1.9' is not installed, so not removed
Package 'ndiswrapper-dkms' is not installed, so not removed
Package 'ndiswrapper-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.


$ sudo rm /etc/modprobe.d/ndis*
rm: cannot remove `/etc/modprobe.d/ndis*': No such file or directory


$ sudo rm -r /etc/ndiswrapper/*
rm: cannot remove `/etc/ndiswrapper/*': No such file or directory
```

---

### Post by praseodym on 2013-02-19
Check:
```

cat /etc/modules
```
After unloading/reloading the drivers, try:
```

sudo depmod -a
sudo update-initramfs -u
```

---

### Post by Korejora on 2013-02-19
Yes, ndiswrapper was in there. I've removed ndiswrapper now, and it doesn't reappear any more. 

Still freezing, though. 

```
$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc
rt5390sta


$ sudo depmod -a


$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic
```

---

### Post by praseodym on 2013-02-20
Install the compiling tools and kernel-headers:
```

sudo apt-get install --reinstall linux-headers-generic build-essential dkms
```
After that change to the 1st terminal with CTRL+ALT+T, and create a xorg.conf file. Login and:
```

sudo service lightdm stop
sudo nvidia-xconfig --configure
sudo service lightdm start
```
Reboot.

---

### Post by Korejora on 2013-02-20
The command doesn't seem to have worked. 

```
$ sudo service lightdm stop
lightdm stop/waiting


$ sudo nvidia-xconfig --configure
nvidia-xconfig: unrecognized option: "--configure"

Invalid commandline, please run `nvidia-xconfig --help` for usage information.


$ sudo service lightdm start
lightdm start/running, process 2945

```

---

### Post by praseodym on 2013-02-21
```
sudo nvidia-xconfig --[COLOR="Red"]composite[/COLOR]
```
Sorry.

---

### Post by Korejora on 2013-02-21
OK. 

```
$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 304.51  (buildmeister@swio-display-x86-rhel47-08.nvidia.com)  Tue Sep 18 18:26:36 PDT 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by praseodym on 2013-02-21
Looks good. Check, if it still freezes.

---

### Post by Korejora on 2013-02-21
Sorry, I've tested after each change, but I've been forgetting to report. It still freezes.

---

### Post by praseodym on 2013-02-22
Try to reinstall the VGA driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) nvidia-current build-essential dkms
```
Reboot. Did you try to boot without the stick being plugged in? I had similar issues with 12.04 but some update did the job.

---

### Post by Korejora on 2013-02-22
It still freezes after reinstalling and rebooting. I don't know what you mean by "the stick".

---

### Post by praseodym on 2013-02-23
Sorry, confused. Do you have any USB-device plugged in during the boot-up?

---

### Post by Korejora on 2013-02-23
My mouse and my keyboard are plugged in via USB. The other USB ports are empty.

---

### Post by praseodym on 2013-02-23
Is it a desktop PC or a laptop/notebook? If its a desktop, try to remove the module
```

sudo rmmod eeepc_wmi
```

---

### Post by Korejora on 2013-02-23
It's a desktop. Still froze after removing the module.

---

### Post by praseodym on 2013-02-23
Uninstall the driver via:
```

make clean
make
sudo make uninstall
```
And try this version with dkms:

[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742)

First line should be modified to:```

sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms
```

---

### Post by Korejora on 2013-02-23
There was a lot of output to copy from these commands, so I saved it in a text file instead of posting it here. 

When I tried connecting to the internet, the freezing process was much slower this time. I was able to access a small, mostly-text website before it partially froze (sound stuttered; I was able to move the cursor, but not much on the interface would respond to clicks; no keyboard commands would work). Actually, I tried several times, and one or two times, it gave me an error window before it completely froze (could not move the cursor at all). I took a photo of the frozen screen so I could transcribe: 

> [Connection failure]
[B]Connection activation failed
[/B](4) Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. I tried a few more times, and when it started to freeze, I quickly tried to disable the wireless and disconnect from the wi-fi network. This time, it gave a nearly identical message before freezing completely:

> [Disconnect failure]
**Device disconnect failed**
(4) Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by praseodym on 2013-02-24
Can you upload the textfile?

---

### Post by Korejora on 2013-02-24
[http://pastebin.com/nmdn5QN6](http://pastebin.com/nmdn5QN6)

---

### Post by praseodym on 2013-02-24
Did you shutdown and wait for about 5 minutes (currentless!)? Check then:
```

sudo iwlist scan
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
iwlist chan
ifconfig -a
iwconfig
rfkill list
lsmod
```

---

### Post by Korejora on 2013-02-25
OK, I turned it off completely, unplugged the power cable, and waited 5-10 minutes before plugging it back in and turning it on again for the next step. 

```
$ sudo iwlist scan
ra0       Scan completed :
          Cell 01 - Address: 5C:D9:98:6B:90:DA
                    Protocol:802.11b/g/n
                    ESSID:"Network"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality=94/100  Signal level=-53 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000110104400010210470010000000000000100000005CD9986B90DA103C000103
          Cell 02 - Address: 42:D9:98:6B:90:DA
                    Protocol:802.11b/g
                    ESSID:"LFN Guest"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality=83/100  Signal level=-57 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 03 - Address: 00:1B:63:2A:E5:C0
                    Protocol:802.11b/g/n
                    ESSID:"Apple Network 2ae5c0"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/100  Signal level=-67 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 64:70:02:8F:08:08
                    Protocol:802.11b/g/n
                    ESSID:"coopernet"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality=63/100  Signal level=-65 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000101

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.



$ cat /etc/network/interfaces 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


$ iwlist chan
ra0       11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)

eth0      no frequency information.

lo        no frequency information.


$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 10:bf:48:b8:b9:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26752 (26.7 KB)  TX bytes:26752 (26.7 KB)

ra0       Link encap:Ethernet  HWaddr c8:be:19:06:dd:5b  
          inet6 addr: fe80::cabe:19ff:fe06:dd5b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86753 (86.7 KB)  TX bytes:0 (0.0 B)
          Interrupt:18 


$ iwconfig
ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.



$ rfkill list


$ lsmod
Module                  Size  Used by
nls_utf8               12558  1 
udf                    89521  1 
crc_itu_t              12708  1 udf
bnep                   18141  2 
parport_pc             32689  0 
rfcomm                 46620  0 
bluetooth             209249  10 bnep,rfcomm
ppdev                  17074  0 
binfmt_misc            17501  1 
nvidia              11257760  41 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
snd_hda_intel          33492  5 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         130468  1 
coretemp               13401  0 
snd_usbmidi_lib        24939  1 snd_usb_audio
snd_hwdep              17699  2 snd_hda_codec,snd_usb_audio
kvm                   414071  0 
snd_pcm                96668  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_seq_midi           13325  0 
snd_rawmidi            30513  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
rt5390sta            1354165  1 
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
eeepc_wmi              13110  0 
asus_wmi               24089  1 eeepc_wmi
sparse_keymap          13891  1 asus_wmi
ghash_clmulni_intel    13221  0 
mei                    40691  0 
aesni_intel            51038  0 
joydev                 17458  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
psmouse                95595  0 
mac_hid                13206  0 
snd                    78921  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19391  0 
mxm_wmi                13022  0 
lp                     17760  0 
wmi                    19071  2 asus_wmi,mxm_wmi
lpc_ich                17062  0 
aes_x86_64             17256  1 aesni_intel
serio_raw              13216  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
parport                46346  3 parport_pc,ppdev,lp
microcode              22804  0 
soundcore              15048  1 snd
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
r8169                  61651  0



```Still freezing.

---

### Post by praseodym on 2013-02-25
Uninstall the package "reolvconf" and reboot.

---

### Post by Korejora on 2013-02-26
```
$ sudo apt-get remove reolvconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package reolvconf

$ sudo apt-get remove resolvconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  resolvconf ubuntu-minimal
0 upgraded, 0 newly installed, 2 to remove and 7 not upgraded.
After this operation, 303 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 321926 files and directories currently installed.)
Removing ubuntu-minimal ...
Removing resolvconf ...
resolvconf stop/waiting
resolvconf.postrm: Reboot recommended
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...

```Still freezes.

---

