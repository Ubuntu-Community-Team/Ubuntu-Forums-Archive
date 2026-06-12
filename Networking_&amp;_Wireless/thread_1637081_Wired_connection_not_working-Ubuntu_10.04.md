---
title: "Wired connection not working-Ubuntu 10.04"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by iisr on 2010-12-04
Hi. I am a complete newbie to Ubuntu. I installed Ubuntu 10.04 on my  Dell 1564. My cabled network connection is not working.
Ubuntu has been  dual booted with Windows 7. 
Internet connection on Windows is working. I  have an ADSL modem connected to my laptop via the cable.
I have given  the details of commands asked to be execute(viewed various posts).

 [FONT=&quot]isr@ISR:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
isr@ISR:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:26:b9:23:31:8c
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:32 ioport:3000(size=256) memory:f0410000-f0410fff(prefetchable) memory:f0400000-f040ffff(prefetchable) memory:f0420000-f043ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 4
       logical name: wlan0
       serial: c4:17:fe:c7:ed:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
isr@ISR:~$ lsusb
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 007: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 006: ID 0c45:6461 Microdia 
Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
isr@ISR:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_realtek   203310  1 
arc4                    1153  2 
dell_wmi                1793  0 
snd_hda_intel          21941  2 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
b43                   163523  0 
snd_seq_dummy           1338  0 
mac80211              205146  1 b43
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               56990  0 
videodev               34361  1 uvcvideo
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24119  0 
video                  17375  0 
output                  1871  1 video
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
v4l1_compat            13251  2 uvcvideo,videodev
dell_laptop             6856  0 
cfg80211              126517  2 b43,mac80211
led_class               2864  1 b43
psmouse                63245  0 
serio_raw               3978  0 
vga16fb                11385  1 
dcdbas                  5422  1 dell_laptop
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
agpgart                31724  1 intel_agp
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
usb_storage            39425  0 
ahci                   32200  1 
ssb                    38671  1 b43
r8169                  34076  0 
mii                     4381  1 r8169
isr@ISR:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:b9:23:31:8c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:32 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6080 (6.0 KB)  TX bytes:6080 (6.0 KB)

isr@ISR:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
isr@ISR:~$ ndiswrapper -1
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common

[/FONT]

---

### Post by northd_tech on 2010-12-04
> **iisr said:**
> [FONT=&quot]** lspci**
04:00.0 Network controller: [COLOR=Red]Broadcom Corporation BCM4312 [/COLOR]802.11b/g (rev 01)
05:00.0 Ethernet controller: **Realtek** Semiconductor Co., Ltd.** RTL8101E/RTL8102E **PCI Express Fast Ethernet controller (rev 02)

**  sudo lshw -C network**
  *-network               
       description: Network controller
       product: [COLOR=Red]BCM4312[/COLOR] 802.11b/g
       vendor: [COLOR=Red]Broadcom [/COLOR]Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product:** RTL8101E/RTL8102E** PCI Express Fast Ethernet controller
       vendor:** Realtek** Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:26:b9:23:31:8c
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:32 ioport:3000(size=256) memory:f0410000-f0410fff(prefetchable) memory:f0400000-f040ffff(prefetchable) memory:f0420000-f043ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 4
       logical name: wlan0
       serial: c4:17:fe:c7:ed:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

**  lsmod**
Module                  Size  Used by
[COLOR=Red]b43[/COLOR]                   163523  0 
snd_seq_dummy           1338  0 
mac80211              205146  1[COLOR=Red] b43[/COLOR]
ssb                    38671  1[COLOR=Red] b43[/COLOR]
**r8169                  34076  0 **
mii                     4381  1 [B]r8169

  ifconfig[/B]
eth0      Link encap:Ethernet  HWaddr 00:26:b9:23:31:8c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:32 Base address:0xa000 

  **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
[/FONT]
It looks like you have a Realtek 8101E/8102E ethernet controller and a Broadcom 4312 wireless network controller (which does not appear to be working either- and I highlighted the wireless stuff in [COLOR=Red]red[/COLOR] above). 

My Broadcom 4321AG can use the same Linux modules as yours (at a slower speed), but I have had the best luck using the "Broadcom STA" driver for mine- I just go into System > Administration > Hardware Drivers and activate the Broadcom STA Wireless Driver (under 10.04 Lucid Lynx as well as 9.04 Jackalope).  Here are some threads tagged with Broadcom STA and Broadcom 4312:
[http://ubuntuforums.org/tags.php?tag=broadcom+4312](http://ubuntuforums.org/tags.php?tag=broadcom+4312)

[http://ubuntuforums.org/tags.php?tag=broadcom+sta](http://ubuntuforums.org/tags.php?tag=broadcom+sta)

There appear to be some recent issues with the Broadcom 4312 and Ubuntu 10.xx, but I would get rid of that "[COLOR=Red]b43[/COLOR]" stuff above and just try the STA driver.  You would need to open a terminal and enter the following command:

```
sudo rmmod b43
```before activating the STA driver to prevent a conflict.  You might also need to "blacklist" the[COLOR=Red] b43[/COLOR] module(s) to prevent them from loading at startup- I think the file locations are different under 10.xx so I would just search the forum for "Broadcom + blacklist"

As far as the Realtek 8101E/8102E cabled connection, all the threads at this forum on that 8101E/8102E that I found are over a year old which leads me to suspect that there should be built-in kernel support.  (since 2007: confirmed by the following post, if correct:
[http://www.linuxforums.org/forum/728584-post2.html](http://www.linuxforums.org/forum/728584-post2.html) )

The Realtek "**r8169**" module(s) look to be loaded and probably correct for a newer Realtek ethernet card IIRC, but it might be worth searching this forum for Realtek 8168 or Realtek 8169 (I believe that the newer generations are backwards-compatible, but don't quote me on that).

If your cable ethernet connection isn't working, I would try rebooting into BIOS and making sure that your [onboard?] ethernet adapter is enabled.  If it is, check the lights on your router and/or network cable receptacle to make sure they are lit up.  If another computer (or another OS on that computer) is available, I would try to connect using the same cable and port to make sure it isn't a network problem rather than an Ubuntu problem (since the Realtek 8101E claims to have built-in kernel support).

Edit:  I just re-read above and saw that your connection** is** working under Win7.  Try unplugging then plugging in your network cable while Ubuntu is running- that has often worked for me.  It is possible that the Network Manager has been corrupted somehow if you still cannot connect.   If it is still not working, can you post some screenshots of what the Network Manager looks like when you click it open or any error messages?

I actually prefer "wicd" to the Gnome Network Manager, but "wicd" required uninstalling the default network connection manager.  It might be worth a try if nothing else has worked:

[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

---

