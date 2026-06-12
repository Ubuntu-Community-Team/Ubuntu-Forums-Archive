---
title: "Wireless on Lenovo b570 not working"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by ashluvsu on 2012-05-29
I have a Lenovo b570 laptop and I just installed Ubuntu 12.04.
I can't get my wireless to work and it's driving me nuts.
I'm not sure how to fix it.
I've downloaded the wireless driver, but I'm not sure what to do next.

---

### Post by praseodym on 2012-05-29
Hi,

please show the terminal (CTRL+ALT+T) outputs of these commands:

```
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list
lsmod
```

---

### Post by ashluvsu on 2012-05-29
```
ashlii@ashlii-Lenovo-B570:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Kernel driver in use: brcmsmac
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169
ashlii@ashlii-Lenovo-B570:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:a006 Alcor Micro Corp. 
Bus 002 Device 003: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 002 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. 
ashlii@ashlii-Lenovo-B570:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

ashlii@ashlii-Lenovo-B570:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
ashlii@ashlii-Lenovo-B570:~$ lsmod
Module                  Size  Used by
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
joydev                 17693  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
wl                   2568210  0 
lib80211               14381  1 wl
bcma                   26696  0 
arc4                   12529  2 
acer_wmi               28418  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
rts5139               351143  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
brcmsmac              570859  0 
psmouse                87603  0 
ideapad_laptop         18234  0 
snd_timer              29990  2 snd_pcm,snd_seq
mac80211              506816  1 brcmsmac
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13211  0 
brcmutil               15139  1 brcmsmac
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
wmi                    19256  1 acer_wmi
mac_hid                13253  0 
cfg80211              205544  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
i915                  468651  3 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cordic                 12535  1 brcmsmac
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
soundcore              15091  1 snd
video                  19596  1 i915
mei                    41616  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 

```

---

### Post by praseodym on 2012-05-29
Several things: The Broadcom-STA driver normally works with this card (from Ubuntu 12.04 the native driver b43 should work, too). But there are several modules loaded, that block each other.

Open this file:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```
add the following lines:
```

blacklist bcma
blacklist brcmsmac
blacklist brcm80211
blacklist acer_wmi    #thinkpad!!!
```
Save, close the editor, and reboot. Check after that

```
rfkill list
iwconfig
lsmod
```

---

### Post by shafi.dude99 on 2012-05-29
also paste the output of following command 


sudo cat /etc/modprobe.d/blacklist.conf

---

### Post by ashluvsu on 2012-05-29
Now they're both hardblocked?

```
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

blacklist bcma
blacklist brcmsmac
blacklist brcm80211
blacklist acer_wmi    #thinkpad!!

```

---

### Post by praseodym on 2012-05-30
Check buttons, switches, keys, and key combinations (e.g. Fn+F2) and/or

```
rfkill unblock all
```
Check the BIOS settings, if it can be activated there, maybe resetting the BIOS to default.

---

### Post by ashluvsu on 2012-05-30
rfkill unblock all does nothing in terminal and changing BIOS settings didn't do anything either =/

---

### Post by praseodym on 2012-05-30
Any button on the front between touchpad and SD slot (see pic)?

---

### Post by ashluvsu on 2012-05-30
Lol. I've been trying to fix my computer and my wireless for a week now. Don't insult me XP
So that's definitely switched on. And I've tried the fn+f5 key that's supposed to turn it on too and neither have turned it on.
I'm at a frustrated loss and I'm tired of having to connect it to a wired connection):

---

### Post by praseodym on 2012-05-31
Check any buttons, switches, keys, key combinations, all pressed permanently or repeatedly during booting

---

### Post by ashluvsu on 2012-05-31
I've been searching for ages and I've been having so many problems with my computer.
I found a forum post about Jupiter and a hardware reset.
I installed Jupiter through terminal and then I shut down my computer and took out the battery and held the power button for 30 seconds.
I'm not sure which one of those two things did it, but I'm posting this from my wireless connection(:

---

