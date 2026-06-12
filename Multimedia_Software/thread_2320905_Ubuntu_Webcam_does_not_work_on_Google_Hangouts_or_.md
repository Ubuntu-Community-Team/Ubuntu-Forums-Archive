---
title: "Ubuntu Webcam does not work on Google Hangouts or Skype"
date: 2016-04-18
forum: Multimedia Software
---

### Post by Nahua_Kang on 2016-04-18
Hi y'all!

I installed my Ubuntu 14.04 LTS alongside my Windows system. It's a ThinkPad E555 laptop. I just tried to use Skype and Google Hangouts today but could not get my built-in webcam to work. I would like to be able to use my webcam so please help if you can! Thank you very much!


I ran cheese and it shows "No device found":
```

** Message: cheese-application.vala:291: Error during camera setup: No device found




(cheese:4268): cheese-CRITICAL **: cheese_camera_device_get_device_node: assertion 'CHEESE_IS_CAMERA_DEVICE (device)' failed


(cheese:4268): GLib-CRITICAL **: g_variant_new_string: assertion 'string != NULL' failed


(cheese:4268): GLib-GIO-CRITICAL **: g_settings_schema_key_type_check: assertion 'value != NULL' failed


(cheese:4268): GLib-CRITICAL **: g_variant_get_type_string: assertion 'value != NULL' failed


(cheese:4268): GLib-GIO-CRITICAL **: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given


** (cheese:4268): CRITICAL **: cheese_preferences_dialog_setup_resolutions_for_device: assertion 'device != NULL' failed

```

I also tried:
```

sudo apt-get install cheese build-essential linux-headers-`uname -r`
[sudo] password for kangnahua: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
cheese is already the newest version.
linux-headers-3.19.0-58-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libntdb1 python-appindicator python-ntdb
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

So cheese is the newest and the problem isn't cheese itself. Below is my lsmod:
```

lsmod
Module                  Size  Used by
ctr                    16384  1 
ccm                    20480  1 
fglrx               13512704  162 
bnep                   20480  2 
rfcomm                 69632  8 
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         53248  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
kvm                   479232  0 
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
aesni_intel           172032  3 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
arc4                   16384  2 
joydev                 20480  0 
serio_raw              16384  0 
rtsx_pci_ms            20480  0 
memstick               20480  1 rtsx_pci_ms
edac_core              53248  0 
snd_hda_codec_hdmi     53248  1 
snd_hda_codec_conexant    24576  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_conexant
edac_mce_amd           24576  0 
thinkpad_acpi          86016  1 
k10temp                16384  0 
fam15h_power           16384  0 
rtl8723be             143360  0 
btcoexist             413696  1 rtl8723be
snd_seq_midi           16384  0 
rtl_pci                40960  1 rtl8723be
rtlwifi               135168  3 btcoexist,rtl_pci,rtl8723be
snd_seq_midi_event     16384  1 snd_seq_midi
nvram                  16384  1 thinkpad_acpi
btusb                  40960  0 
mac80211              720896  3 rtl_pci,rtlwifi,rtl8723be
snd_hda_intel          36864  9 snd_hda_codec_hdmi
bluetooth             491520  22 bnep,btusb,rfcomm
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
snd_rawmidi            32768  1 snd_seq_midi
i2c_piix4              24576  0 
cfg80211              532480  2 mac80211,rtlwifi
snd_pcm               106496  6 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
shpchp                 40960  0 
amd_iommu_v2           20480  1 fglrx
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    86016  26 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
soundcore              16384  2 snd,snd_hda_codec
wmi                    20480  0 
video                  20480  0 
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
rtsx_pci_sdmmc         24576  0 
psmouse               118784  0 
r8169                  81920  0 
mii                    16384  1 r8169
ahci                   36864  2 
libahci                32768  1 ahci
rtsx_pci               49152  2 rtsx_pci_ms,rtsx_pci_sdmmc

```

and my lsusb:
```

lsusb
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 5986:055a Acer, Inc 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

