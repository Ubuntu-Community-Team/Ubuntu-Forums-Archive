---
title: "Impossible wireless connection on Ubuntu LTS 10.04"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by virtual phenix on 2010-06-05
Hi everybody,
I am a new user of  Ubuntu, I installed the latest version 10.04 LTS, everything works great  (sound, video, bluetooth, ...) except the wireless, because my wireless  connection was not detected. 

I use a laptop DELL  Vostro 1015 
My network card is Dell  Wireless 1397 Mini-Card 
The manufacturer is  Broadcom (BCM4312) 

The site  [http://linux-wless.passys.nl](http://linux-wless.passys.nl) proposed in the literature shows my  configuration in red and wrote: 
"Currently no native  driver exists for this device" 

I checked the BIOS,  everything is enabled 

I suppose that these commands can give you some informations:

cat /etc/lsb-release
lsusb
lspci
lspci -nn | grep -i net
sudo  lshw -C network
lsmod
iwconfig
ifconfig
sudo iwlist scan

uname  -r -m 

cat  /etc/network/interfaces

nm-tool

so this is what i got:

```
bk@bk-laptop:~$ cat /etc/lsb-release


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


bk@bk-laptop:~$ lsusb


Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 5986:01a2 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


bk@bk-laptop:~$ lspci


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0f:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
0f:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
0f:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)


bk@bk-laptop:~$ lspci -nn | grep -i net


09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)


bk@bk-laptop:~$ sudo lshw -C network


  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 00:26:b9:20:55:fc
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:30 ioport:ce00(size=256) memory:f0204000-f0204fff(prefetchable) memory:f0200000-f0203fff(prefetchable) memory:f0220000-f023ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: c4:17:fe:57:f9:6c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


bk@bk-laptop:~$ lsmod


Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
hidp                   11083  0 
hid                    67032  1 hidp
rfcomm                 33421  4 
binfmt_misc             6587  1 
ppdev                   5259  0 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  17 hidp,rfcomm,bnep
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
mmc_block               8258  2 
joydev                  8708  0 
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  1 snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               56990  0 
b43                   157218  0 
dell_wmi                1793  0 
i915                  282354  3 
snd                    54148  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
mac80211              204922  1 b43
drm_kms_helper         29297  1 i915
dell_laptop             6856  0 
dcdbas                  5422  1 dell_laptop
btusb                  10925  2 
bluetooth              49892  10 hidp,rfcomm,sco,bnep,l2cap,btusb
psmouse                63245  0 
serio_raw               3978  0 
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
cfg80211              126485  2 b43,mac80211
led_class               2864  2 b43,sdhci
drm                   162471  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
intel_agp              24177  2 i915
agpgart                31724  2 drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
r8169                  33884  0 
mii                     4381  1 r8169
ieee1394               81181  1 ohci1394
ssb                    37336  1 b43
ahci                   32008  3 


bk@bk-laptop:~$ iwconfig


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.



bk@bk-laptop:~$ ifconfig


eth0      Link encap:Ethernet  HWaddr 00:26:b9:20:55:fc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:30 Adresse de base:0xa000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:185 erreurs:0 :0 overruns:0 frame:0
          TX packets:185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:21212 (21.2 KB) Octets transmis:21212 (21.2 KB)



bk@bk-laptop:~$ sudo iwlist scan



lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.



bk@bk-laptop:~$ 


bk@bk-laptop:~$ uname -r -m
2.6.32-21-generic i686
bk@bk-laptop:~$ 


bk@bk-laptop:~$ cat  /etc/network/interfaces


auto lo
iface lo inet loopback

bk@bk-laptop:~$ 
bk@bk-laptop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        C4:17:FE:57:F9:6C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:26:B9:20:55:FC

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: 00:1D:28:7A:D9:FD ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:


bk@bk-laptop:~$
```

Thank you for all your answers

---

### Post by kahnoie on 2010-06-17
Hi,
I am stuck in exactly the same boat as you. I have a HP DV6-1330 laptop with a broadcom wireless adapter and I upgraded from 9.10 to 10.04 TLS thinking that my WiFi would work. But It doesn't. I first tried to install the proprietary drivers - B43 and STA, one by one (uninstalling one before reinstalling the other). But none of them seem to work.

sudo lshw -C network
*-network               
 description: Network controller
 product: BCM4312 802.11b/g
 vendor: Broadcom Corporation
 physical id: 0
 bus info: pci@0000:02:00.0
 version: 01
 width: 64 bits
 clock: 33MHz
 capabilities: pm msi pciexpress bus_master cap_list
 configuration: driver=b43-pci-bridge latency=0
 resources: irq:16 memory:d9000000-d9003fff

*-network
 description: Wireless interface
 physical id: 2
 logical name: wlan0
 serial: 0c:60:76:44:a6:4a
 capabilities: ethernet physical wireless
 configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

lspci -nn | grep BCM
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

uname -a
Linux amit-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

I also tried to download the official broadcom drivers. But they too didnt work!!

---

### Post by Shazzam6999 on 2010-06-17
I don't know what happened but I'm pretty sure it worked out of the box in 9.10, if you're not feeling really motivated I'm sure it still works out of the box in 9.10.

This is a bit of an obnoxious method but as far as I know it works, this is what I have to do in Arch at least. The b43 driver should work.

```
sudo iwconfig wlan0 power on
sudo ifconfig wlan0 up
at this point you should be able to scan
sudo iwconfig wlan0 essid *network name* key *network passwd*
dhclient wlan0 (I actually use dhcpcd but I think this is still the right command)
```

Just replace wlan0 with whatever your wireless interface is and if that doesn't work post back here and we'll figure it out.

---

### Post by frenetico on 2010-07-05
Broadcom's README.txt file for its proprietary driver provides installation instructions for both Fedora and Ubuntu. The file has not yet been updated to reflect the relatively recent release of Ubuntu 10.04 Lucid Lynx, but the instructions still worked well for me on a Dell Vostro 1015:

> Ubuntu:
------
Go to System->Administration->Hardware Drivers
Choose the Broadcom STA wireless driver
Activate

Sometimes the driver does not show up in the Hardware Drivers choices.  In
this case, try reintalling the driver from the GUI or shell like this:

From the GUI:
Package Manager (System>Administration>Synaptic Package Manager). Click the
Reload button in the upper left corner of Synaptic to refresh your index then
search for and reinstall the package named bcmwl-kernel-source.

From the shell:
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

In either GUI or text case, after reinstalling, reboot your machine.

Now go back to System->Administration->Hardware Drivers
and you should see the driver enabled and working.The driver (in the form of object code) and supporting documentation are available at Broadcom's website:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

