---
title: "Networking Wireless Problem"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by Ardichoke on 2011-09-04
Hi everybody!

I've had an issue with my network and wireless connection since last night. I've got 11.04 installed on my laptop and the problem has been effecting file sharing between my laptop and the dekstop as well as my wireless connection. Before then it had been working fine but for some reason it has started to act up.

At the moment I'm on my laptop with an ethernet cable plugged in and it's connecting... but much slower than before. Additionally, at the top bar connection manager it's indicating that it's connected via the wireless and not the ethernet. Although when I unplug the ethernet cable, it doesn't connect to the internet or the home network anymore.

Any help would be greatly appreciated.

Thanks!

**lspci -nn**

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 18)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 18)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1]
01:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]
02:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
03:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
7f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
7f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
7f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
7f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
7f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
7f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)

**lsusb**
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:c21c Suyin Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**rfkill list all**
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no

**lsmod**

Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi           13132  0 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            25269  1 snd_seq_midi
i915                  451068  8 
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                925094  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
acer_wmi               23153  0 
lib80211_crypt_tkip    17203  0 
sparse_keymap          13666  1 acer_wmi
wl                   2642531  0 
uvcvideo               66851  0 
ttm                    65184  1 radeon
drm_kms_helper         40745  2 radeon,i915
videodev               75143  1 uvcvideo
psmouse                59039  0 
drm                   184164  6 radeon,i915,ttm,drm_kms_helper
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  2 i915,radeon
lib80211               14570  2 lib80211_crypt_tkip,wl
video                  18951  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
intel_ips              17769  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
atl1c                  36237  0 
ardiastarto@Normandy:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi           13132  0 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            25269  1 snd_seq_midi
i915                  451068  8 
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                925094  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
acer_wmi               23153  0 
lib80211_crypt_tkip    17203  0 
sparse_keymap          13666  1 acer_wmi
wl                   2642531  0 
uvcvideo               66851  0 
ttm                    65184  1 radeon
drm_kms_helper         40745  2 radeon,i915
videodev               75143  1 uvcvideo
psmouse                59039  0 
drm                   184164  6 radeon,i915,ttm,drm_kms_helper
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  2 i915,radeon
lib80211               14570  2 lib80211_crypt_tkip,wl
video                  18951  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
intel_ips              17769  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
atl1c                  36237  0 
ardiastarto@Normandy:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi           13132  0 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            25269  1 snd_seq_midi
i915                  451068  8 
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                925094  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
acer_wmi               23153  0 
lib80211_crypt_tkip    17203  0 
sparse_keymap          13666  1 acer_wmi
wl                   2642531  0 
uvcvideo               66851  0 
ttm                    65184  1 radeon
drm_kms_helper         40745  2 radeon,i915
videodev               75143  1 uvcvideo
psmouse                59039  0 
drm                   184164  6 radeon,i915,ttm,drm_kms_helper
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  2 i915,radeon
lib80211               14570  2 lib80211_crypt_tkip,wl
video                  18951  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
intel_ips              17769  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
atl1c                  36237  0 

**cat /etc/modprobe.d/blacklist.conf**

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

