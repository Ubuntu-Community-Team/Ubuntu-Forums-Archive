---
title: "Wireless not working -  HP dv6000"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by junkbox01 on 2011-08-22
I just install Ubuntu 11.04 on an HP dv6000. Everything is working great except the wireless. It sees the wireless networks and tries to connect, but it never does successfully.

Any help would be much appreciated.

---

### Post by praseodym on 2011-08-22
Hello,

can you post the following terminal outputs:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by junkbox01 on 2011-08-22
lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
    Subsystem: Intel Corporation Vaio VGN-SZ79SN_C [8086:1100]
    Kernel driver in use: iwlagn
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Kernel driver in use: r8169


lsusb
Bus 007 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  0 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_si3054    12924  1 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
rfcomm                 38125  8 
arc4                   12473  2 
snd_hda_intel          24113  2 
sco                    17827  2 
bnep                   17785  2 
snd_hda_codec          90901  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
l2cap                  48656  16 rfcomm,bnep
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
iwlagn                284745  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  451033  3 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13418  0 
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
iwlcore               148964  1 iwlagn
sparse_keymap          13666  1 hp_wmi
mac80211              257001  2 iwlagn,iwlcore
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
r852                   17878  0 
btusb                  18160  2 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
drm                   184164  4 i915,drm_kms_helper
videodev               75143  1 uvcvideo
psmouse                73312  0 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd                    55295  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
mtd                    26720  2 sm_common,nand
cfg80211              156212  3 iwlagn,iwlcore,mac80211
serio_raw              12990  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
r8169                  42534  0 
sdhci_pci              13623  0 
firewire_ohci          31504  0 
libahci                25548  1 ahci
sdhci                  22720  1 sdhci_pci
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


rfkill list
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by praseodym on 2011-08-22
Intel deactivates the N-mode per default. It can be activated by:

```
echo "options iwlagn 11n_disable=0" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo service network-manager stop
sudo modprobe -rf iwlagn
sudo modprobe -v iwlagn
sudo service network-manager start
```

---

### Post by junkbox01 on 2011-08-22
> **praseodym said:**
> Intel deactivates the N-mode per default. It can be activated by:



No luck. It still does the same thing. Anything else?

---

### Post by garvinrick4 on 2011-08-22
The iwlagn is using "N" it will not work in "N" mode:
Will work in "G" and have to set router in 2.4 ghz to mixed so G can work with router
and make a config file to take N out of card.
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```Now install the line below and save: (you are making new config file so will be only line)
options iwlagn 11n_disable50=1 11n_disable=1
and reboot.

---

### Post by garvinrick4 on 2011-08-22
You can use "N" with iwlagn driver with kernel 3.0 and up and change module-init-tools
to 3.13-1ubuntu1 they are all in .deb files already so very easy to install.
Download in your architecture 32 or 64 bit.
Need 3, all.deb, headers and image. Download them and
install in that order can just click on them and ubuntu software center will install
if need any help just ask.
[Index of /~kernel-ppa/mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") 
Will be back to give .deb package link for module-init-tools
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1/+build/2555500](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1/+build/2555500)
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1/+build/2555502](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1/+build/2555502)
#First link is 64 bit second link is 32 bit and will be in lower left of page in .deb
download and install by just clicking on before you install 3.0 and up kernel.
Can be done in sudo dpkg -i "name of .deb package" without quotes from terminal also, if any problems.

## This works in Natty and Maverick but lucid will not accept 3.0 kernel. Oneiric comes with 3.0 and up kernel.

---

### Post by junkbox01 on 2011-08-22
Alright. So I went away for my computer for a little bit. Came back and  the wireless is working, but only on my router in my room. I live on a  college campus, and I need the computer to connect to the campus  internet also.

Is there any reason that it will connect to my router, but not the campus internet?

Also, **garvinrick4**, I have not tried any of your suggestions because it started working on my internet. Should I still try them?

Thanks

---

### Post by garvinrick4 on 2011-08-22
> Also, **garvinrick4**, I have not tried any of your suggestions because it started working on my internet. Should I still try them?

When your card and driver hit at "N" speeds will drop off pretty soon to real slow speeds.
Click on network icon in upper right and go to connection information and will start at
54 or 72 Mb/s or higher and then drop off to 6 or 1 sooner or later. So slow a page will not
load.

Use the first post I gave you and will work in "G" mode everywhere. Will only not work
with routers set a "N" speeds only. Your campus will not have a router set at "N" only to
many "G" cards out there. 

Use my second post if you want your card and driver to work at "G" and "N" speeds everywhere. The fastest "G" will be is 54Mb/s which gets around pretty good. Take your
choice and what your skill set says you are comfortable with.

It was an Intel thing not a Ubuntu thing with the intel wireless iwlagn driver. But as I said
fixed in the 3.0 kernel and up which is part of 11.10 Oneiric but the 3.0 kernel does work
in 11.04 Natty with the changes I told you in my second post.

---

### Post by junkbox01 on 2011-08-22
Finally got it working. Thanks for your help! Keep up the good work!

---

### Post by garvinrick4 on 2011-08-22
Good, I am glad your Ubuntu experience will be better, please mark as Solved
in the upper right side of page called Thread Tools. Have a nice day.

---

