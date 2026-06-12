---
title: "Netgear N300 USB Wireless Adapter Issues"
date: 2013-08-21
forum: Networking &amp; Wireless
---

### Post by jacob5 on 2013-08-21
Hi, 

I recently installed Ubuntu 12.04 LTS on my desktop/workstation system after becoming partial to it on my laptop. I do not currently have an ethernet cable long enough to reach from my network router to the workstation, so I thought I would try using a Netgear N300 USB adapter that I had been using with Windows on the same system. Ubuntu does not detect that any wireless networks are availible, however, ```
lsusb
``` does show the device itself is detected. I installed ndiswrapper using packages downloaded from the "Package Information" Ubuntu site. I transferred the packages to the offline computer with a flashdrive. The installation went smoothly, except for the GTK interface package. I cannot remember the details of the error right now, but will try to recall them if this could be significant. I then configured ndiswrapper, via the terminal, to "wrap" the correct (I assume) drivers, which I copied from my Windows hard-disk. During the last part of the process, the follwing command: ```
modprobe ndiswrapper
``` yields the follwing error: ```
FATAL module ndiswrapper not found
```.

I have done some research, and have found that this could be due to the ndiswrapper package not being compiled for the kernel that I am using. Apparently, it could have something to do with kernel header files, which I know nothing about. 

If you can provide any insight into this issue then it would be greatly appreciated. :)

---

### Post by praseodym on 2013-08-21
Please show the outputs of
```

uname -a
lsusb
iwconfig
lsmod
```
Does LAN work?

---

### Post by jacob5 on 2013-08-21
> **praseodym said:**
> Please show the outputs of
```

uname -a
lsusb
iwconfig
lsmod
```
Does LAN work?

Hi, praseodym. Thank you for your reply. The LAN is working fine on my other devices.

Here is the output from the commands that you requested:

```
uname -a: Linux jacob-Precision-WorkStation-T5400 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

lsusb: Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 005: ID 05dc:a205 Lexar Media, Inc. 
Bus 003 Device 002: ID 045e:0797 Microsoft Corp. 
Bus 004 Device 002: ID 088e:5036 iLok Portable secure storage for software licenses
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

iwconfig: lo        no wireless extensions.

lsmod: Module                  Size  Used by
nls_iso8859_1          12714  1 
usb_storage            49288  1 
dm_crypt               23126  1 
rfcomm                 47562  0 
bnep                   18240  2 
bluetooth             211812  10 rfcomm,bnep
snd_hda_codec_analog    97900  1 
coretemp               13642  0 
kvm                   422160  0 
ppdev                  17114  0 
gpio_ich               13384  0 
dcdbas                 14491  0 
microcode              23030  0 
serio_raw              13216  0 
snd_hda_intel          34117  2 
snd_hda_codec         135141  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  2 snd_hda_intel,snd_hda_codec
parport_pc             32867  1 
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
lpc_ich                17145  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13254  0 
snd                    83674  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
i5400_edac             13395  0 
edac_core              53053  3 i5400_edac
i5k_amb                13288  0 
shpchp                 37278  0 
lp                     17800  0 
parport                46563  3 ppdev,parport_pc,lp
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
firewire_ohci          41034  0 
firewire_core          64697  1 firewire_ohci
crc_itu_t              12708  1 firewire_core
radeon                912794  3 
ttm                    88495  1 radeon
drm_kms_helper         49259  1 radeon
drm                   290344  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13565  1 radeon


```

---

### Post by praseodym on 2013-08-22
You need ndiswrapper and the corresponding windows driver (here 64bit) for Broadcom-USB devices:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms ndisgk ndiswrapper-dkms
```
Driver here:

[http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)

You may need to change the router settings to b/g-mode only.

---

### Post by jacob5 on 2013-08-22
> **praseodym said:**
> You need ndiswrapper and the corresponding windows driver (here 64bit) for Broadcom-USB devices:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms ndisgk ndiswrapper-dkms
```
Driver here:

[http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)

You may need to change the router settings to b/g-mode only.

Is there a way that I can do the first part without being online?

---

### Post by praseodym on 2013-08-24
Download these packages and save them in "Downloads":

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-quantal/linux-headers-3.5.0-23-generic_3.5.0-23.35~precise1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-quantal/linux-headers-3.5.0-23-generic_3.5.0-23.35~precise1_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-quantal/linux-headers-3.5.0-23_3.5.0-23.35~precise1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-quantal/linux-headers-3.5.0-23_3.5.0-23.35~precise1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-quantal/linux-headers-generic-lts-quantal_3.5.0.39.45_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-quantal/linux-headers-generic-lts-quantal_3.5.0.39.45_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.8.5-1ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.8.5-1ubuntu1_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.58-0ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.58-0ubuntu1_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-common_1.58-0ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-common_1.58-0ubuntu1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-dkms_1.58-0ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-dkms_1.58-0ubuntu1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1ubuntu3_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1ubuntu3_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.5-1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.5-1_amd64.deb)

Installation via:
```

sudo dpkg -i ~/Downloads/*.deb
```

---

### Post by jacob5 on 2013-08-25
> **praseodym said:**
> Download these packages and save them in "Downloads":

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-quantal/linux-headers-3.5.0-23-generic_3.5.0-23.35~precise1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-quantal/linux-headers-3.5.0-23-generic_3.5.0-23.35~precise1_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-quantal/linux-headers-3.5.0-23_3.5.0-23.35~precise1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-quantal/linux-headers-3.5.0-23_3.5.0-23.35~precise1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-quantal/linux-headers-generic-lts-quantal_3.5.0.39.45_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-quantal/linux-headers-generic-lts-quantal_3.5.0.39.45_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.8.5-1ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.8.5-1ubuntu1_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.58-0ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.58-0ubuntu1_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-common_1.58-0ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-common_1.58-0ubuntu1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-dkms_1.58-0ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-dkms_1.58-0ubuntu1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1ubuntu3_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1ubuntu3_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.5-1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.5-1_amd64.deb)

Installation via:
```

sudo dpkg -i ~/Downloads/*.deb
```

I really appreciate your help praseodym. However, after installing the packages the issue is still not resolved. After the installations there were some error messages:

```
Errors were encountered while processing:
linux-headers-generic-lts-quantal
ndisgtk

```

Also, when I try to run ndisgtk the terminal outputs the following message:

```
bash: /usr/sbin/ndisgtk: /usr/bin/python3: bad interpreter: No such file or directory
```

I am not sure if it is relevant or not, but the default version of Python installed on my system is 2.7.3 and not Python 3. Could this be part of the issue?

---

### Post by praseodym on 2013-08-25
Try it without these two files. After that install the windows driver via terminal:
```

sudo ndiswrapper -i /path/to/64bit/file.inf
sudo ndiswrapper -ma
sudo modprobe -v ndiswrapper
```
Replug the stick and check
```

iwconfig
sudo iwlist scan
dmesg | grep ndis
```

---

### Post by jacob5 on 2013-08-25
> **praseodym said:**
> Try it without these two files. After that install the windows driver via terminal:
```

sudo ndiswrapper -i /path/to/64bit/file.inf
sudo ndiswrapper -ma
sudo modprobe -v ndiswrapper
```
Replug the stick and check
```

iwconfig
sudo iwlist scan
dmesg | grep ndis
```

Do you mean that I should try re-installing all of the packages except those that were listed in the error messages?

---

### Post by praseodym on 2013-08-26
Yes.

---

