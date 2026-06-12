---
title: "Wireless network disabled on Dell Inspiron 1720"
date: 2012-01-31
forum: Networking &amp; Wireless
---

### Post by gnourta on 2012-01-31
Hi, I have Dell laptop Inspiron 1720 with Ubuntu 10.04 installed. The wired network works but the wireless is not

---

### Post by gnourta on 2012-01-31
Hi, I have Dell laptop Inspiron 1720 with Ubuntu 10.04 installed. The wired network works but the wireless is not
Am I right in thinking that the problem seems to be that the driver b43 is not loaded  and could not be found on the 

compat_firmware_38_generic-pae.sh[1939]: Cannot find  firmware file 'b43-open/ucode11.fw' ?

 Can someone help point me to the right path of getting the wireless wlan0 to work. Thanks.



sudo lshw -class network
[sudo] password for atruong:
  *-network              
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f9ffc000-f9ffffff memory:f0000000-f00fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:6d:40:89
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.198 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:f9bfe000-f9bfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:e1:5a:17:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.32-38-generic-pae firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
atruong@dell080808:~$ sudo lshw -class network
[sudo] password for atruong:
  *-network              
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f9ffc000-f9ffffff memory:f0000000-f00fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:6d:40:89
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.198 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:f9bfe000-f9bfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:e1:5a:17:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.32-38-generic-pae firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
atruong@dell080808:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:1F:E1:5A:17:CD

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        00:21:70:6D:40:89

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.198
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


atruong@dell080808:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network              
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f9ffc000-f9ffffff memory:f0000000-f00fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:6d:40:89
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.2.198 latency=64 multicast=yes
       resources: irq:17 memory:f9bfe000-f9bfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:e1:5a:17:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.32-38-generic-pae firmware=N/A multicast=yes wireless=IEEE 802.11bg
atruong@dell080808:~$ sudo lshw -C network
  *-network              
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f9ffc000-f9ffffff memory:f0000000-f00fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:6d:40:89
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.198 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:f9bfe000-f9bfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:e1:5a:17:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.32-38-generic-pae firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
atruong@dell080808:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1
ppdev                   5259  0
rfcomm                 32083  4
joydev                  8740  0
snd_hda_codec_idt      52042  1
arc4                    1153  2
snd_hda_intel          22165  2
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0
snd_seq_oss            26722  0
snd_seq_midi            4557  0
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
b43                   289628  0
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nouveau               467624  2
mac80211              247057  1 b43
psmouse                63677  0
dell_wmi                1793  0
ttm                    49943  1 nouveau
drm_kms_helper         29329  1 nouveau
uvcvideo               57470  0
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
btusb                  11117  2
bluetooth              57209  9 rfcomm,sco,bnep,l2cap,btusb
dell_laptop             6888  0
dcdbas                  5490  1 dell_laptop
ricoh_mmc               2923  0
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci_pci               5502  0
sdhci                  15654  1 sdhci_pci
cfg80211              151374  2 b43,mac80211
serio_raw               3978  0
compat_firmware_class     6296  1 b43
drm                   164436  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            5028  1 nouveau
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
intel_agp              24671  0
agpgart                31788  3 ttm,drm,intel_agp
video                  17375  0
output                  1871  1 video
lp                      7028  0
parport                32635  2 ppdev,lp
usbhid                 36206  0
hid                    67288  1 usbhid
b44                    24856  0
ssb                    45765  2 b43,b44
ohci1394               27238  0
usb_storage            40065  2
mii                     4381  1 b44
ieee1394               81213  1 ohci1394
pcmcia                 30912  2 b43,ssb
compat                  7331  5 b43,mac80211,btusb,cfg80211,ssb
led_class               2864  3 b43,sdhci,compat
pcmcia_core            32996  2 pcmcia,compat
ahci                   32712  2
atruong@dell080808:~$ lsmod | grep 44
videodev               34425  1 uvcvideo
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   164436  4 nouveau,ttm,drm_kms_helper
b44                    24856  0
ssb                    45765  2 b43,b44
mii                     4381  1 b44
atruong@dell080808:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID off/any 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm  
          Retry  long limit:7   RTS thr off   Fragment thr off
          Encryption key off
          Power Management off
         
pan0      no wireless extensions.

atruong@dell080808:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
atruong@dell080808:~$ ^C
atruong@dell080808:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID ff/any 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm  
          Retry  long limit:7   RTS thr off   Fragment thr off
          Power Management off

atruong@dell080808:~$ lsmod | grep b43
b43                   289628  0
mac80211              247057  1 b43
cfg80211              151374  2 b43,mac80211
compat_firmware_class     6296  1 b43
ssb                    45765  2 b43,b44
pcmcia                 30912  2 b43,ssb
compat                  7331  5 b43,mac80211,btusb,cfg80211,ssb
led_class               2864  3 b43,sdhci,compat

sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -ewlan0 | tail -n35
Jan 31 14:07:28 dell080808 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 31 14:07:28 dell080808 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 31 14:07:28 dell080808 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 31 14:07:28 dell080808 NetworkManager: <info>  (wlan0): bringing up device.
Jan 31 14:07:28 dell080808 compat_firmware_38_generic-pae.sh[1931]: Cannot find  firmware file 'b43/ucode11.fw'
Jan 31 14:07:28 dell080808 NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 4)
Jan 31 14:07:28 dell080808 NetworkManager: <info>  Activation (wlan0) failed for access point (mynails)
Jan 31 14:07:28 dell080808 NetworkManager: <info>  Activation (wlan0) failed.
Jan 31 14:07:28 dell080808 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 31 14:07:28 dell080808 NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jan 31 14:07:28 dell080808 NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jan 31 14:07:28 dell080808 kernel: [ 2133.585459] b43-phy0 ERROR: f007dad0
Jan 31 14:07:28 dell080808 kernel: [ 2133.585463] b43-phy0 ERROR: f007dad0
Jan 31 14:07:28 dell080808 compat_firmware_38_generic-pae.sh[1939]: Cannot find  firmware file 'b43-open/ucode11.fw'
Jan 31 14:07:30 dell080808 kernel: [ 2133.585466] b43-phy0 ERROR: f007d9e8
Jan 31 15:42:22 dell080808 NetworkManager: <info>  Activation (wlan0) starting connection 'dbstart'
Jan 31 15:42:22 dell080808 NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jan 31 15:42:22 dell080808 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 31 15:42:22 dell080808 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 31 15:42:22 dell080808 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 31 15:42:22 dell080808 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 31 15:42:22 dell080808 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 31 15:42:22 dell080808 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 31 15:42:22 dell080808 NetworkManager: <info>  (wlan0): bringing up device.
Jan 31 15:42:22 dell080808 compat_firmware_38_generic-pae.sh[2485]: Cannot find  firmware file 'b43/ucode11.fw'
Jan 31 15:42:22 dell080808 NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 4)
Jan 31 15:42:22 dell080808 NetworkManager: <info>  Activation (wlan0) failed for access point (dbstart)
Jan 31 15:42:22 dell080808 NetworkManager: <info>  Activation (wlan0) failed.
Jan 31 15:42:22 dell080808 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 31 15:42:22 dell080808 NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jan 31 15:42:22 dell080808 NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jan 31 15:42:22 dell080808 kernel: [ 7827.857345] b43-phy0 ERROR: f007dad0
Jan 31 15:42:22 dell080808 kernel: [ 7827.857349] b43-phy0 ERROR: f007dad0
Jan 31 15:42:22 dell080808 compat_firmware_38_generic-pae.sh[2492]: Cannot find  firmware file 'b43-open/ucode11.fw'
Jan 31 15:46:46 dell080808 kernel: [ 7827.857352] b43-phy0 ERROR: f007d9e8
atruong@dell080808:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
E: Couldn't find package firmware-b43-installer
atruong@dell080808:~$ sudo modprobe -r wl
FATAL: Module wl not found.
atruong@dell080808:~$ sudo modprobe b43
atruong@dell080808:~$ gksudo gedit /etc/modules
atruong@dell080808:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
.....

Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,058B]
Fetched 1,732kB in 5s (309kB/s)                    
Reading package lists... Done
atruong@dell080808:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
E: Couldn't find package firmware-b43-installer

---

### Post by UltimateCat on 2012-01-31
If you can open a terminal and post commands members of the forum can be of help.

Command:
```
lspci

```
Is a command for displaying info about all PCI buses in the system and all devices connected to them.  It is also useful when you want to diagnose problems or when you want to report bugs related to PCI devices.

Also, finding out the NIC ( network interface card) will be helpful because sometimes you might  need a driver to aid it.

Go up to your Menu:  System> Administration> Hardware Drivers
There you will find information about your drivers and if they are working properly.

Your can find help at:
[http://ubuntu.com/community](http://ubuntu.com/community)

---

### Post by praseodym on 2012-02-01
Try this firmware package:

```
wget http://media.ubuntuusers.de/forum/attachments/2480236/Broadcom_Firmware.tar.gz 
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

### Post by 23senick on 2012-02-01
broadcom wireless cause a few problems (try "googling broadcom ubuntu wireless fix"). My sympathies, I had same problems.  But don't despair, many people simply fix it by going into system settings/additional drivers and activating a broadcom driver listed there. Or you may find ubuntu loads old drivers which don't work, so you need to blacklist them.  My struggles ended here...
[http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170)

---

### Post by ts3 on 2012-02-02
> **gnourta said:**
> 
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
  
b43-fwcutter is already the newest version.
E: Couldn't find package firmware-b43-installer

Hello, I know little about wireless apart from the particular chipset on my own laptop that I struggled with (different from yours) and I am not at my ubuntu laptop so can't check but seeing the error message above the first thing I'd do is go to Ubuntu Software Centre, type b43 in the search box, check if b43 supports your wireless BCM4328 and if it does I'd install the firmware-b43-installer through the software centre.  

If that does not work I'd check for conflicts and blacklisted drivers, and also do a bit more research with that particular BCM4328 as a search term to find a solution.  

Hope this helps,  
Cheers :)

---

### Post by sffvba[e0rt on 2012-02-03
Duplicate threads merged.


404

---

### Post by collisionystm on 2012-02-03
post the output of

rfkill list

---

