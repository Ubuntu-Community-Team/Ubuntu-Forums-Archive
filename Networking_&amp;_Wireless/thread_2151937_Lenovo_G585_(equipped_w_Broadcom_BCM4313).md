---
title: "Lenovo G585 (equipped w/ Broadcom BCM4313)"
date: 2013-06-06
forum: Networking &amp; Wireless
---

### Post by thomas0327 on 2013-06-06
Hello everybody!

I'm completely new here, so I would like to excuse for asking simple things in advance.

I purchased this notebook 2 months ago, it was equipped with Win7 x64. Wireless and wired connections worked without problem with the drives supplied, however, the computer was very slow with that OS so I decided to change to Linux Mint 15 x64 Cinnamon ed. This OS is quite good but seems to have a problem recognizing my wireless (Broadcom BCM4313). Wired connection operates perfectly. 

I tried to find out what the problem is, so typed these into the terminal:

```

thomas@thomas-Lenovo-G585 ~ $ lspci

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 7310]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] FCH SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] FCH PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI to PCI bridge (PCIE port 1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Robson CE [Radeon HD 6370M/7370M]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
07:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

``````

thomas@thomas-Lenovo-G585 ~ $ sudo lshw -C network
[sudo] password for thomas: 

  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: dc:0e:a1:f3:fe:fb
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 01
       serial: c0:14:3d:d1:a5:9f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: aa:bb:cc:dd:ee:ff
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.130 link=yes multicast=yes

``````

thomas@thomas-Lenovo-G585 ~ $ lsmod

Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
binfmt_misc            17500  1 
nls_iso8859_1          12713  1 
lib80211_crypt_tkip    17379  0 
uvcvideo               80847  0 
joydev                 17377  0 
wl                   3074449  0 
rts5139               352481  0 
snd_hda_codec_conexant    62000  1 
snd_hda_codec_hdmi     36913  1 
snd_hda_intel          39619  5 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
rndis_wlan             36998  0 
rndis_host             13855  1 rndis_wlan
cdc_ether              13453  1 rndis_host
btusb                  22474  0 
usbnet                 31879  3 rndis_host,rndis_wlan,cdc_ether
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
bluetooth             228619  22 bnep,btusb,rfcomm
videodev              129260  2 uvcvideo,videobuf2_core
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
kvm_amd                59717  0 
snd_seq_midi           13324  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
kvm                   443165  1 kvm_amd
dm_multipath           22843  0 
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              510937  2 wl,rndis_wlan
snd_rawmidi            30180  1 snd_seq_midi
scsi_dh                14843  1 dm_multipath
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
psmouse                95870  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
serio_raw              13215  0 
microcode              22881  0 
k10temp                13126  0 
i2c_piix4              13266  0 
snd                    68876  20 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
ideapad_laptop         18394  0 
sparse_keymap          13890  1 ideapad_laptop
soundcore              12680  1 snd
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
btrfs                 785967  0 
zlib_deflate           26885  1 btrfs
libcrc32c              12615  1 btrfs
dm_raid45              76725  0 
xor                    17116  1 dm_raid45
dm_mirror              21946  0 
dm_region_hash         20820  1 dm_mirror
dm_log                 18529  3 dm_region_hash,dm_mirror,dm_raid45
r8169                  67446  0 
radeon                937749  4 
i2c_algo_bit           13413  1 radeon
ttm                    83187  1 radeon
drm_kms_helper         49394  1 radeon
video                  19390  0 
drm                   286313  6 ttm,drm_kms_helper,radeon
ahci                   25731  5 
libahci                31364  1 ahci

```
========================================================================================================================

Now I tried to reinstall bcmwl-kernel-source hoping it would solve the problem, but no results. Could someone please help me out? Thanks for your help in advance.
T.

---

### Post by chili555 on 2013-06-06
I believe bcmwl-kernel-source is wrong for your device. I suggest:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -r wl
sudo modprobe brcmsmac
```Remove the USB wireless and tell us how it's working.

---

### Post by thomas0327 on 2013-06-06
```
thomas@thomas-Lenovo-G585 ~ $ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for thomas: 

Csomaglisták olvasása... Kész
Függ&#337;ségi fa építése       
Állapotinformációk olvasása... Kész
Az alábbi csomagok el lesznek TÁVOLÍTVA:
  bcmwl-kernel-source*
0 frissített, 0 újonnan telepített, 1 eltávolítandó és 66 nem frissített.
A m&#369;velet után 4.279 kB lemezterület szabadul fel.
Folytatni akarja [I/n]? i
(Adatbázis olvasása ... 203574 files and directories currently installed.)
Eltávolítás: bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
bcmwl-kernel-source beállító fájlok törlése ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-23-generic
Warning: No support for locale: hu_HU.utf8

thomas@thomas-Lenovo-G585 ~ $ sudo modprobe -r wl
FATAL: Module wl not found.

thomas@thomas-Lenovo-G585 ~ $ sudo modprobe brcmsmac

thomas@thomas-Lenovo-G585 ~ $ 
```

Still the same. It tries connecting to the home network, but throws me off saying I'm disconnected.

---

### Post by chili555 on 2013-06-06
Let's have a look at the log:```
cat /var/log/syslog | grep -e wlan -e brcmsmac | tail -n20
```

---

### Post by thomas0327 on 2013-06-06
Here it is: 

```

thomas@thomas-Lenovo-G585 ~ $ cat /var/log/syslog | grep -e wlan -e brcmsmac | tail -n20
Jun  6 12:52:10 thomas-Lenovo-G585 kernel: [   13.044574] usbcore: registered new interface driver rndis_wlan
```

---

### Post by chili555 on 2013-06-06
> **thomas0327 said:**
> Here it is: 

thomas@thomas-Lenovo-G585 ~ $ cat /var/log/syslog | grep -e wlan -e brcmsmac | tail -n20
Jun  6 12:52:10 thomas-Lenovo-G585 kernel: [   13.044574] usbcore: registered new interface driver rndis_wlanAll we see here is the USB. Please detach it and run these commands:```
sudo su
echo brcmsmac >> /etc/modules
exit
```Reboot and run this again and post the result:```
cat /var/log/syslog | grep -e wlan -e brcmsmac | tail -n20
```

---

### Post by thomas0327 on 2013-06-06
Whoa, something happened! After executing the below-linked code and rebooting, I was able to catch the home network and connected it, but only for a few seconds. Then it disconnected again. 


sudo suecho brcmsmac >> /etc/modules
Typing the "cat..." code it gave the result:


```

thomas@thomas-Lenovo-G585 ~ $ cat /var/log/syslog | grep -e wlan -e brcmsmac | tail -n20
Jun  6 15:26:33 thomas-Lenovo-G585 NetworkManager[979]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  6 15:26:33 thomas-Lenovo-G585 NetworkManager[979]: <info> Activation (wlan0/wireless): access point 'Automatikus ADB-C2C557' has security, but secrets are required.
Jun  6 15:26:33 thomas-Lenovo-G585 NetworkManager[979]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun  6 15:26:33 thomas-Lenovo-G585 NetworkManager[979]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  6 15:26:33 thomas-Lenovo-G585 NetworkManager[979]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  6 15:26:33 thomas-Lenovo-G585 NetworkManager[979]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  6 15:26:33 thomas-Lenovo-G585 NetworkManager[979]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jun  6 15:26:33 thomas-Lenovo-G585 NetworkManager[979]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  6 15:26:33 thomas-Lenovo-G585 NetworkManager[979]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  6 15:26:33 thomas-Lenovo-G585 NetworkManager[979]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  6 15:26:33 thomas-Lenovo-G585 NetworkManager[979]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  6 15:26:33 thomas-Lenovo-G585 NetworkManager[979]: <info> Activation (wlan0/wireless): connection 'Automatikus ADB-C2C557' has security, and secrets exist.  No new secrets needed.
Jun  6 15:26:33 thomas-Lenovo-G585 NetworkManager[979]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  6 15:26:33 thomas-Lenovo-G585 NetworkManager[979]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  6 15:26:58 thomas-Lenovo-G585 NetworkManager[979]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jun  6 15:26:58 thomas-Lenovo-G585 NetworkManager[979]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Jun  6 15:26:58 thomas-Lenovo-G585 NetworkManager[979]: <warn> Activation (wlan0) failed for connection 'Automatikus ADB-C2C557'
Jun  6 15:26:58 thomas-Lenovo-G585 NetworkManager[979]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun  6 15:26:58 thomas-Lenovo-G585 NetworkManager[979]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun  6 15:26:59 thomas-Lenovo-G585 NetworkManager[979]: <info> (wlan0): supplicant interface state: scanning -> inactive
```

---

### Post by chili555 on 2013-06-06
We're getting closer! Now how about:```
cat /var/log/syslog | grep -e wlan -e 80211 | tail -n20
```Please run it after you tried to connect.

---

### Post by thomas0327 on 2013-06-06
This time it didn't try to connect to the network. However, executing the code gave the result:

```

thomas-Lenovo-G585 thomas # cat /var/log/syslog | grep -e wlan -e 80211 | tail -n20
Jun  6 16:01:17 thomas-Lenovo-G585 kernel: [   19.187313] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  6 16:01:17 thomas-Lenovo-G585 kernel: [   19.187317] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  6 16:01:17 thomas-Lenovo-G585 kernel: [   19.187321] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  6 16:01:18 thomas-Lenovo-G585 NetworkManager[981]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:07:00.0/bcma0:0/net/wlan0, iface: wlan0)
Jun  6 16:01:18 thomas-Lenovo-G585 NetworkManager[981]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:07:00.0/bcma0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:15.1/0000:07:00.0/bcma0:0/ieee80211/phy0/rfkill0) (driver brcmsmac)
Jun  6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0): using nl80211 for WiFi device control
Jun  6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0): new 802.11 WiFi device (driver: 'brcmsmac' ifindex: 3)
Jun  6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun  6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0): bringing up device.
Jun  6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0): preparing device.
Jun  6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun  6 16:01:19 thomas-Lenovo-G585 kernel: [   21.995906] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  6 16:01:19 thomas-Lenovo-G585 kernel: [   21.996571] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0) supports 4 scan SSIDs
Jun  6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0): supplicant interface state: starting -> ready
Jun  6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun  6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0) supports 4 scan SSIDs
```

---

### Post by chili555 on 2013-06-06
Please do:```
gksudo gedit /etc/network/interfaces
```If the file contains any lines related to wlan0, please remove them. Proofread carefully, save and close gedit. Now do:```
gksudo gedit /etc/NetworkManager/NetworkManager.conf
```Please be sure managed=true. Proofread carefully, save and close gedit. Now do:```
sudo service network-manager restart
```Now try to connect. Run:```
cat /var/log/syslog | grep -e wlan -e 80211 | tail -n20
```Have we gotten past the error as before:> device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]Look for and post entries after the timestamps you posted:> Jun 6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 6 16:01:19 thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0): supplicant interface state: ready -> inactive
[COLOR="#FF0000"]Jun 6 16:01:19[/COLOR] thomas-Lenovo-G585 NetworkManager[981]: <info> (wlan0) supports 4 scan SSIDs 

---

### Post by thomas0327 on 2013-06-06
```

thomas-Lenovo-G585 thomas # cat /var/log/syslog | grep -e wlan -e 80211 | tail -n20
Jun  6 16:20:21 thomas-Lenovo-G585 kernel: [ 1162.873269] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  6 16:20:21 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): preparing device.
Jun  6 16:20:21 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun  6 16:20:21 thomas-Lenovo-G585 kernel: [ 1162.874768] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
_[COLOR=#ff0000]Jun  6 16:20:21[/COLOR] thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0) supports 4 scan SSIDs_
Jun  6 16:20:21 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): supplicant interface state: starting -> ready
Jun  6 16:20:21 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  6 16:20:21 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun  6 16:20:21 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0) supports 4 scan SSIDs
Jun  6 16:20:45 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
Jun  6 16:20:45 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun  6 16:20:46 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): taking down device.
Jun  6 16:20:49 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): bringing up device.
Jun  6 16:20:49 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): bringing up device.
Jun  6 16:20:49 thomas-Lenovo-G585 kernel: [ 1190.487855] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  6 16:20:49 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0) supports 4 scan SSIDs
Jun  6 16:20:49 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): supplicant interface state: starting -> ready
Jun  6 16:20:49 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  6 16:20:49 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun  6 16:20:49 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0) supports 4 scan SSIDs
```

No connection, it even doesn't recognize other networks nearby.

---

### Post by thomas0327 on 2013-06-06
```
thomas-Lenovo-G585 thomas # cat /var/log/syslog | grep -e wlan -e 80211 | tail -n20
Jun  6 16:20:21 thomas-Lenovo-G585 kernel: [ 1162.873269] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  6 16:20:21 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): preparing device.
Jun  6 16:20:21 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun  6 16:20:21 thomas-Lenovo-G585 kernel: [ 1162.874768] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  6 16:20:21 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0) supports 4 scan SSIDs
Jun  6 16:20:21 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): supplicant interface state: starting -> ready
Jun  6 16:20:21 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  6 16:20:21 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun  6 16:20:21 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0) supports 4 scan SSIDs
Jun  6 16:20:45 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
Jun  6 16:20:45 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun  6 16:20:46 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): taking down device.
Jun  6 16:20:49 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): bringing up device.
Jun  6 16:20:49 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): bringing up device.
Jun  6 16:20:49 thomas-Lenovo-G585 kernel: [ 1190.487855] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  6 16:20:49 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0) supports 4 scan SSIDs
Jun  6 16:20:49 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): supplicant interface state: starting -> ready
Jun  6 16:20:49 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  6 16:20:49 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun  6 16:20:49 thomas-Lenovo-G585 NetworkManager[3575]: <info> (wlan0) supports 4 scan SSIDs

No result, it even does not recognize the networks nearby it previously did.
```

---

### Post by matt_symes on 2013-06-06
Hi

Just to let you know, i have the same chip in a Lenovo S206 and i had to use the wl driver to be able to connect at all.

The open source driver would allow me to scan but would not seem to allow me to connect.

```
matthew-S206:/home/matthew % sudo dmidecode -qt 1 | egrep -v "Serial|UUID"
System Information
        Manufacturer: LENOVO
        Product Name: 2638
        Version: Lenovo IdeaPad S206
        Wake-up Type: Power Switch
        SKU Number: LENOVO_BIOSID
        Family: IDEAPAD

matthew-S206:/home/matthew % lspci -nnk | grep -iA2 net                   
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
        Subsystem: Broadcom Corporation Device [14e4:0587]
        Kernel driver in use: wl
matthew-S206:/home/matthew % sudo lshw -c network                         
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: c0:14:3d:c7:03:c9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.0.100 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:f0000000-f0003fff
matthew-S206:/home/matthew % 

```

Posting from it now.

Kind regards

---

### Post by thomas0327 on 2013-06-06
NEWS: Suddenly it connected again (17:02) and disconnected again, after 10sec or whatever. No reason what could cause this action.

---

### Post by thomas0327 on 2013-06-06
Another connection, I removed the cable, and now it operates with wi-fi. What the...? :p

Update 17:13: It worked well for 2mins but disconnected again. Now it operates with cable.

Matthew: I tried what you described, here's the output:

thomas-Lenovo-G585 thomas #  sudo dmidecode -qt 1 | egrep -v "Serial|UUID"System Information
	Manufacturer: LENOVO
	Product Name: 20137
	Version: Lenovo G585
	Wake-up Type: Power Switch
	SKU Number: 123456789
	Family: IDEAPAD


thomas-Lenovo-G585 thomas # lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Lenovo Device [17aa:397f]
	Kernel driver in use: r8169
07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0587]
	Kernel driver in use: bcma-pci-bridge
thomas-Lenovo-G585 thomas # sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: dc:0e:a1:f3:fe:fb
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.198 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f0100000-f0103fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: c0:14:3d:d1:a5:9f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.8.0-23-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

---

### Post by chili555 on 2013-06-06
> Update 17:13: It worked well for 2mins but disconnected again. Now it operates with cable.We would love to see the syslog showing the disconnect:```
cat /var/log/syslog | grep -e wlan -e 80211 | tail -n20
```This is a tricky device. Some work quite well with the proprietary driver wl; others only seem to work with brcmsmac. So far, we have found little reason for either.

Is your router set for:

* AES or TKIP;

* WPA and WPA2 or strictly WPA2 only;

* B, G and N speeds or B and G only; and

*QOS?

With your help, let's try to solve this device's peculiarities forever!

---

