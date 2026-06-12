---
title: "Dwa 140 help"
date: 2011-08-29
forum: Networking &amp; Wireless
---

### Post by DoBa7a on 2011-08-29
Hello, I need some help with installing the drivers for D Link DWA 140 .. The problem is that I don't have any internet connection on the computer without it and I can't download ndiswrapper to install them (I have a disk).

---

### Post by wildmanne39 on 2011-08-29
Hi, please run these commands in terminal:
```
lsusb
```
```
lsmod
```
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by DoBa7a on 2011-08-29
Here, I copied the whole thing that was in terminal. ```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

name@Pccc:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3c0a D-Link System DWA-140 RangeBooster N Adapter(rev.B2) [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
name@Pccc:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
usb_storage            43946  0 
uas                    17676  0 
nls_utf8               12493  1 
isofs                  39571  1 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  4 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
rt2870sta             410104  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
psmouse                73312  0 
nouveau               621970  2 
ttm                    65184  1 nouveau
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17322  0 
serio_raw              12990  0 
soundcore              12600  1 snd
cfg80211              156212  2 rt2x00lib,mac80211
usbhid                 41704  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
hid                    77084  1 usbhid
drm_kms_helper         40745  1 nouveau
drm                   180037  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13184  1 nouveau
video                  18951  1 nouveau
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
jme                    35907  0 
name@Pccc:~$ cat /etc/lsb -release
cat: invalid option -- 'r'
Try `cat --help' for more information.
name@Pccc:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux Pccc 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
name@Pccc:~$ sudo lshw -C network
[sudo] password for name: 
PCI (sysfs)  
SCSI                      
  *-network        
       description: Ethernet interface
       product: JMC260 PCI Express Fast Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 44:87:fc:e8:61:13
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.7 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 memory:febfc000-febfffff ioport:ec00(size=128) ioport:e800(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: 1c:af:f7:73:6f:4f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-8-generic firmware=0.12 link=no multicast=yes wireless=IEEE 802.11bgn
name@Pccc:~$ 
name@Pccc:~$ 
name@Pccc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
name@Pccc:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
name@Pccc:~$ ^C
name@Pccc:~$ 

```

---

### Post by wildmanne39 on 2011-08-29
Hi, lets black list some drivers then see if you can connect.
```
sudo su
echo "blacklist rt2800usb " >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2800lib " >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00usb " >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00lib " >> /etc/modprobe.d/blacklist.conf
exit

```
now restart your computer and see if you can connect.

---

### Post by DoBa7a on 2011-08-29
rt2x00lib: command not found 

Edit: Oh, forget it I typed the whole thing wrong ...

---

### Post by DoBa7a on 2011-08-29
YES! Man I love you! Thanks for the super quick and correct reply!

---

### Post by wildmanne39 on 2011-08-29
Hi, your welcome! glad I could help, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

