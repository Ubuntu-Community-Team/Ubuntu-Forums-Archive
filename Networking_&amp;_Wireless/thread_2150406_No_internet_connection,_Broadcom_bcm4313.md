---
title: "No internet connection, Broadcom bcm4313"
date: 2013-06-01
forum: Networking &amp; Wireless
---

### Post by trepnr on 2013-06-01
Hello, I very recently installed Ubuntu 12.04 and am already having issues. I am completely unable to connect to the internet from it; not through wireless or ethernet. I have a dual boot with Windows 7, in which all internet works fine. I've read on countless threads that it has something to do with my laptop's network card (bcm4313), however, all of the fixes people provided were no help as I can't even connect through ethernet. I really want to like this OS, however, it's kind of hard when you can't even do basic web browsing.

Also, if it makes anything easier, I'm not too concerned about getting ehernet working, as I never use it anyways.

Any help would be greatly appreciated. Thank you.

---

### Post by praseodym on 2013-06-01
Please show these terminal (CTRL+ALT+T) outputs:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```Wired connection will help.

---

### Post by trepnr on 2013-06-01
```
uname 
-aLinux alijahpc 3.5.0-31-generic #52~precise1-Ubuntu SMP Fri May 17 15:27:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```



```
lspci -nnk | grep -iA2 net


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:180b]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel modules: bcma




lsmod
Module                  Size  Used by
hp_wmi                 18093  0 
sparse_keymap          13891  1 hp_wmi
joydev                 17694  0 
snd_hda_codec_idt      70774  1 
snd_hda_codec_hdmi     32476  1 
kvm                   422160  0 
hid_logitech_dj        18768  0 
parport_pc             32867  0 
ppdev                  17114  0 
snd_seq_midi           13325  0 
rfcomm                 47562  12 
bnep                   18240  2 
snd_rawmidi            30750  1 snd_seq_midi
btusb                  22432  0 
bluetooth             211812  24 rfcomm,bnep,btusb
microcode              23030  0 
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_hda_intel          34063  5 
snd_hda_codec         135141  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
videobuf2_memops       13405  1 videobuf2_vmalloc
psmouse               102506  0 
k10temp                13174  0 
serio_raw              13216  0 
snd_timer              29990  2 snd_seq,snd_pcm
i2c_piix4              13302  0 
usbhid                 47259  1 hid_logitech_dj
hid                   100815  2 hid_logitech_dj,usbhid
radeon                917824  3 
snd                    83674  20 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
ttm                    88495  1 radeon
drm_kms_helper         49259  1 radeon
rtsx_pci_ms            13181  0 
drm                   290344  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13565  1 radeon
memstick               16606  1 rtsx_pci_ms
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
wmi                    19257  1 hp_wmi
video                  19653  0 
hp_accel               25977  0 
lis3lv02d              19878  1 hp_accel
input_polldev          13897  1 lis3lv02d
mac_hid                13254  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
rtsx_pci_sdmmc         17801  0 
sdhci_pci              18749  0 
pata_atiixp            13205  0 
sdhci                  33145  1 sdhci_pci
rtsx_pci               33680  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25869  3 
libahci                27338  1 ahci
r8169                  62766  0 

```

```
iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.

```

```
rfkill list
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

I'm unable to get a wired connection to work with Ubuntu (nothing is detected when I plug it in, same with wireless), however I can download stuff from Windows.

---

### Post by trepnr on 2013-06-01
Anyone?

---

### Post by praseodym on 2013-06-02
Download the following package and save it in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz)

Install it via:

```
sudo tar xvf ~/Downloads/5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware
```
Shutdown completely currentless for 10 minutes. Then reboot. Wireless should work now.

For ethernet you can now install the driver according to this "with dkms":

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

---

