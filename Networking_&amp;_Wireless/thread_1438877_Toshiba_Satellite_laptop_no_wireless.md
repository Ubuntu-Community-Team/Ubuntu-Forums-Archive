---
title: "Toshiba Satellite laptop no wireless"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by BRFC on 2010-03-25
I wonder if someone could help me get the wireless working on my mum's laptop as having to plug it into the router everytime she wants to go online is now becoming an issue for her. I recently upgraded it from 8.04 to 9.04 and thought that might help solve it but unfortunately not.  Ive tried using the Windows Wireless Driver option in System - Admin but to no avail.  Any help gratefully received, details below.
 

Laptop Toshiba Satellite L300D-13D


$ lspci, returns the following

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

ifconfig, gives this;

eth0      Link encap:Ethernet  HWaddr 00:1e:33:87:a1:c5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:250 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7272 (7.2 KB)  TX bytes:7272 (7.2 KB)

iwconfig and I get;

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

$ lsmod
Module                  Size  Used by
ndiswrapper           193436  0 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_hda_intel         436148  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               63368  0 
compat_ioctl32          9344  1 uvcvideo
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2081668  31 
soundcore              15200  1 snd
videodev               41600  1 uvcvideo
psmouse                61972  0 
agpgart                42696  1 fglrx
pcspkr                 10496  0 
v4l1_compat            21764  2 uvcvideo,videodev
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
serio_raw              13444  0 
video                  25872  0 
output                 11008  1 video
input_polldev          11912  0 
shpchp                 40212  0 
i2c_piix4              18448  0 
usb_storage            99648  1 
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


$ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

---

### Post by bkratz on 2010-03-25
Is her wireless card a USB device? It doesn't seem to even show up above. Please also post the outputs of 

lsusb
ndiswrapper -l
dmesg | grep -e wlan -e ndis

( both of those were lowercase "L" not 1's.  use the code tags (#) above to make it readable.)

---

### Post by BRFC on 2010-03-25
lsusb

Bus 002 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8198 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ndiswrapper -l

net8185 : driver installed

dmesg |grep -e wlan -e ndis


[   13.943757] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.706797] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,12/26/2007,5.1116.1226.2007) loaded
[   18.288832] wlan0: ethernet device 00:21:63:bb:2a:1d using NDIS driver: net8187b, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0BDA:8198.F.conf
[   18.288865] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   18.288912] usbcore: registered new interface driver ndiswrapper
[   39.584043] wlan0: no IPv6 routers present
[  342.272852] usbcore: deregistering interface driver ndiswrapper
[  342.364388] ndiswrapper: device wlan0 removed
[  342.381780] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  342.688651] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,12/26/2007,5.1116.1226.2007) loaded
[  346.290860] wlan0: ethernet device 00:21:63:bb:2a:1d using NDIS driver: net8187b, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0BDA:8198.F.conf
[  346.290967] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  346.291110] usbcore: registered new interface driver ndiswrapper
[  360.640530] wlan0: no IPv6 routers present
[ 6948.838389] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7067.612136] usbcore: deregistering interface driver ndiswrapper
[ 7068.516972] ndiswrapper: device wlan0 removed
[ 7068.555948] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 7068.620517] usbcore: registered new interface driver ndiswrapper
[ 8413.559015] usbcore: deregistering interface driver ndiswrapper
[ 8413.590167] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 8413.620153] usbcore: registered new interface driver ndiswrapper

---

### Post by bkratz on 2010-03-25
This one is the wireless card.

Bus 001 Device 003: ID 0bda:8198 Realtek Semiconductor Corp. 

I am looking through various threads about this right now, but could you also post

sudo lshw -C network

while I look.

---

### Post by bkratz on 2010-03-25
managed to get a duplicate post sorry.

---

### Post by BRFC on 2010-03-25
sudo lshw -C network
 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:87:a1:c5
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:ba:e1:5e:47:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by bkratz on 2010-03-25
Well I'm afraid my search will take a while. It seems like most people who have had any luck with this patched the rtl8187b driver already inherrent since earlier versions than yours. It bothers me that it doesn't show up at all in your last posting.  could there be a switch or keystroke combination that turns it off: or could it be disabled in the bios?

---

### Post by BRFC on 2010-03-25
There is a small switch on the front of the machine to turn the wireless on/off but that is in the on position all the time, I've checked the bios and there is nothing in there that seems to suggest its turned off.

Thanks for any help you find, without wireless my mum is going to have to use the Vista install side of her dual boot laptop but at 65 she's not keen to change from something (Ubuntu) that she has been used to for four years.  If you do happen to find anything you would make an old lady very happy and I would be in your debt.  Mum has health issues which have taken their toll on her mobility and her laptop is her link to everyone and everything she loves.  Again cheers for the help.

---

### Post by daemonkorn on 2010-03-25
what kind of router are you using and isp provider as well?

---

### Post by BRFC on 2010-03-25
The computer is currently at my house where the ISP is BT and the router is the BT branded router supplied by BT.


Mum's
isp is Virgin
Router is Netgear DG834G if I remember rightly

Both networks have various other bits of kit and computers connected wirelessly to them and functioning fine.

---

### Post by bkratz on 2010-03-25
> **BRFC said:**
> There is a small switch on the front of the machine to turn the wireless on/off but that is in the on position all the time, I've checked the bios and there is nothing in there that seems to suggest its turned off.

Thanks for any help you find, without wireless my mum is going to have to use the Vista install side of her dual boot laptop but at 65 she's not keen to change from something (Ubuntu) that she has been used to for four years.  If you do happen to find anything you would make an old lady very happy and I would be in your debt.  Mum has health issues which have taken their toll on her mobility and her laptop is her link to everyone and everything she loves.  Again cheers for the help.

Found this about the driver, maybe worth looking at

[http://www.doc.ic.ac.uk/~pgp/personal/logs/r8198-wifi.html](http://www.doc.ic.ac.uk/~pgp/personal/logs/r8198-wifi.html)

Also this

[http://sourceforge.net/projects/rtl-wifi/forums/forum/652149/topic/2389615](http://sourceforge.net/projects/rtl-wifi/forums/forum/652149/topic/2389615)

---

### Post by moaoci on 2010-03-25
I saw post [http://ubuntuforums.org/showpost.php?p=6079637&postcount=40](http://ubuntuforums.org/showpost.php?p=6079637&postcount=40) that might do it for you

> But the compat-wireless drivers (for >--2.26.27) from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) seem to be working great. The files / drivers are far more intact and you nolonger need to edit the source code to point it towards the chipset like in 8.04.

If after loading the drivers you restart and the wireless doesn't work try it again with the 'switch' on the front turned off.**You may also want to contact realtek support** at  [EMAIL="nicfae@realtek.com"]nicfae@realtek.com[/EMAIL] with output from lspci and dmesg to see what driver you need.  Don't hesitate to write to realtek support for help, they provide excellent service for linux users (and it's free of charge). 

For your information, RTL8192E is a driver that is not available for download at Realtek but they do have one that works and they send it on demand.  Maybe they have one like that for your   0dba.8198 usb driver.  If they have one and it doesn't work for you, tell them, they will try to solve the problem.

---

### Post by BRFC on 2010-04-14
Sorry its has been a while but I just wanted to thank all those for their help, my mum now has a working wireless card and is very happy.  Once again thanks for all the advice.

Cheers

Chris

---

### Post by bkratz on 2010-04-14
> **BRFC said:**
> Sorry its has been a while but I just wanted to thank all those for their help, my mum now has a working wireless card and is very happy.  Once again thanks for all the advice.

Cheers

Chris

I've seen others looking for a solution to that same device. 0dba.8198
If you don't mind expanding did you find your answer in one of the threads or somewhere else?  You might also want to go to the thread tools and mark as [solved] in case it helps someone else.

---

