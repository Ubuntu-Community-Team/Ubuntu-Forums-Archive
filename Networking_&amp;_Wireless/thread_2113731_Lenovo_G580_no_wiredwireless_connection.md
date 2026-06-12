---
title: "Lenovo G580 no wired/wireless connection"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by Cyrebo on 2013-02-08
I can't seem to get a wired connection or wireless connection on either Kubuntu and Ubuntu 12.10. I've followed several guides like this: [http://ubuntuforums.org/showthread.php?t=2050126](http://ubuntuforums.org/showthread.php?t=2050126) on installing the driver for my Atheros 8162 network driver to no avail.

While trying to install the network drivers which i download and copied over I ran into another problem which is: **make:gcc:command not found**. I then went and installed every single package for gcc, g++, lib-c6,dpkg, make and build essentials and it still refused to work. It said I was still missing dependencies.

Is there a way of checking what version of all the build essentials i have?

Thanks in advance for all help is much appreciated

---

### Post by praseodym on 2013-02-08
Hi,

please show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
lsusb
iwconfig
ifconfig -a
rfkill list
route -n
```

---

### Post by Cyrebo on 2013-02-09
Thanks for the reply. I have managed to tether a wireless connection using my mobile phone which i'm using now. Using this i installed build essentials and the compat-wireless package i was trying to get but still no direct access using wired or wireless connection. Anyways here is the output of the commands:

**uname -a**
Linux ubuntu 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

**lspci -nnk | grep iA2 net:**
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 08)
        Subsystem: Lenovo Device [17aa:3979]
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
        Subsystem: Broadcom Corporation Device [14e4:0587]
        Kernel driver in use: bcma-pci-bridge

**lsmod:**
Module                  Size  Used by
nls_iso8859_1          12714  1 
rndis_wlan             37072  0 
cfg80211              206797  1 rndis_wlan
rndis_host             13856  1 rndis_wlan
cdc_ether              13495  1 rndis_host
usbnet                 26160  3 rndis_wlan,rndis_host,cdc_ether
usb_storage            48839  1 
joydev                 17458  0 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_conexant    57843  1 
ipt_ULOG               17440  1 
x_tables               29757  1 ipt_ULOG
coretemp               13401  0 
kvm                   414071  0 
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
snd_hda_intel          33492  5 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
microcode              22804  0 
snd_pcm                96668  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               76750  0 
snd                    78921  19 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
psmouse                95595  0 
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
serio_raw              13216  0 
lpc_ich                17062  0 
bcma                   35657  0 
mei                    40691  0 
bnep                   18141  2 
rfcomm                 46620  0 
bluetooth             209249  10 bnep,rfcomm
parport_pc             32689  0 
ppdev                  17074  0 
mac_hid                13206  0 
ideapad_laptop         18087  0 
sparse_keymap          13891  1 ideapad_laptop
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
i915                  520621  3 
drm_kms_helper         49113  1 i915
drm                   288721  4 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
video                  19336  1 i915

**lsusb:**
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 004: ID 0bb4:0ffe HTC (High Tech Computer Corp.) Desire HD (modem mode)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 002 Device 003: ID 5986:0294 Acer, Inc

**iwconfig:**
usb0      no wireless extensions.

lo        no wireless extensions.

**ifconfig -a:**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24323 (24.3 KB)  TX bytes:24323 (24.3 KB)

usb0      Link encap:Ethernet  HWaddr ba:52:8e:39:4e:a0  
          inet addr:192.168.42.59  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::b852:8eff:fe39:4ea0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15780 errors:1 dropped:0 overruns:0 frame:1
          TX packets:9853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20699636 (20.6 MB)  TX bytes:1529780 (1.5 MB)

**rfkill list:**
0: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: ideapad_bluetooth: Bluetooth
        Soft blocked: yes
        Hard blocked: no

**route -n:**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0

---

### Post by praseodym on 2013-02-09
Install the following driver and firmware update:
```

sudo apt-get install --reinstall linux-headers-generic build-essential dkms linux-backports-modules-cw-3.6-precise-generic
wget http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_fae7121.tar.gz -C /lib/firmware 
sudo modprobe -rfv bcma
sudo modprobe -v brcmsmac
```

---

### Post by Cyrebo on 2013-02-09
Got the following error message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-cw-3.6-precise-generic
E: Couldn't find any package by regex 'linux-backports-modules-cw-3.6-precise-generic'

**EDIT:** It actually worked, i just did the last 3 commands, only the first one had an error message, thanks again!

---

### Post by Cyrebo on 2013-02-09
> **Cyrebo said:**
> Got the following error message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-cw-3.6-precise-generic
E: Couldn't find any package by regex 'linux-backports-modules-cw-3.6-precise-generic'

**EDIT:** It actually worked, i just did the last 3 commands, only the first one had an error message, thanks again!

Last 4 i mean

---

### Post by praseodym on 2013-02-09
```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms linux-backports-modules-cw-3.6-[COLOR="Red"]quantal[/COLOR]-generic
```
Sorry, I meant "quantal".

---

