---
title: "unstable wifi on 12.04"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by RooSH23 on 2012-05-03
I've been trying all of the different solutions suggested on this forum, but none have been helpful for me.
after upgrading to 12.04 i keep getting error messages, and the system keep crashing couple of minutes after startup.
I am running ubuntu 12.04 on dell vostro 1310.

```
lspci -vvnn | grep 14e4
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

```
rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Any help would be appreciated...

---

### Post by kc1di on 2012-05-03
Which broadcom driver are you using?

it should be STA.

---

### Post by TBABill on 2012-05-03
> **kc1di said:**
> Which broadcom driver are you using?
 
it should be STA.
 +1 on the STA. If you had also tried to install the b43, make sure you have it blacklisted in /etc/modprobe.d/blacklist.conf

---

### Post by RooSH23 on 2012-05-03
I installed STA, but I getting a FATAL message
```
modprobe bcm43xx
FATAL: Module bcm43xx not found.
```

How do I blacklist exactly?

---

### Post by kc1di on 2012-05-03
> **RooSH23 said:**
> I installed STA, but I getting a FATAL message
```
modprobe bcm43xx
FATAL: Module bcm43xx not found.
```

How do I blacklist exactly?

here's a page that explains that:

[http://www.cyberciti.biz/tips/avoid-linux-kernel-module-driver-autoloading.html]("http://www.cyberciti.biz/tips/avoid-linux-kernel-module-driver-autoloading.html")

please run the following command and post output here

```
lsmod
```

---

### Post by RooSH23 on 2012-05-03
```
lsmod
Module                  Size  Used by
hidp                   22628  1 
hid                    99559  1 hidp
dm_crypt               23125  0 
ipt_ULOG               17439  1 
x_tables               29846  1 ipt_ULOG
joydev                 17693  0 
bnep                   18281  2 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
rfcomm                 47604  12 
parport_pc             32866  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
dell_laptop            18119  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14490  1 dell_laptop
lib80211_crypt_tkip    17390  0 
ppdev                  17113  0 
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   2568210  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
psmouse                87692  0 
serio_raw              13211  0 
v4l2_compat_ioctl32    17128  1 videodev
soundcore              15091  1 snd
lib80211               14381  2 lib80211_crypt_tkip,wl
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
btusb                  18288  4 
bluetooth             180104  28 hidp,bnep,rfcomm,btusb
binfmt_misc            17540  1 
coretemp               13525  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
r8169                  62099  0 
i915                  468651  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
wmi                    19256  1 dell_wmi
video                  19596  1 i915

```

edited blacklisting

```
cat /etc/modprobe.d/blacklist.conf 
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
blacklist b43

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

```

---

### Post by kc1di on 2012-05-03
the wl module is loaded which should be the correct one and I don't see any other wireless modules loaded so it should work. 

but maybe try going to network center and making sure everything is set up correctly.(right click on wireless icon in panel and select edit connections) 
see if the following parameters are set
under wireless tab then select edit

under MTU select automatic for now. 


under Ipv4 settings select automatic DHCP
Ipv6 automatic
under wireless security wpa & wpe personal ?> or what ever your router requires.

---

### Post by TBABill on 2012-05-03
The module you would want to modprobe, assuming you needed to, is wl. That's the module for the STA driver. You have b43 correctly blacklisted. If you want to disable and then re-enable the STA driver, just ```
sudo modprobe -r wl
``` Then ```
sudo modprobe wl
```If you are unable to use it I would suggest ```
sudo apt-get install --reinstall bcmwl-kernel-source
```while connected via ethernet, then ```
sudo modprobe wl
```Wait a few moments, then try to connect.

---

