---
title: "Ralink rt2070 driver install problems"
date: 2012-07-15
forum: Networking &amp; Wireless
---

### Post by jasekshaw on 2012-07-15
Hi, i finally got my driver to install and work, then with the internet connection i updated to teh latest version of ubuntu, doing this stopped my usb wireless adapter from working again, i tried to do a clean install but this didnt work
 
im on my laptop now
 
and have ubuntu on my computor
 
thanks for any help

---

### Post by Kirk Schnable on 2012-07-15
Try following the instructions you followed to install your driver before.  When you update your kernel, any kernel modules you compiled for the old kernel will need to be recompiled before they'll load up in the new kernel.

Kirk

---

### Post by jasekshaw on 2012-07-15
i did, still wont find any networks

---

### Post by Kirk Schnable on 2012-07-15
> **jasekshaw said:**
> i did, still wont find any networks

Can you give me:

```
lspci -v
```

Kirk

---

### Post by jasekshaw on 2012-07-15
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
 Subsystem: Giga-byte Technology Device 2580
 Flags: bus master, fast devsel, latency 0
 Capabilities: <access denied>
 Kernel modules: intel-agp
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
 I/O behind bridge: 00008000-00008fff
 Memory behind bridge: d0000000-efffffff
 Prefetchable memory behind bridge: 80000000-800fffff
 Capabilities: <access denied>
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
 Subsystem: Giga-byte Technology Device a005
 Flags: bus master, fast devsel, latency 0, IRQ 16
 Memory at f0300000 (64-bit, non-prefetchable) [size=16K]
 Capabilities: <access denied>
 Kernel driver in use: HDA Intel
 Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
 I/O behind bridge: 00007000-00007fff
 Memory behind bridge: 80100000-802fffff
 Prefetchable memory behind bridge: 0000000080300000-00000000804fffff
 Capabilities: <access denied>
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
 I/O behind bridge: 00001000-00001fff
 Memory behind bridge: f0000000-f00fffff
 Prefetchable memory behind bridge: 0000000080500000-00000000806fffff
 Capabilities: <access denied>
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
 I/O behind bridge: 00002000-00002fff
 Memory behind bridge: f0100000-f01fffff
 Prefetchable memory behind bridge: 0000000080700000-00000000808fffff
 Capabilities: <access denied>
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
 Subsystem: Giga-byte Technology Device 2658
 Flags: bus master, medium devsel, latency 0, IRQ 23
 I/O ports at bc00 [size=32]
 Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
 Subsystem: Giga-byte Technology Device 2659
 Flags: bus master, medium devsel, latency 0, IRQ 19
 I/O ports at b000 [size=32]
 Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
 Subsystem: Giga-byte Technology Device 265a
 Flags: bus master, medium devsel, latency 0, IRQ 18
 I/O ports at b400 [size=32]
 Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
 Subsystem: Giga-byte Technology Device 265a
 Flags: bus master, medium devsel, latency 0, IRQ 16
 I/O ports at b800 [size=32]
 Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
 Subsystem: Giga-byte Technology Device 5006
 Flags: bus master, medium devsel, latency 0, IRQ 23
 Memory at f0304000 (32-bit, non-prefetchable) [size=1K]
 Capabilities: <access denied>
 Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01)
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
 I/O behind bridge: 00009000-0000afff
 Memory behind bridge: f0200000-f02fffff
 Capabilities: <access denied>
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
 Flags: bus master, medium devsel, latency 0
 Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
 Subsystem: Giga-byte Technology Device 266f
 Flags: bus master, medium devsel, latency 0, IRQ 18
 I/O ports at 01f0 [size=8]
 I/O ports at 03f4 [size=1]
 I/O ports at 0170 [size=8]
 I/O ports at 0374 [size=1]
 I/O ports at f000 [size=16]
 Kernel driver in use: ata_piix
00:1f.2 RAID bus controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
 Subsystem: Giga-byte Technology Device 2652
 Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
 I/O ports at d000 [size=8]
 I/O ports at d400 [size=4]
 I/O ports at d800 [size=8]
 I/O ports at dc00 [size=4]
 I/O ports at e000 [size=16]
 Memory at f0307000 (32-bit, non-prefetchable) [size=1K]
 Capabilities: <access denied>
 Kernel driver in use: ata_piix
 Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
 Subsystem: Giga-byte Technology Device 266a
 Flags: medium devsel, IRQ 10
 I/O ports at 0500 [size=32]
 Kernel modules: i2c-i801
01:00.0 VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600 Series]
 Subsystem: PC Partner Limited Device e410
 Flags: bus master, fast devsel, latency 0, IRQ 28
 Memory at d0000000 (64-bit, prefetchable) [size=256M]
 Memory at e1000000 (64-bit, non-prefetchable) [size=64K]
 I/O ports at 8000 [size=256]
 [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
 Capabilities: <access denied>
 Kernel driver in use: radeon
 Kernel modules: radeon
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
 Subsystem: PC Partner Limited Device aa08
 Flags: bus master, fast devsel, latency 0, IRQ 17
 Memory at e1010000 (64-bit, non-prefetchable) [size=16K]
 Capabilities: <access denied>
 Kernel driver in use: HDA Intel
 Kernel modules: snd-hda-intel
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
 Subsystem: Giga-byte Technology Device e000
 Flags: bus master, fast devsel, latency 0, IRQ 18
 Memory at f0000000 (64-bit, non-prefetchable) [size=64K]
 Expansion ROM at <ignored> [disabled]
 Capabilities: <access denied>
 Kernel driver in use: tg3
 Kernel modules: tg3
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
 Subsystem: Giga-byte Technology Device e000
 Flags: bus master, fast devsel, latency 0, IRQ 19
 Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
 Expansion ROM at <ignored> [disabled]
 Capabilities: <access denied>
 Kernel driver in use: tg3
 Kernel modules: tg3
05:06.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
 Subsystem: VIA Technologies, Inc. VT6410 ATA133 RAID controller
 Flags: bus master, medium devsel, latency 32, IRQ 22
 I/O ports at 9000 [size=8]
 I/O ports at 9400 [size=4]
 I/O ports at 9800 [size=8]
 I/O ports at 9c00 [size=4]
 I/O ports at a000 [size=16]
 Capabilities: <access denied>
 Kernel driver in use: pata_via
 Kernel modules: pata_via
05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
 Subsystem: Giga-byte Technology Device 1000
 Flags: bus master, medium devsel, latency 32, IRQ 23
 Memory at f0204000 (32-bit, non-prefetchable) [size=2K]
 Memory at f0200000 (32-bit, non-prefetchable) [size=16K]
 Capabilities: <access denied>
 Kernel driver in use: ohci1394
 Kernel modules: firewire-ohci, ohci1394

---

### Post by Kirk Schnable on 2012-07-15
Oh, sorry, I didn't realize this was a USB device.  Let's try:

```
lshw -c network
```

Kirk

---

### Post by jasekshaw on 2012-07-15
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5789 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:03:00.0"]pci@0000:03:00.0[/EMAIL]
       logical name: eth0
       version: 11
       serial: 00:0f:ea:e5:2d:eb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=5789-v3.29a latency=0 multicast=yes
       resources: irq:18 memory:f0000000-f000ffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5789 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:04:00.0"]pci@0000:04:00.0[/EMAIL]
       logical name: eth1
       version: 11
       serial: 00:0f:ea:e5:2d:ed
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=5789-v3.29a latency=0 multicast=yes
       resources: irq:19 memory:f0100000-f010ffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 7c:dd:90:1a:7e:ca
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

---

### Post by chili555 on 2012-07-15
Let's see:```
lsusb
lsmod | grep -e rt2 -e rt3
lsb_release -d
```Thanks.

---

### Post by jasekshaw on 2012-07-15
[EMAIL="jason@jason-desktop:~$"]jason@jason-desktop:~$[/EMAIL] lsusb
Bus 005 Device 002: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 1c4f:0002 SiGma Micro 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 013: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[EMAIL="jason@jason-desktop:~$"]jason@jason-desktop:~$[/EMAIL] lsmod | grep -e rt2 -e rt3
rt2870sta             461811  0 
rt2800usb              31531  0 
rt2x00usb               9639  1 rt2800usb
rt2x00lib              27573  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205434  2 rt2x00usb,rt2x00lib
cfg80211              126528  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
[EMAIL="jason@jason-desktop:~$"]jason@jason-desktop:~$[/EMAIL] lsb_release -d
Description: Ubuntu 10.04.4 LTS

---

### Post by chili555 on 2012-07-15
Man, that is a whole great big pile of conflicting drivers you have there! Please do:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report.

---

### Post by jasekshaw on 2012-07-15
rebooted and it can now find the networks!! BUT, it wont connect, keep asking for the password, when i put it in, it tries, then asks for it again, its 100% teh right password and network that im trying to connect too

---

### Post by jasekshaw on 2012-07-15
Dupe Post...

---

### Post by chili555 on 2012-07-15
> **jasekshaw said:**
> rebooted and it can now find the networks!! BUT, it wont connect, keep asking for the password, when i put it in, it tries, then asks for it again, its 100% teh right password and network that im trying to connect tooLet's see:```
sudo iwlist wlan0 scan
iwconfig
```Thanks.

---

### Post by jasekshaw on 2012-07-15
[EMAIL="jason@jason-desktop:~$"]jason@jason-desktop:~$[/EMAIL] sudo iwlist wlan0 scan
[sudo] password for jason: 
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:74:CD:F3:4F
                    Protocol:802.11b/g
                    ESSID:"SKY62286"
                    Mode:Managed
                    Channel:1
                    Quality:7/100  Signal level:-87 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: A0:21:B7:D9:2D:23
                    Protocol:802.11b/g/n
                    ESSID:"virginmedia1837164"
                    Mode:Managed
                    Channel:6
                    Quality:42/100  Signal level:-73 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
[EMAIL="jason@jason-desktop:~$"]jason@jason-desktop:~$[/EMAIL] iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      no wireless extensions.
wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=90/100  Signal level:-75 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[EMAIL="jason@jason-desktop:~$"]jason@jason-desktop:~$[/EMAIL]

---

### Post by chili555 on 2012-07-15
When you compiled the driver, did you read the README and make the needed changes to config.mk? If not, please do and re-compile:```
cd Desktop/RT2870file [COLOR="Red"]<--or wherever you extracted the driver[/COLOR]
sudo su
make clean
make
make install
modprobe -r rt2870sta
modprobe rt2870sta
exit
```

---

### Post by jasekshaw on 2012-07-15
done that, im new to linux, so from what i can understand from the readme seems to already be done, still no luck connecting
 
I have to get some sleep now, ill be back tommorow
 
Thanks for helping man

---

### Post by chili555 on 2012-07-15
Please open the files you extracted and go to the folder *os* and then to *linux* and look in the file config.mk with any text editor. What do these lines say?> # Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=[COLOR="Red"]??[/COLOR]

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="Red"]??[/COLOR]
Do they say y, n or c01db33r?

---

### Post by jasekshaw on 2012-07-16
both say "=y" ... c01db33r? lol

---

### Post by chili555 on 2012-07-16
> **jasekshaw said:**
> both say "=y" ... c01db33r? lolYes, indeed. i 10v3 c01d b33r!

Do you have the needed dat file in place? ```
head -n5 /etc/Wireless/RT2870STA/RT2870STA.dat
```Any clues here?```
sudo cat /var/log/syslog | grep etwork | tail -n20
dmesg | grep -e wlan -e rt2 
```

---

### Post by jasekshaw on 2012-07-16
jason@jason-desktop:~$ head -n5 /etc/Wireless/RT2870STA/RT2870STA.dat
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=

jason@jason-desktop:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
[sudo] password for jason: 
Jul 16 18:45:30 jason-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 16 18:45:30 jason-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jul 16 18:45:35 jason-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
Jul 16 18:45:35 jason-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jul 16 18:45:36 jason-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Jul 16 18:45:36 jason-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 16 18:45:38 jason-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated
Jul 16 18:45:46 jason-desktop NetworkManager: <info>  wlan0: link timed out.
Jul 16 18:45:48 jason-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Jul 16 18:45:48 jason-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 16 18:45:48 jason-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jul 16 18:45:53 jason-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
Jul 16 18:45:53 jason-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jul 16 18:46:00 jason-desktop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jul 16 18:46:00 jason-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 7)
Jul 16 18:46:00 jason-desktop NetworkManager: <info>  Activation (wlan0) failed for access point (virginmedia1837164)
Jul 16 18:46:00 jason-desktop NetworkManager: <info>  Marking connection 'Auto virginmedia1837164' invalid.
Jul 16 18:46:00 jason-desktop NetworkManager: <info>  Activation (wlan0) failed.
Jul 16 18:46:00 jason-desktop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jul 16 18:46:00 jason-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
jason@jason-desktop:~$ dmesg | grep -e wlan -e rt2
[   14.152980] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   14.187121] usbcore: registered new interface driver rt2870
[   14.328425] Error: Driver 'rt2870' is already registered, aborting...
[   14.328468] usbcore: error -16 registering interface     driver rt2870
[   26.396006] wlan0: no IPv6 routers present

---

### Post by chili555 on 2012-07-16
> Error: Driver 'rt2870' is already registered, aborting...Very interesting. Please let me see:```
lsmod
```It sounds as if there is a conflict here.

---

### Post by jasekshaw on 2012-07-16
[EMAIL="jason@jason-desktop:~$"]jason@jason-desktop:~$[/EMAIL] lsmod
Module                  Size  Used by
rt2870sta             461811  1 
binfmt_misc             6587  1 
snd_hda_codec_atihdmi     2367  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_cmedia     7454  1 
snd_hda_intel          22069  2 
snd_seq_dummy           1338  0 
snd_hda_codec          74297  3 snd_hda_codec_atihdmi,snd_hda_codec_cmedia,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                678607  3 
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49847  1 radeon
ppdev                   5259  0 
drm_kms_helper         29329  1 radeon
snd                    54244  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             25962  1 
psmouse                63677  0 
joydev                  8740  0 
drm                   163779  5 radeon,ttm,drm_kms_helper
serio_raw               3978  0 
i2c_algo_bit            5028  1 radeon
soundcore               6620  1 snd
intel_agp              24375  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  3 ttm,drm,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
usbhid                 36110  0 
hid                    67288  1 usbhid
floppy                 53016  0 
ieee1394               81181  1 ohci1394
pata_via                7272  0 
tg3                   109324  0

---

### Post by chili555 on 2012-07-16
Well, you only have the correct driver rt2870sta loaded and running. Did you every try ndiswrapper?```
cat /etc/modules
ls /etc/ndiswrapper
```Since rt2870sta is included in 10.04 by default, what made you decide to compile a downloaded driver with all it's problems and prerequisites? I wonder if you are actually using the compiled version and not the default version:```
modinfo rt2870sta | head -n3
```

---

### Post by jasekshaw on 2012-07-16
i had a an old version of ubuntu, and installed the driver, then i was able to update to new version of ubuntu, but when that happened it stopped me connecting to the internet again, so i thought i had to install it again, thats when i got problems
 
Here are the results of the codes you told me to enter
 
[EMAIL="jason@jason-desktop:~$"]jason@jason-desktop:~$[/EMAIL] cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
lp

[EMAIL="jason@jason-desktop:~$"]jason@jason-desktop:~$[/EMAIL] ls /etc/ndiswrapper
ls: cannot access /etc/ndiswrapper: No such file or directory

[EMAIL="jason@jason-desktop:~$"]jason@jason-desktop:~$[/EMAIL] modinfo rt2870sta | head -n3
filename:       /lib/modules/2.6.32-41-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
alias:          rt3070sta
version:        2.0.1.0
[EMAIL="jason@jason-desktop:~$"]jason@jason-desktop:~$[/EMAIL]

---

### Post by chili555 on 2012-07-16
> filename: /lib/modules/2.6.32-41-generic/[COLOR="Red"]kernel/drivers/staging[/COLOR]/rt2870/rt2870sta.koI think that, and the fact that it's wlan0 and not ra0, tell us it's the stock default version. I suggest you try to compile the version you have downloaded. Have you installed build-essential and linux-headers?

---

### Post by jasekshaw on 2012-07-16
i cant install anything, because there is no way i can get the ineternet on teh computor, all i have is a usb stick? do you meen the version that came on the disk when i brought the usb stick?

---

### Post by jasekshaw on 2012-07-17
Not sure if i should have done this, but iv uninstalled the drivers i installed, so whats on the system now, is what came with the ubuntu upgrade, saMe problem persists though, it can find the networks, but just wont connect

This is one of the most annoying problems iv ever had, im at a point where i feel kickin the hell out of it ha i really dont wanna go back to windows though

---

### Post by chili555 on 2012-07-17
> Cell 02 - Address: A0:21:B79:2D:23
Protocol:802.11b/g/n
ESSID:"virginmedia1837164"
Mode:Managed
Channel:6
Quality:42/100 Signal level:-73 dBm Noise level:-97 dBm
Encryption keyn
Bit Rates:54 Mb/s
IE: [COLOR="Red"]WPA Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/[COLOR="Red"]WPA2 Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSKI suggest you reset the router to WPA2 only and not mixed mode WPA/WPA2. You might also try WPA instead of WPA2. Will it connect with either?

---

### Post by jasekshaw on 2012-07-17
nope, no difference, still fails to connect....

---

### Post by jasekshaw on 2012-07-17
like, in teh old version of ubuntu, i could connect and use it, but since the upgrade its not having any of it

---

### Post by chili555 on 2012-07-17
> but since the upgrade its not having any of itThe upgraded driver or the upgraded version of Ubuntu? Are you still on 10.04?

---

### Post by jasekshaw on 2012-07-17
ubuntu, yeh i had 9. somthing at first, then once i got the ralink adater to work, it updated to 10.4 n then adapter stopped working

---

### Post by chili555 on 2012-07-17
Are the symptoms the same with all three versions of encryption? WPA/WPA2 mixed mode; WPA only and WPA2 only? It asks for the password and never quite connects? Or does it connect and drop?

---

### Post by jasekshaw on 2012-07-17
yeh same with all, never connects, tries to then asks for password again, then tries, then asks again, liek a loop,

---

### Post by chili555 on 2012-07-18
What is the version of the driver you installed and then uninstalled. Maybe we can find something newer. I may have something in my files,as well.

---

