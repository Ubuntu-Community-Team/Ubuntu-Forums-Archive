---
title: "(Wireless) Device not ready (firmware missing)"
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by Rawrzarz on 2012-02-11
Hello, im using Ubuntu 11.10. I cannot connect to the internet what so ever in Ubuntu. I am dual booting this with Windows 7. Please help if you can. Sorry if i dont understand what you might say.

---

### Post by mikewhatever on 2012-02-11
Hi, and welcome to the forums.

We need to know more about the wireless hardware. You can either look it up in the Windows device manager, or, in Ubuntu, open a terminal window (ctrl+alt+t) and post the output of 'lsmod'.

---

### Post by kurt18947 on 2012-02-11
> **mikewhatever said:**
> Hi, and welcome to the forums.

We need to know more about the wireless hardware. You can either look it up in the Windows device manager, or, in Ubuntu, open a terminal window (ctrl+alt+t) and post the output of 'lsmod'.

And perhaps the output of 'lspci' if the wireless device is internal or 'lsusb' if the device is a USB plug-in.  We're looking for a line that looks something like this:
**Bus 002 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]**

Certain chip families tend to have certain issues.  For example rtl-8192SU chipsets needed an updated firmware file copied into a certain location on Ubuntu releases prior to 11.04.  That is one example, not necessarily your problem.

---

### Post by Rawrzarz on 2012-02-12
> **mikewhatever said:**
> Hi, and welcome to the forums.

We need to know more about the wireless hardware. You can either look it  up in the Windows device manager, or, in Ubuntu, open a terminal window  (ctrl+alt+t) and post the output of 'lsmod'.

LSMOD
Module                  Size  Used by
nls_utf8               12557  1 
udf                    93640  2 
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
snd_hda_codec_realtek   330769  1 
snd_usb_audio         118064  4 
snd_usbmidi_lib        25371  1 snd_usb_audio
snd_hda_intel          33390  4 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                96755  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
dcdbas                 14490  0 
arc4                   12529  2 
psmouse                73882  0 
joydev                 17693  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
b43                   341198  0 
serio_raw              13166  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              310872  1 b43
snd_timer              29991  2 snd_pcm,snd_seq
i915                  566711  3 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              199587  2 b43,mac80211
drm_kms_helper         42558  1 i915
snd                    68266  27 snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
soundcore              12680  1 snd
video                  19412  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
usbhid                 47198  0 
hid                    95463  1 usbhid
uas                    18027  0 
ahci                   26002  2 
libahci                26861  1 ahci
r8169                  52788  0 
firewire_ohci          40722  0 
ssb                    52752  1 b43
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  2 udf,firewire_core



> **kurt18947 said:**
> And perhaps the output of 'lspci' if the wireless device is internal or 'lsusb' if the device is a USB plug-in.  We're looking for a line that looks something like this:
**Bus 002 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]**

Certain chip families tend to have certain issues.  For example rtl-8192SU chipsets needed an updated firmware file copied into a certain location on Ubuntu releases prior to 11.04.  That is one example, not necessarily your problem.

I couldnt find it, but i will still paste my results for both lspci and lsusb



LSUSB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 004 Device 002: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 007 Device 002: ID 046d:c52a Logitech, Inc. 

LSPCI

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation 82801H (ICH8 Family) Thermal Reporting Device
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
04:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)

---

### Post by mikewhatever on 2012-02-13
Thanks for the outputs. You have a BCM4321 wireless, as indicated by the following line:
```
04:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
```

To install the driver, plug in an ethernet cable, you should get a prompt after a minute or so. If no prompt appears, search for 'drivers' in the Dash search field.

---

### Post by Rawrzarz on 2012-02-13
> **mikewhatever said:**
> plug in an ethernet cable

Is there another way? i am unavailable to plug in a Ethernet cable.

---

### Post by varunendra on 2012-02-14
> **Rawrzarz said:**
> Is there another way? i am unavailable to plug in a Ethernet cable.
You can manually download the '.deb. packages of bcmwl-kernel-source + its dependencies from [here]("http://packages.ubuntu.com/oneiric/bcmwl-kernel-source"), then copy them to ubuntu and double-click to install. But satisfying dependencies may get tricky sometimes.

---

### Post by mikewhatever on 2012-02-14
Check out the howto: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access)

---

### Post by Rawrzarz on 2012-02-14
> **varunendra said:**
> You can manually download the '.deb. packages of bcmwl-kernel-source + its dependencies from [here]("http://packages.ubuntu.com/oneiric/bcmwl-kernel-source"), then copy them to ubuntu and double-click to install. But satisfying dependencies may get tricky sometimes.

Which download should i chose in [http://packages.ubuntu.com/oneiric/bcmwl-kernel-source](http://packages.ubuntu.com/oneiric/bcmwl-kernel-source) ?

---

### Post by josephmills on 2012-02-14
Hi there could we see a ```
lspci -nn | grep 14e4
``` the -nn is for name and number of the card. please see [Why this is important](http://linuxwireless.org/en/users/Drivers/b43) 

so if you just need firmware as I see the b43 in lsmod 
Might want to try this Post # 11 
[http://ubuntuforums.org/showthread.php?t=1799571&page=2/](http://ubuntuforums.org/showthread.php?t=1799571&page=2/)


Hope that this helps in some way

---

### Post by josephmills on 2012-02-14
> **Lovehang said:**
> Is there another way? i am unavailable to plug in a Ethernet cable.[IMG]<snip>[/IMG]

Yes there is but first lets see the part that you get in red please. 

```
lspci -nn | grep 14e4
```

sould be something like [14e4:4312] or something like that 
if it is the card that I think it is this should be a easy fix I posted something about post#11 on this 
[http://ubuntuforums.org/showthread.p...799571&page=2/](http://ubuntuforums.org/showthread.p...799571&page=2/)

that is how to install the B43 with no ethernet card you do need a computer with a cd or a usb stick to transfer the files over. But it is best that we see the part in red that you get from lspci -nn | grep 14e4   as we will know for sure that you need the b43 and not the wl or some other driver:) hope this helps

---

