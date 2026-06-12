---
title: "canyon cn-wf516 how to make it work"
date: 2013-04-01
forum: Networking &amp; Wireless
---

### Post by startas on 2013-04-01
Is it possible to make my canyon cn-wf516 usb adapter ( [http://wikidevi.com/wiki/CANYON_CN-WF516](http://wikidevi.com/wiki/CANYON_CN-WF516) ) working in ubuntu 12.10 / 13.04 ? In windows this device uses microsoft mn-510 wifi drivers, of course, this device is old, drivers for him are bad and sometimes it causes system freezes, but anyway. In ubuntu 13.04, it detects my usb adapter as Acer WarpLink USB-400. it detecs my wifi connection, but it rejects my password. In wifi settings wep was selected, but my connection uses wpa-personal, i tried to select wpa, but my password still doesnt work. Is there any way to make it work ?

---

### Post by praseodym on 2013-04-01
Please show the outputs of:
```

lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```

---

### Post by startas on 2013-04-04
Ok, so i finally found some time, booted latest 13.04 ubuntu live, and did it :

lsusb
Bus 001 Device 002: ID 13fe:3800 Kingston Technology Company Inc. Rage XT Flash Drive
Bus 005 Device 002: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 005 Device 003: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 006 Device 002: ID 0967:0204 Acer (??) WarpLink 802.11b Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
-----------------------------------------------------------------------------------
lsmod
Module                  Size  Used by
prism2_usb            166935  0 
cfg80211              436177  1 prism2_usb
dm_crypt               22321  0 
snd_hda_codec_analog    75266  1 
snd_hda_intel          38307  4 
snd_hda_codec         117303  2 snd_hda_intel,snd_hda_codec_analog
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
coretemp               13131  0 
kvm_intel             126842  0 
snd_rawmidi            25114  1 snd_seq_midi
kvm                   376505  1 kvm_intel
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
gpio_ich               13236  0 
dm_multipath           22402  0 
scsi_dh                14427  1 dm_multipath
asus_atk0110           17390  0 
snd                    56485  17 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog
microcode              18286  0 
lpc_ich                16925  0 
psmouse                81038  0 
mac_hid                13037  0 
bnep                   17669  2 
serio_raw              13031  0 
rfcomm                 37420  0 
parport_pc             31968  1 
soundcore              12600  1 snd
ppdev                  12817  0 
bluetooth             202069  10 bnep,rfcomm
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
squashfs               35834  1 
overlayfs              27279  1 
nls_iso8859_1          12617  1 
dm_raid45              75357  0 
xor                    26062  1 dm_raid45
dm_mirror              21621  0 
dm_region_hash         16012  1 dm_mirror
dm_log                 18137  3 dm_region_hash,dm_mirror,dm_raid45
pata_acpi              12886  0 
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
nouveau               838609  3 
usb_storage            47684  1 
mxm_wmi                12893  1 nouveau
wmi                    18590  2 mxm_wmi,nouveau
video                  18894  1 nouveau
i2c_algo_bit           13197  1 nouveau
ttm                    71289  1 nouveau
drm_kms_helper         47545  1 nouveau
r8169                  61531  0 
drm                   228750  5 ttm,drm_kms_helper,nouveau
pata_jmicron           12662  0 
ahci                   25507  1 
libahci                26108  1 ahci
--------------------------------------------------------------------------
iwconfig
wlan0     IEEE 802.11b ESSID : off / any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr : off   Fragment thr : off
          Power Management : on
          
lo        no wireless extensions.

eth0      no wireless extensions.

------------------------------------------------------------------------
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
---------------------------------------------------------------------------
iwlist chan
wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
lo        no frequency information.

eth0      no frequency information.
----------------------------------------------------------------------------
sudo iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:9F:85:3A : D3
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key : on
                    ESSID:"ThomsonABD40C"
                    Mode:Master
                    Extra:tsf=000000000000903b
                    Extra: Last beacon: 252ms ago
                    IE: Unknown: 000D54686F6D736F6E414244343043

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by praseodym on 2013-04-05
Try to install these packages via cable:
```

sudo apt-get install linux-wlan-ng linux-wlan-ng-firmware
```
AFAIK this driver only works with WEP encryption. Reboot and check:
```

dmesg | grep prism2
```

---

### Post by startas on 2013-04-08
Well, it still doesnt work with those packages, wifi adapter cant connect...

output of dmesg is :

[  439.709490] prism2_usb: module is from the staging directory, the quality is unknown, you have been warned. 
[  439.712344] prism2_usb: Checking for firmware prism2_ru.fw 
[  439.715342] prism2_usb: Firmware not available, but not essential 
[  439.715347] prism2_usb: can continue to use card anyway. 
[  441.184548] usbcore: registered new interface driver prism2_usb

However, i tried to install windows drivers with ndiswrapper, and it worked, but it freezes ubuntu even more often :D It can load some pages, but when i try to download any file, ubuntu freezes immediately. So, its still unsolved.

---

### Post by praseodym on 2013-04-08
Try ndiswrapper according to this:

[http://ubuntuforums.org/showthread.php?t=885847&p=12592600#post12592600](http://ubuntuforums.org/showthread.php?t=885847&p=12592600#post12592600)

The one from the sources is buggy.

---

### Post by startas on 2013-04-08
With this ubuntu doesnt completely freeze, but internet goes off, and i cant do anything in terminal, i cant restart, shutdown or anything else.

---

### Post by praseodym on 2013-04-08
Hard reset via button? Then install these packages, if possible:

[http://ubuntuforums.org/showthread.php?t=885847&p=12592398#post12592398](http://ubuntuforums.org/showthread.php?t=885847&p=12592398#post12592398)

---

### Post by startas on 2013-04-10
Doesnt help, same thing.

---

