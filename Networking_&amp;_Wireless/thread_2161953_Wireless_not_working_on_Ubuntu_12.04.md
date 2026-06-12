---
title: "Wireless not working on Ubuntu 12.04"
date: 2013-07-12
forum: Networking &amp; Wireless
---

### Post by chandranshu on 2013-07-12
Hi

I have a Dell Vostro 1550 laptop with Ubuntu 12.04. The wireless has stopped working since a month. I can still see wireless networks available in my locality but am unable to connect to them. The problem started after we got a new broadband connection at home and the person sent for installing the cables reset our router to factory settings. Other laptops/mobile devices are able to connect properly. I have tried several different steps mentioned throughout these forums (except configuring ndiswrapper), mostly mentioned at [http://ubuntuforums.org/showthread.php?t=1966633](http://ubuntuforums.org/showthread.php?t=1966633) and the posts linking from there but I think I have a different beast to deal with.

I'm now desperately in need of technical help. Here is the output of the relevant commands as asked in the aforesaid post:
```

$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux kumud-laptop 3.2.0-49-generic-pae #75-Ubuntu SMP Tue Jun 18 18:00:21 UTC 2013 i686 i686 i386 GNU/Linux

```

```
$ lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Dell Device [1028:0508]
    Kernel driver in use: r8169
--
09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0012]
    Kernel driver in use: wl

```

```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0a5c:21bc Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 001 Device 004: ID 0bda:58c1 Realtek Semiconductor Corp.

```

```
$ iwconfig
lo        no wireless extensions.


eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

```

```
$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
```

$ lsmod
Module                  Size  Used by
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
dm_crypt               22528  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
lib80211_crypt_tkip    17275  0 
snd_seq_midi           13132  0 
joydev                 17393  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
btusb                  17948  2 
bluetooth             158479  23 rfcomm,bnep,btusb
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
wl                   2906597  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178877  1 wl
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
psmouse                86520  0 
dell_wmi               12601  0 
serio_raw              13027  0 
sparse_keymap          13658  1 dell_wmi
lib80211               14040  2 lib80211_crypt_tkip,wl
mei                    36570  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
usb_storage            39646  1 ums_realtek
wmi                    18744  1 dell_wmi
r8169                  56368  0 
i915                  428056  3 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19115  1 i915


```

All help is much appreciated.

Regards
Chandranshu

---

### Post by praseodym on 2013-07-12
Does LAN work? If yes, update the native driver, uninstall the STA and install the missing firmware:
```

sudo apt-get install --reinstall linux-headers-generic-pae build-essential dkms linux-backports-modules-cw-3.6-$(grep CODE /etc/lsb-release | cut -c18-28)-$( uname -r | cut -c10-23) 
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```
Shutdown currentless for 10 minutes and reboot.

---

### Post by chandranshu on 2013-07-12
Hi P[COLOR=#000000]raseodym

Thanks a ton! After executing the steps given by you, the wireless starting working immediately.

If it's not asking for too much, could you plz explain the following to me:
[LIST=1]
[*]What was the problem?
[*]How did you diagnose it?
[*]How did performing the steps given by you resolved it?
[/LIST]

Even pointing the direction I should be looking into would be a great help.

Regards
Chandranshu[/COLOR]

---

### Post by praseodym on 2013-07-12
The native driver **brcmsmac** works better than the proprietary STA driver with this card. After a driver update only the proprietary firmware was missing (not shipped)

---

