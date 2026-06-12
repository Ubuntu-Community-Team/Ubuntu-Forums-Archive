---
title: "wireless is disabled after upgrading to 10.10"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by muhkah on 2010-10-10
Hi all, last night I already succeeded upgrading to 10.10 (Maverick meerkat), on previous version I never face wireless issue after installed additional package (**sudo apt-get install b43-fwcutter**). But after upgrading I saw the wireless is disabled and the hardware indicator light off. I used Lenovo notebook.

This is my wireless detail info :
```

root@muhkah-laptop:~# lspci
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
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
06:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
06:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
06:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
06:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

root@muhkah-laptop:~# lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 5986:0205 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

root@muhkah-laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:20:f4:57  
          inet addr:10.61.5.183  Bcast:10.61.5.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe20:f457/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7454 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6974370 (6.9 MB)  TX bytes:1060095 (1.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

root@muhkah-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

root@muhkah-laptop:~# iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

root@muhkah-laptop:~# lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26378  0 
ppdev                   5556  0 
snd_hda_codec_realtek   217980  1 
joydev                  8735  0 
arc4                    1165  2 
snd_hda_intel          22203  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71571  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
i915                  291548  3 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
b43                   169225  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 i915
mac80211              231541  1 b43
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
drm                   168726  4 i915,drm_kms_helper
r852                    9600  0 
acer_wmi               13929  0 
sm_common               3285  1 r852
cfg80211              144470  2 b43,mac80211
videodev               43098  1 uvcvideo
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13359  2 uvcvideo,videodev
mtd                    18877  2 sm_common,nand
intel_agp              26720  2 i915
psmouse                59033  0 
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
serio_raw               4022  0 
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
agpgart                32075  2 drm,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36978  0 
hid                    67742  1 usbhid
firewire_ohci          21394  0 
sdhci_pci               6339  0 
sdhci                  15954  1 sdhci_pci
firewire_core          46675  1 firewire_ohci
led_class               2633  3 b43,acer_wmi,sdhci
crc_itu_t               1383  1 firewire_core
ssb                    39320  1 b43
tg3                   123726  0

root@muhkah-laptop:~# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:20:f4:57
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=sb v3.04 ip=10.61.5.183 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:d5600000-d560ffff
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:d4600000-d4603fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:26:82:02:34:89
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

root@muhkah-laptop:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

root@muhkah-laptop:~# lsb_release -d
Description:    Ubuntu 10.10
root@muhkah-laptop:~# uname -mr
2.6.35-22-generic-pae i686
root@muhkah-laptop:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 


```Any suggestion?

Really thanks in advance.

---

### Post by davidmohammed on 2010-10-10
... I presume you've got to System - Administrator - Additional Drivers (or whatever its called in meerkat) and reactivated the b43 driver? - remember to plugin into a wired connection first.

Also try deactivating and reactivating using the same screen.

---

### Post by Dex73 on 2010-10-10
> **davidmohammed said:**
> ... I presume you've got to System - Administrator - Additional Drivers (or whatever its called in meerkat) and reactivated the b43 driver? - remember to plugin into a wired connection first.

Also try deactivating and reactivating using the same screen.

Definitely try the plug it in idea first. This worked for me. I fix my wireless drivers with update manager and an ethernet cable.

---

### Post by muhkah on 2010-10-10
Thanks for your reply, now I already update the driver and the wireless indicator is light on and the wireless detail is also identified, but after this command I still find the network is in DISABLE state :

```

muhkah@muhkah-laptop:~$ sudo lshw -C network
[sudo] password for muhkah: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:20:f4:57
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=sb v3.04 ip=10.61.5.183 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:45 memory:d5600000-d560ffff
  *-network DISABLED
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:02:34:89
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:d4600000-d4603fff

```

how to make it enabled?

Really thanks in advance.

---

### Post by armita on 2010-10-11
I have the same problem .... 
I have Brodcam STA Wireless driver , it was working in 10.04 , I've reinstalled it after upgrading to 10.10 , but my wireless is disabled.
Any suggestions ? my laptop is Dell vostro 1520

---

### Post by favri on 2010-10-11
Same problem here.

I managed to install my broadcom 43225 , but :

get the following message:

*-network DISABLED 
and all the other info about the adaptar.
How can i turn it to ENABLE?

Thx

---

### Post by SmoothFreeze on 2010-10-11
i have this same problem... I have a HP pavilion laptop. Been trying to figure this out for 2 days now...

---

### Post by favri on 2010-10-11
I've gone 1 step forward.

Now i guet :

*-network
Description: Wireless interface 

and so on.

The light of the Wireless device is now on.

But still i can't see any wireless coneccion available.

---

### Post by erwin__1 on 2010-10-12
I have the exact same problems: upgraded Dell Vostro 1520 from 10.04 (wifi worked fine) to 10.10.

I've removed and re-activated the Broadcom STA driver via Additional Drivers after which the driver seems to be fine.

lshw -C network lists:
..
  *-network DISABLED
       description: Wireless interface
..

If I use ifconfig eth1 up, the DISABLED is not shown anymore, but in the network manager, I still can't use the wireless network. It says 'wire is disabled'

iwconfig seems to list eth1 correctly, however I can't set the essid using iwconfig eth1 essid my_essid
(no errors, but it wasn't set either)


If anyone figures out a solution, let us know!

Many thanks.

---

### Post by erwin__1 on 2010-10-12
I've found a solution. At least for the Dell Vostro 1520...
Our problem is more or less the same as this:
[http://ubuntuforums.org/showthread.php?t=1307077&page=2](http://ubuntuforums.org/showthread.php?t=1307077&page=2)

Upgrading the BIOS to version A08 fixed the problem in my case.

It's still a little bit strange that the wireless driver worked fine with the older BIOS (A02) in ubuntu 10.04. (the problem popped up after upgrading to 10.10)

But in any case: I'm glad my wifi is back! Thanks [http://twitter.com/#!/tiainen/status/27134816038](http://twitter.com/#!/tiainen/status/27134816038) for finding the old thread.

---

### Post by CSLSr. on 2010-10-12
Do not try to upgrade via wireless. If you only have access to wireless (like me), then backup, create a live usb, boot into live environment, and do a fresh install. If doing this worries you...download the new maverick version of your wireless driver onto your usb first.

---

### Post by armita on 2010-10-12
my wireless is working correctly right now ... check this :
[http://ww.ubuntuforums.org/showthread.php?t=1593112](http://ww.ubuntuforums.org/showthread.php?t=1593112)

---

### Post by mehturt on 2010-10-12
I seem to have the same Wireless HW.
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
The wireless is working after upgrade from 10.04 to 10.10 without any problems, even with dell-laptop module.  However the iwconfig command says I'm not associated, even though wifi is working fine. I seem to have a bit greater latency than in 10.04.

$/sbin/iwconfig
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:211  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

---

### Post by sunner_sun on 2010-10-13
I have the same problem on Lenovo Ideapad S12 and I found the solution:

1. "lsmod|grep acer_wmi". If there are output, that means the solution perhaps works for you.
2. Append one line "blacklist acer_wmi" into /etc/modprobe.d/blacklist.conf
3. reboot and wish be fine

---

### Post by mehturt on 2010-10-13
> **mehturt said:**
> However the iwconfig command says I'm not associated, even though wifi is working fine.

sorry, I need to do sudo /sbin/iwconfig in 10.10

---

### Post by g0d4 on 2010-10-13
I had the same problem.
i tried using 

```
 sudo rfkill unblock all
```

and all that i could get was that sometimes my wireless worked but sometimes it was disabled. 

I tried to boot ubuntu with a previous version of kernel (2.6.32-25-generic) instead of (2.6.35-25) and my wireless worked just fine.. so i think i will keep running my ubuntu until a new update of the kernel..

---

### Post by rmtatum on 2010-10-17
I found a solution that worked on my roommate's laptop.

First, uninstall all b43 and bcmwl packages (including the bcmwl-modaliases package).

Reboot.

Then run the following command:

```
sudo apt-get install bcmwl-kernel-source firmware-b43-lpphy-installer
```

---

### Post by Zeno Cosini on 2010-12-18
I have been using Ubuntu 10.10 on a Dell Latitude XT for about six weeks. About three weeks ago, my wireless suddenly stopped working. The NetworkManager Applet tells me that the "wireless is disabled", and the "Enable Wireless" command is greyed-out. The blue WiFi light is constantly turned off. I do not know whether any automatic updates were installed right before the problems started, and I cannot think of any other reason why the wireless should suddenly have been disabled after working out of the box. 

Here is the (sanitized) output of various commands providing detailed information on the hardware and the OS:

```

xxx@yyy:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 7930 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS7932 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Device 7934
00:06.0 PCI bridge: ATI Technologies Inc RS7936 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc Device 7937
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Xpress 1250
03:01.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:01.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:01.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5756ME Gigabit Ethernet PCI Express
0b:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)

xxx@yyy:~$ lsusb
Bus 006 Device 002: ID 413c:8138 Dell Computer Corp. Wireless 5520 Voda I Mobile Broadband (3G HSDPA) Minicard EAP-SIM Port
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1b96:0001 N-Trig Duosense Transparent Electromagnetic Digitizer
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 1028:0204 Inovys Corp. 
Bus 001 Device 007: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)
Bus 001 Device 006: ID 413c:9001 Dell Computer Corp. 
Bus 001 Device 004: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

xxx@yyy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:255.255.255.0
          inet6 addr: xx::xx:xx:xx:xx:xx /64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7117451 (7.1 MB)  TX bytes:1791000 (1.7 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1944 (1.9 KB)  TX bytes:1944 (1.9 KB)

xxx@yyy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

xxx@yyy:~$ lsmod
Module                  Size  Used by
aes_i586                7280  466 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
dm_crypt               11385  0 
snd_hda_codec_idt      54887  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop             5730  0 
dell_wmi                2852  0 
soundcore                880  1 snd
dcdbas                  5402  1 dell_laptop
pcmcia                 35973  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lib80211_crypt_tkip     7736  0 
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
wl                   1959533  0 
lp                      7342  0 
shpchp                 29886  0 
psmouse                59033  0 
joydev                  8735  0 
option                 13133  0 
usb_wwan                9953  1 option
i2c_piix4               8635  0 
hid_ntrig               5529  0 
lib80211                5058  2 lib80211_crypt_tkip,wl
serio_raw               4022  0 
usbserial              33100  2 option,usb_wwan
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40172  0 
radeon                827837  3 
usbhid                 36882  1 hid_ntrig
hid                    67742  2 hid_ntrig,usbhid
ttm                    56633  1 radeon
drm_kms_helper         30168  1 radeon
firewire_ohci          21106  0 
sdhci_pci               6339  0 
drm                   168054  5 radeon,ttm,drm_kms_helper
sdhci                  15890  1 sdhci_pci
video                  18712  0 
firewire_core          46643  1 firewire_ohci
ati_agp                 5202  0 
led_class               2633  1 sdhci
output                  1883  1 video
tg3                   123310  0 
i2c_algo_bit            5168  1 radeon
pata_atiixp             3288  5 
crc_itu_t               1383  1 firewire_core
agpgart                32011  3 ttm,drm,ati_agp

xxx@yyy:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5756ME Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: xx:xx:xx:xx:xx:xx
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=5756m-v3.09 ip=xxx.xxx.xxx.xxx latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:43 memory:fe9f0000-fe9fffff
  *-network DISABLED
       description: Wireless interface
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 03
       serial: xx:xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:fe8fc000-fe8fffff memory:f0000000-f00fffff

xxx@yyy:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

xxx@yyy:~$ lsb_release -d
Description:	Ubuntu 10.10

xxx@yyy:~$ uname -mr
2.6.35-23-generic i686

```

System-Administration-Additional Drivers shows me that I am using the Broadcom STA wireless driver. I currently do not dare to remove it, because I am not sure how to reinstall it. Would I simply have to reinstall the packages bcmwl-kernel-source and bcmwl-modaliases in the Synaptic Package Manager?

Do you have any idea what the problem might be? I highly appreciate your help.

---

### Post by M!SF!TS on 2010-12-25
I cannot believe there is STILL no fix to this. I STILL cannot use 10.10 because of the Broadcom Issue... It works good under Ubuntu 10.04, I have tried everything possible, Still Nothing. (I got a HP DV2000, Broadcom STA 4321 Wireless Driver)

Sometimes... ya know, Sometimes... I wish there was better support...

---

### Post by Zeno Cosini on 2011-01-01
> **M!SF!TS said:**
> I cannot believe there is STILL no fix to this. I STILL cannot use 10.10 because of the Broadcom Issue... It works good under Ubuntu 10.04, I have tried everything possible, Still Nothing. (I got a HP DV2000, Broadcom STA 4321 Wireless Driver)

Sometimes... ya know, Sometimes... I wish there was better support...

Funny thing is that wireless initially *did* work with Ubuntu 10.10...

Is there any way for me to find out whether the problem is hardware-related? After all, the wireless card *may* have failed.

---

### Post by Leejjon on 2011-06-08
> **M!SF!TS said:**
> I cannot believe there is STILL no fix to this. I STILL cannot use 10.10 because of the Broadcom Issue... It works good under Ubuntu 10.04, I have tried everything possible, Still Nothing. (I got a HP DV2000, Broadcom STA 4321 Wireless Driver)

Sometimes... ya know, Sometimes... I wish there was better support...
				**[B]Medion MD98300 laptop here, exact same problem. I tried upgrading to 11.04 and it still doesn't work. It does work under 10.04. Please pm/e-mail me if you found a solution.**[/B]

---

### Post by Leejjon on 2012-10-19
Is there anyone who tested the new 12.10 release on the **[B]Medion MD98300**[/B] or other laptops with this broadcom thing? I'm scared that if I try to update I cannot go back anymore without a re-install.

---

