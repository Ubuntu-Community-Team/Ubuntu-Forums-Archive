---
title: "UGGGHHH !! Wireless setup for this dummy please"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by mustangman198129650 on 2009-05-26
I'm running 9.04 on a homebuilt media center PC

I am attempting to get my usb wireless adapter to function, but after reading countless threads where those seeking help are re-directed to tutorials that totally confuse me, I humbly ask that someone give me the "for dummies" version.  My linux skills go as far as the ability to follow a step by step walkthrough, copying and pasting code as i go.  PLEASE HELP

wireless adapter: Linksys WUSB54GC, RT73 chipset, I have the drivers downloaded from Ralink on my desktop 2009_0206_RT73_Linux_STA_Drv1.1.0.2.tar.bz2

mark@mark-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.3 Co-processor: nVidia Corporation MCP73 Co-processor (rev a2)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)
01:06.0 Multimedia audio controller: Creative Labs SB X-Fi
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GS (rev a2)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

mark@mark-desktop:~$ lsusb
Bus 001 Device 004: ID 13fe:1f00 Kingston Technology Company Inc. DataTraveler 2.0 4GB Flash Drive
Bus 001 Device 002: ID 1737:0077 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

mark@mark-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

mark@mark-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
usb_storage            82880  1 
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
ppdev                  15620  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
pcspkr                 10496  0 
serio_raw              13316  0 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
joydev                 18368  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
hid_sunplus            10112  0 
usbhid                 42336  0 
r8169                  40836  0 
mii                    13312  1 r8169
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

mark@mark-desktop:~$ sudo lshw -C network
[sudo] password for mark: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:01:2e:24:03:97
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.15 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b6:09:c6:6c:e0:7d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


I have given as much info as my limited skills can gather, hoping someone is feeling altruistic enough to help me out so i can get boxee up and running on this box and start streaming my content instead of having to rely on SATAN (my cable company) for entertainment. This sireless issue is the only one i foresee needing help on, so please help me get this thing wireless. :)

---

### Post by chili555 on 2009-05-26
I believe the package *linux-backports-modules-jaunty-generic* has the needed module, rt73usb, included in it. Please open a terminal and do:```
sudo apt-get install linux-backports-modules-jaunty-generic
```After that, please detach your ethernet cable and do:```
sudo ifdown eth0
sudo modprobe rt73usb
```Does your wireless spring to life?

---

### Post by mustangman198129650 on 2009-05-26
the first line of code seemed to install that missing module, however i got this when i tried the last two commands,

mark@mark-desktop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
mark@mark-desktop:~$ sudo modprobe rt73usb
mark@mark-desktop:~$ 

thoughts?

---

### Post by chili555 on 2009-05-27
Now does the wireless interface show up in the Network Manager icon? Does:```
iwconfig
```show your wireless interface?

---

### Post by colli012 on 2009-05-27
Thanks for helping.  Just tried the steps.  Still doesn't work.  This is what happened.

ellie@ellie-desktop:~$ sudo ifdown eth0
Ignoring unknown interface eth0=eth0.

ellie@ellie-desktop:~$ sudo modprobe rt73usb
WARNING: Error inserting input_polldev (/lib/modules/2.6.28-11-generic/kernel/drivers/input/input-polldev.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting led_class (/lib/modules/2.6.28-11-generic/kernel/drivers/leds/led-class.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-11-generic/updates/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.28-11-generic/updates/rt2x00usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting crc_itu_t (/lib/modules/2.6.28-11-generic/kernel/lib/crc-itu-t.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt73usb (/lib/modules/2.6.28-11-generic/updates/rt73usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)

ellie@ellie-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=1 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Trying to install the drivers to make my WUSB54GC v.1 work.  Does anyone else have some ideas.  Thanks

---

### Post by chili555 on 2009-05-27
> Unknown symbol in module, or unknown parameter (see dmesg)Let's find out. Please do:```
dmesg | grep rt73usb
```Let's see what the error might be.

---

### Post by mustangman198129650 on 2009-05-27
mark@mark-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

mark@mark-desktop:~$ 

thats what i get after running iwconfig

---

### Post by superprash2003 on 2009-05-30
post output of **sudo iwlist scanning** and post the contents of the /etc/network/interfaces file

---

