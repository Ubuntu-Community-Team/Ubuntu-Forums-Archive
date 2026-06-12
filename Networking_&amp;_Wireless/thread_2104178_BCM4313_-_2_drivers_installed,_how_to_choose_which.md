---
title: "BCM4313 - 2 drivers installed, how to choose which is used?"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by adamr on 2013-01-12
I've got a BCM4313 in this Lenovo G580, and through various things I've got two drivers installed. wl and bcma.

The problem is bcma is terrible, the connection is slow and frequently drops. Using wl I have a great connection. However, the drivers load randomly, so sometimes bcma loads at boot, sometimes bcma, and I have no idea what I can do to stop bcma loading. I've tried adding it to the blacklist in /etc/modprobe.d/, but it's not making any difference.

Can anyone help either a) remove bcma (the driver that loads for that module is bcma-pci-bridge), or b) make sure wl is the one that loads.

Here is my lspci -vv :

```
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
   Subsystem: Broadcom Corporation Device 0587
   Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
   Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
   Latency: 0, Cache Line Size: 64 bytes
   Interrupt: pin A routed to IRQ 17
   Region 0: Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
   Capabilities: <access denied>
   Kernel driver in use: bcma-pci-bridge
   Kernel modules: wl, bcma
```

---

### Post by steeldriver on 2013-01-12
Hmm... it looks like the bcma-pci-bridge driver might be manually loading the module so I'm not sure how you'd stop that. Unless you have a left-over 'modprobe' in /etc/rc.local for example (which would happen after the boot time blacklist)

There *are* documented ways of manually unbinding / binding drivers to devices (via /sys/bus/[pci|usb]/drivers/) if that's really what it takes - I've never done it though and I've never heard of it being necessary for the BCM4313

---

### Post by adamr on 2013-01-12
If I install the bcmwl-kernel-source drivers from additional drivers, nothing seems to happen. I've checked rc.local, there's nothing in there. 

I've tried manually installing the broadcom drivers from their website, but the make fails because it's for an older kernel.

---

### Post by Hadaka on 2013-01-12
Hi, please post the output of..

```
lsb_release -a 
```
```
 lspci-nn | grep 0280
```
```
 grep -i blacklist /etc/modprobe.d/blacklist.conf
```

thanks.

---

### Post by adamr on 2013-01-12
lspci -nn | grep 0280:
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```

grep -i blacklist /etc/modprobe.d/blacklist.conf:
```
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist bcma-pci-bridge
blacklist bcma
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
blacklist amd76x_edac
```

The bcma-pci-bridge and bcma lines in blacklist.conf are my attempt to stop it loading, which have failed so far.

---

### Post by Hadaka on 2013-01-12
Hi, try this..

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
 
``````
sudo su
echo 'wl' >> /etc/modules  
```boot and see if that helps

*if  the bcma is not removed, then delete the 2 bcma items you
put in /etc/modprobe.d/blacklist.conf. Then re-run the above commands
and the reinstall of wl will put all the bcma stuff in the blacklist file under
bcm43xx.....its magic

---

### Post by adamr on 2013-01-12
No difference.

It re-installed the driver by the looks ok it, but it's still using bcma-pci-bridge, despite showing bcma and wl as the kernel modules when I lspci -vv

 :(

---

### Post by Hadaka on 2013-01-12
Hi, if you havent already done so, please remove the 2
bcma items in the /etc/modprobe.d/blacklist.conf file
then..

```
 [FONT=Courier New]rmmod bcma [/FONT]
```

and re-run this also please.
```
sudo apt-get install --reinstall bcmwl-kernel-source 
```

---

### Post by adamr on 2013-01-12
I can't rmmod bcma:

```
adam@adam-Lenovo-G580 ~ $ sudo rmmod bcma
ERROR: Module bcma is in use by brcmsmac

```

---

### Post by Hadaka on 2013-01-12
Hi, fun stuff huh?
ok lets see just what modules you are loading at boot...

```
lsmod 
```

thanks

---

### Post by adamr on 2013-01-12
```
Module                  Size  Used by
michael_mic            12612  4 
arc4                   12529  2 
parport_pc             32688  0 
bnep                   18140  2 
ppdev                  17073  0 
rfcomm                 46619  12 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
joydev                 17457  0 
coretemp               13400  0 
kvm                   414070  0 
ghash_clmulni_intel    13180  0 
cryptd                 20403  1 ghash_clmulni_intel
brcmsmac              531848  0 
mac80211              539908  1 brcmsmac
alx                    81256  0 
lib80211_crypt_tkip    17379  0 
microcode              22803  0 
ideapad_laptop         18086  0 
sparse_keymap          13890  1 ideapad_laptop
btusb                  18334  0 
bluetooth             209199  22 bnep,rfcomm,btusb
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
wmi                    19070  0 
bcma                   35656  1 brcmsmac
brcmutil               14755  1 brcmsmac
snd_seq_midi           13324  0 
cfg80211              206566  2 brcmsmac,mac80211
cordic                 12535  1 brcmsmac
mac_hid                13205  0 
snd_rawmidi            30512  1 snd_seq_midi
psmouse                95552  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2573568  0 
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13215  0 
lpc_ich                17061  0 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
i915                  520519  4 
lib80211               14381  2 lib80211_crypt_tkip,wl
mei                    40690  0 
drm_kms_helper         46784  1 i915
drm                   275528  5 i915,drm_kms_helper
lp                     17759  0 
i2c_algo_bit           13413  1 i915
video                  19335  1 i915
parport                46345  3 parport_pc,ppdev,lp
uas                    17844  0 
usb_storage            48838  0 

```

---

### Post by chili555 on 2013-01-12
> Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]]This device is claimed by two conflicting drivers: wl and brcmsmac. One of the dependencies of brcmsmac is bcma. How and why it gets named bcma-pci-bridge, I have no idea.

The answer is to blacklist *BOTH* bcma and brcmsmac. You already have bcma blacklisted so let's do:```
sudo su
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and give us your report.

bcma probably loaded even though it was blacklisted because brcmsmac was not blacklisted, loaded and took its happy family mac80211, bcma, brcmutil, cfg80211 and cordic along with it.

If you wanted to be super sanitary, you could remove this incorrect line:```
blacklist bcma-pci-bridge
```There is no driver named bcma-pci-bridge; confirm:```
chili@Think410:~$ modinfo bcma-pci-bridge
ERROR: modinfo: could not find module bcma-pci-bridge
```There ya go, everything you ever wanted to know about bcma in 2,000 words or less!

---

### Post by adamr on 2013-01-13
Thanks for the help, but guess what...

despite now having blacklisted both brcmsmac and bcma in blacklist.conf, I just rebooted and *still* it's loaded bcma-pci-bridge instead of wl.

Any more ideas?

---

### Post by chili555 on 2013-01-13
Let's see it, just because I am curious, suspicious and love to learn:```
cat /etc/modprobe.d/blacklist.conf
cat /etc/modules
cat /etc/rc.local
ls /etc/modprobe.d
```Thanks.

---

### Post by adamr on 2013-01-13
blacklist.conf:
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
blacklist brcmsmac
blacklist bcma
```

modules:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
brcmsmac
wl
```

rc.local:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```

ls modprobe.d:
```
alsa-base.conf
blacklist
blacklist-ath_pci.conf
blacklist-bcm43.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-rare-network.conf
blacklist-watchdog.conf
broadcom-sta-common.conf
dkms.conf
iwlwifi.conf
vmwgfx-fbdev.conf
```

I'm no expert (clearly), but is it just because I have brcmsmac in modules? Does that file override blacklist.conf?

---

### Post by chili555 on 2013-01-13
> **adamr said:**
> 

I'm no expert (clearly), but is it just because I have brcmsmac in modules? Does that file override blacklist.conf?Exactly. You want to amend it and reboot?

---

### Post by adamr on 2013-01-13
So far so good, thanks for the help. I'll have to remember as I go along that modules overrides the blacklist. Seems a bit odd, but I'm sure there's a good reason for it that I just don't understand yet :)

---

### Post by chili555 on 2013-01-13
I'm sure it's just the order these files are processed in during boot. It's an obvious conflict between 'these are the modules we definitely want to load' and 'these are never to load.' I am confident you are all set now.

---

