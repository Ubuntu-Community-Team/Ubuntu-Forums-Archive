---
title: "Netgear WG111T not working on Precise?"
date: 2012-07-31
forum: Networking &amp; Wireless
---

### Post by iMurshaq on 2012-07-31
Hey all!!!

Wow its good to be back on Ubuntu but its inevitable that there will be issues and sadly they have arisen early this time around! I'm having trouble getting my Netgear WG111T Wireless-G USB adapter working on Precise and I have been having trouble getting Ubuntu to detect it or install any drivers. I have been able to find fixes for older versions of Ubuntu but they have become obsolete with the release of Precise. Any help would be greatly appreciated!!

iMurshaq

P.S. The computer is an eMachines EL-1333G-01w if that is necessary.

---

### Post by iMurshaq on 2012-07-31
Bumparooni

---

### Post by praseodym on 2012-07-31
Please show:

> lsusb
lsmod
iwconfig
rfkill list

---

### Post by iMurshaq on 2012-07-31
lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1385:4251 Netgear, Inc WG111T (no firmware)
Bus 001 Device 004: ID 058f:6361 Alcor Micro Corp. Multimedia Card Reader
Bus 002 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 001 Device 014: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter [GL811E]

```

lsmod
```
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
isofs                  39553  1 
dm_crypt               22528  0 
bnep                   17830  2 
rfcomm                 38139  4 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   174055  1 
binfmt_misc            17292  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
nvidia              10971098  40 
snd_seq_midi           13132  0 
acer_wmi               23612  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
sparse_keymap          13658  1 acer_wmi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                72846  0 
serio_raw              13027  0 
joydev                 17393  0 
wmi                    18744  1 acer_wmi
k8temp                 12905  0 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77367  1 usbhid
forcedeth              58096  0 
pata_amd               13750  0 
sata_nv                23360  3 
usb_storage            39646  1 

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

rfkill list
```
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Does that help at all???

---

### Post by praseodym on 2012-07-31
Did you try ndiswrapper?

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms ndiswrapper-utils-1.9 ndiswrapper-common ndisgtk ndiswrapper-dkms
```
Try the **atheros5523_usb_XPw9x** driver from one of the attached tarballs.

Its from the German forum:

[http://forum.ubuntuusers.de/post/2205984/](http://forum.ubuntuusers.de/post/2205984/)

I have split up the original tarball because of the size. The other 2 drivers are older.

---

### Post by iMurshaq on 2012-07-31
Should I install the ar5523.sys file with wine or is there another way????

---

### Post by praseodym on 2012-08-01
Install the .inf via terminal:

```
sudo ndiswrapper -i /path/to/folder/atheros5523_xpusb.inf
```

Check:

```
ndiswrapper -l
```
If the driver is shown, load the module:

```
sudo modprobe -v ndiswrapper
```
and replug the stick. Check:

```
lsmod
iwconfig
dmesg | grep ndis
rfkill list
sudo iwlist scan
```

---

### Post by iMurshaq on 2012-08-01
ok if the .inf file is in a folder called ath5523usb_mod1 in my downloads folder what would be the path to the file? sorry im a noob

---

### Post by praseodym on 2012-08-01
Then it is:

```
sudo ndiswrapper -i ~/Downloads/ath5523usb_mod1/atheros5523_xpusb.inf
```
But I recommend this one:

atheros5523_usb_XPw9x.tar.gz

---

### Post by iMurshaq on 2012-08-01
I get this output:
```
tyler@EL1333G:~$ sudo ndiswrapper -i ~/Downloads/ath5523usb_mod1/atheros5523_xpusb.inf
couldn't open /home/tyler/Downloads/ath5523usb_mod1/atheros5523_xpusb.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

```

---

### Post by praseodym on 2012-08-01
Wrong driver name from the wrong tarball

---

### Post by iMurshaq on 2012-08-01
Ok the output for the last command string is
```
tyler@EL1333G:~$ sudo modprobe -v ndiswrapper
insmod /lib/modules/3.2.0-27-generic-pae/updates/dkms/ndiswrapper.ko 
tyler@EL1333G:~$ lsmod
Module                  Size  Used by
ndiswrapper           192268  0 
snd_usb_audio         101566  2 
snd_usbmidi_lib        24603  1 snd_usb_audio
isofs                  39553  0 
bnep                   17830  2 
rfcomm                 38139  4 
bluetooth             158438  8 bnep,rfcomm
parport_pc             32114  0 
dm_crypt               22528  0 
ppdev                  12849  0 
snd_hda_codec_realtek   174134  1 
snd_hda_intel          32765  3 
binfmt_misc            17292  1 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
nvidia              10971098  30 
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_pcm                80845  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
snd                    62064  21 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
psmouse                72919  0 
serio_raw              13027  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
k8temp                 12905  0 
joydev                 17393  0 
mac_hid                13077  0 
i2c_nforce2            12906  0 
wmi                    18744  1 acer_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77367  1 usbhid
pata_amd               13750  0 
forcedeth              58096  0 
sata_nv                23360  2 
usb_storage            39646  1 
tyler@EL1333G:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

tyler@EL1333G:~$ dmesg | grep ndis
[85126.656990] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[85126.713172] usbcore: registered new interface driver ndiswrapper
[85146.999160] ndiswrapper: driver net5523_mod1 (,10/04/2004,1.0.1.4) loaded
[85157.004750] ndiswrapper (NdisWriteErrorLogEntry:188): log: C0001389, count: 4, return_address: f9a73cbb
[85157.004763] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xef5e3c00
[85157.004770] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x28
[85157.004777] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xf9466000
[85157.004783] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xf9466000
[85157.005224] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[85157.005236] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[85157.005256] ndiswrapper (mp_halt:254): device f2040480 is not initialized - not halting
[85157.005263] ndiswrapper: device eth%d removed
[85157.005365] ndiswrapper: probe of 1-5:1.0 failed with error -22
tyler@EL1333G:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
tyler@EL1333G:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

tyler@EL1333G:~$ 

```

but the usb stick still wont work

---

### Post by flash63 on 2012-08-02
Hello,
unplug short the stick and connect it again to.

check it once again
```
dmesg | grep ndis
iwconfig
```

---

### Post by iMurshaq on 2012-08-03
```
tyler@EL1333G:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by iMurshaq on 2012-08-03
[praseodym]("http://ubuntuforums.org/member.php?u=1411497") can you please just post a reply with what i shouldve done thus far in simple way so i can repeat it?

---

### Post by praseodym on 2012-08-03
> [85157.005236] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[85157.005256] ndiswrapper (mp_halt:254): device f2040480 is not initialized - not halting
Tried another of these drivers?

---

