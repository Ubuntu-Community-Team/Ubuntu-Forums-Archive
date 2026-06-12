---
title: "Intel 3945ABG / 12.04 LTS (fresh) / Dell D830"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by marcdonovan on 2012-05-03
I see the driver in lsmod, but not in lspci

```

user@user-Latitude-D830:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

user@user-Latitude-D830:~$ lsb_release -d
Description:    Ubuntu 12.04 LTS
user@user-Latitude-D830:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
user@user-Latitude-D830:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
user@user-Latitude-D830:~$ lsmod
Module                  Size  Used by
snd_hda_codec_idt      60251  1 
joydev                 17393  0 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
dell_laptop            13671  0 
binfmt_misc            17292  1 
dcdbas                 14098  1 dell_laptop
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39791  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 dell_wmi
i915                  414568  3 
mac_hid                13077  0 
psmouse                87213  0 
serio_raw              13027  0 
iwl3945                73111  0 
iwl_legacy             71134  1 iwl3945
mac80211              436455  2 iwl3945,iwl_legacy
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
cfg80211              178679  3 iwl3945,iwl_legacy,mac80211
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40180  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   137273  0 
user@user-Latitude-D830:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

user@user-Latitude-D830:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

user@user-Latitude-D830:~$ uname -mr
3.2.0-24-generic i686
user@user-Latitude-D830:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
user@user-Latitude-D830:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:bd:a0:1f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5755m-v3.29 ip=192.168.0.10 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:fe5f0000-fe5fffff
user@user-Latitude-D830:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no



```I have two such cards and both give me the same symptoms. Hoping you can help....

Thanks!

---

### Post by bkratz on 2012-05-03
Could they (perhaps) be on an internal usb connection?  You could find out with 

lsusb rather than the lspci you tried earlier.

---

### Post by chili555 on 2012-05-03
Suggestion to bkratz: dmesg to pastebin. Does Dell whitelist wireless cards? If he is swapping them in and out, are they seated and the antennae connected securely?

I've subscribed. You're in good hands with bkratz.

---

### Post by marcdonovan on 2012-05-04
I fixed it!

I thought.... maybe there is a setting for this in the bios. Guess what.... disabled. Shoulda checked that first, LOL.

---

### Post by chili555 on 2012-05-04
We're glad it's working! Have fun!

---

### Post by bkratz on 2012-05-04
> **marcdonovan said:**
> I fixed it!

I thought.... maybe there is a setting for this in the bios. Guess what.... disabled. Shoulda checked that first, LOL.


Just checked in and see you got it.  I was wondering what had occurred since the last contact. Sure glad you got it too!

---

