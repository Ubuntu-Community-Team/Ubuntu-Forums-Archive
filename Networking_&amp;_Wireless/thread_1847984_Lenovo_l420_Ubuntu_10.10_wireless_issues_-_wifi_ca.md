---
title: "Lenovo l420 Ubuntu 10.10 wireless issues - wifi card not active/can't activate"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by samamclean on 2011-09-21
Hi, I just did a fresh install of 10.10 (since 11.04 doesn't work on my laptop) but the wireless doesn't work.

I've read a lot of posts, and nobody seems to have my situation .. but I'll post all the information from the types of searches I've done.

when I run nm-tool it looks fine - but wlan0 is not present when I run ifconfig. when i run iwconfig, wlan0 shows up
when I run lsmod, I' not sure if I have too many drivers ..rtl8192ce, rtl8192c_common, and rtlwifi all show up as well as compat, (which was the first solution I tried)

when I do rfkill list. it says 
0: phy0: wireless LAN
 softblocked: no
hard blocked: no

I have no idea what's going on - the phsycial switch on my l420 is on, I've not touched it. The computer obviously sees the wifi card, it just doesn't.. do something I don't know.

Any suggestions?

---

### Post by wildmanne39 on 2011-09-21
Hi, please post the results of these commands:
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by samamclean on 2011-09-21
for the lspci, it says the name of the driver - then kernel driver in use rtl8192ce for physical addres 03:00.0 which is where the device is found by other tools, then it gives the ethernet driver as well

for wiconfig - output is normal.

wlan0 IEEE 802.11bgn ESSID:off/any
 mode: managed access point: not-associated tx-power= 0 dBm etc etc

for lsmod

rtl8192ce  68218 0
rtl8192c_common 6176 1 rtl8192ce
rtlwifi 86811 1 rtl81892ce

does this help at all?

---

### Post by samamclean on 2011-09-21
```
for iwconfig [CODE]  wlan0 IEEE 802.11bgn ESSID:off/any
 mode: managed access point: not-associated tx-power= 0 dBm etc etc
```

for lsmod

```
rtl8192ce  68218 0
rtl8192c_common 6176 1 rtl8192ce
rtlwifi 86811 1 rtl81892ce
```

---

### Post by wildmanne39 on 2011-09-21
Hi, I just noticed you are new, welcome to the forum! Thank you for the information. I need you to post all the output from those commands here please, it all is important so I do not miss something, and I may need you to rum more commands.

If you need to you can paste the information to a flash drive to put on a computer with internet access then paste it here.
Thank you

---

### Post by samamclean on 2011-09-21
here we go
lspci ```

00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b4)
00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)


```

for wiconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on

```

for lsmod

```

Module                  Size  Used by
nls_iso8859_1           4657  1 
nls_cp437               6375  1 
vfat                   10954  1 
fat                    56244  1 vfat
arc4                    1497  2 
rtl8192ce              68218  0 
rtl8192c_common        61976  1 rtl8192ce
rtlwifi                86811  1 rtl8192ce
mac80211              290957  2 rtl8192ce,rtlwifi
cfg80211              174996  2 rtlwifi,mac80211
compat                  8707  2 mac80211,cfg80211
cryptd                  8140  0 
aes_x86_64              7936  438 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7984  1 
joydev                 11395  0 
parport_pc             30086  0 
ppdev                   6804  0 
dm_crypt               13381  0 
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_realtek   300109  1 
uvcvideo               62411  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
snd_hda_intel          26147  2 
snd_hda_codec         100919  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
psmouse                62080  0 
serio_raw               4910  0 
thinkpad_acpi          78535  0 
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64277  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
led_class               3393  2 compat,thinkpad_acpi
nvram                   7990  1 thinkpad_acpi
tpm_tis                10022  0 
tpm                    16019  1 tpm_tis
tpm_bios                6426  1 tpm
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usb_storage            50788  2 
i915                  335073  3 
drm_kms_helper         32836  1 i915
drm                   206198  3 i915,drm_kms_helper
ahci                   22370  2 
libahci                26148  1 ahci
r8169                  42286  0 
mii                     5261  1 r8169
i2c_algo_bit            6208  1 i915
video                  22176  1 i915
intel_agp              32334  2 i915
output                  2527  1 video

```

just in some additional information - if I go through the normal gui to activate/deactivate wireless - if I deactivate, and then reactivate, it says device not ready. I have to reboot for the device to be recognized.

---

### Post by samamclean on 2011-09-21
also, ifconfig doesn't have any entry for wlan0

---

### Post by wildmanne39 on 2011-09-21
Hi, let's try this please: Unplug your wired connection then run these commands.
```
sudo su
echo "blacklist compat" >> /etc/modprobe.d/blacklist.conf
exit
```
```
sudo modprobe rtl8192ce
```
Thank you

---

### Post by samamclean on 2011-09-21
I followed those commands.. rebooted, no effect. Would you like me to post output form something else?

---

### Post by wildmanne39 on 2011-09-21
Hi, I do not think it will work yet but I want to make sure the second command run again please and do not reboot, but unplug your wired connection first.

What concerns me also is that your router is not showing any power out put, do you have the power in the router set to maximum?

Is wireless enabled in your router?
Thank you

---

### Post by samamclean on 2011-09-21
my laptop isn't tapped into a router with a wire, it's just sitting on the desk next to me. Do you want me to turn off networking first before I run modprobe?

---

### Post by wildmanne39 on 2011-09-21
Hi, no I do not, do you know if your router is able to be connected to with a wireless device for sure, as I asked in the last post about the power?
Thank you

---

### Post by samamclean on 2011-09-21
the router is definitely a wireless router. 

However, from what I can see the wireless isn't even looking for a signal- it's disabled (so says lshw -C network.

however the physical switch is enabled.

---

### Post by samamclean on 2011-09-21
```
lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 38:59:f9:e2:1a:5d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=2.6.35-30-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: e8:9a:8f:b8:11:d9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:46 ioport:4000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff

```

```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by wildmanne39 on 2011-09-21
Hi, have your ever connected a cable to the router from a computer and set the wireless up and turn the wireless on?

Please post the results of these commands:
```
cat /etc/lsb-release; uname -a
```
```
nm-tool
```
```
iwconfig
```
```
sudo iwlist scan
```
```
iwlist chan
```
```
dmesg | egrep 'rtl|firm|radio|switch|wlan0'
```
```
lsmod | grep rtl
```
```
cat /etc/modprobe.d/blacklist.conf
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by samamclean on 2011-09-21
Here we go:

```
cat /etc/lsb-release; uname -a 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux Leopard 2.6.35-30-generic #59-Ubuntu SMP Tue Aug 30 19:00:03 UTC 2011 x86_64 GNU/Linux
State: disconnected
```

```
nm-tool
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             disconnected
  Default:           no
  HW Address:        38:59:F9:E2:1A:5D

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E8:9A:8F:B8:11:D9

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off
```

```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

```
iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
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
```

```
dmesg | egrep 'rtl|firm|radio|switch|wlan0'
[    2.609513] Console: switching to colour frame buffer device 170x48
[   12.679650] thinkpad_acpi: radio switch found; radios are enabled
[   12.679697] thinkpad_acpi: possible tablet mode switch found; ThinkPad in laptop mode
[   12.682071] thinkpad_acpi: asked for hotkey mask 0x078dffff, but firmware forced it to 0x008dffff
[   13.596695] rtl8192ce 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.596704] rtl8192ce 0000:03:00.0: setting latency timer to 64
[   13.717395] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.717875] rtlwifi: wireless switch is off
[   13.758829] rtl8192cu: Loading firmware file rtlwifi/rtl8192cfw.bin
[   13.868824] rtl8192cu: Firmware loading failed
[   14.064086] rtl8192cu: Loading firmware file rtlwifi/rtl8192cfw.bin
[   14.065278] rtl8192cu: Firmware loading failed
[   20.061735] IBM TrackPoint firmware: 0x0e, buttons: 3/3
```

```

lsmod | grep rtl
rtl8192ce              68218  0 
rtl8192c_common        61976  1 rtl8192ce
rtlwifi                86811  1 rtl8192ce
mac80211              290957  2 rtl8192ce,rtlwifi
cfg80211              174996  2 rtlwifi,mac80211
```

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
blacklist compat
```

you also asked for iwconfig - I posted the results for that on a previous post. Hope these help

---

### Post by wildmanne39 on 2011-09-21
Hi, I am researching the issue it says you  have a radio switch off, I am looking into that.

I think we need to unblacklist the compat we blacklisted earlier, I need not realize that the driver did not come with 10.10, because it comes with 11.04, my mistake.

Do this please:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```

then delete this
```
compat
```
save the file.
Then restart your computer and if it does not come on look for a switch or button like fn f11 that turns it on.
Thank you

---

### Post by samamclean on 2011-09-21
I changed the blacklist .. but F5 is supposed to turn the radio on/off.. I turned it off, and then on again, and it says device not ready. i can't get the device to be recognized again.

---

### Post by wildmanne39 on 2011-09-21
Hi, please try this.
```
rfkill unblock wifi
```
```
sudo ifconfig wlan0 down
```
```
sudo ifconfig wlan0 up
```
the run these commands again.
```
sudo iwlist scan
```
```
dmesg | egrep 'rtl|firm|radio|switch|wlan0'
```
```
lsmod | grep rtl
```
Thank you

---

### Post by samamclean on 2011-09-21
reply to iwlist scan:

```
interface doesn't support scanning : network is down
```

reply to dmesg:

for ever instance - it's similar to the last dmesg. Simply put - firmware failures, all the way around.

reply to lsmod
```


rtl8192ce                                             68218    0
rtl8192c_common                                 61976    1 rtl8192ce
rtlwifi                                                   86811    1 rtl8192ce
mac80211                                            290957   2 rtl8192c3, rtlwifi
cfg80211                                              174886   2 rtlwifi, mac80211

```

if I understand this correctly, the firmware failures mean that the wifi card can't be interacted with / turned on. Is this your evaluation?

---

### Post by wildmanne39 on 2011-09-21
Yes, that is correct.

```
lsmod | grep rtl
```
that did not show the compat?

Please show all of:
```
lsmod
```
and give me a link to where you installed your driver from please:
Thank you

---

### Post by samamclean on 2011-09-21
reading over this again - it seems that... rtlwifi/rtl8192cfw.bin is the file that is failing over and over again.  However, rtlwifi, wireless switch is off comes first as an issue.

So, is the firmware failing to load because the wireless switch is off? and how do I turn the wireless switch on? because neither the fn key nor the physical switch on the side changes anything it seems.

---

### Post by samamclean on 2011-09-21
I have to say - would it be possible to upgrade the kernel to solve this issue without upgrading to 11.04? because 11.04 doesn't work with my display at all.

---

### Post by wildmanne39 on 2011-09-21
Hi, that is why I meed the link to where you installed the driver from to see what it says about the firmware, and I am not sure upgrading the kernel would work because it might still mess up your display

I am going to have to give off for a little while my blood sugar is very low and I need to get it up before I continue.
Thank you

---

### Post by samamclean on 2011-09-21
I had found a solution that suggested upgrading the kernel.. so I did
now it's 2.6.37. Now I no longer have the realtek driver that I had before - my system doesn't even see the wireless card. However, my display is fine.

---

### Post by samamclean on 2011-09-21
[http://ubuntuforums.org/showthread.php?t=1806263](http://ubuntuforums.org/showthread.php?t=1806263) this is where I got the idea for the firmware that I downloaded, as well as the kernel upgrade. I upgraded to the 2.6.37 and now I can't see the wireless card at all. 

I'm thinking about just scrubbing the install and starting without the compat stuff. Maybe I should start from there.

---

### Post by wildmanne39 on 2011-09-21
Hi, post the results of this please:
```
modinfo rtl8192ce

```
Thank you

---

### Post by samamclean on 2011-09-21
```

filename:       /lib/modules/2.6.37-020637-generic/updates/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D00D59F71E90DD9202E7716
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8192c-common,mac80211
vermagic:       2.6.37-020637-generic SMP mod_unload modversions 
parm:           swenc:using hardware crypto (default 0 [hardware])

```

---

### Post by wildmanne39 on 2011-09-21
Hi, alright that is good the driver is there, know we probably need to get rid of the one from compat.

let's look at 
```
lsmod
```
```
cat /etc/modprobe.d/blacklist.conf
```
```
dmesg | egrep 'rtl|firm|radio|switch|wlan0'
```
please post the complete output of each command.
Thank you

---

### Post by samamclean on 2011-09-21
I don't think compat is the issue. After I upgraded the kernel, it could not see the wireless card. THen I did compat, and suddently my system could see the wireless card but we were in the same spot as before. I think getting rid of compat will mean the system can't see the card again.

---

### Post by samamclean on 2011-09-21
I think it's clear that the problem is that the wireless switch is "off". However, if I use fn +f5 or the switch on the side of the laptop to off, there is a clear change that lasts until I reboot my laptop.

I think compat would work just fine, if I can turn on the switch. The question is how do I do that?

---

### Post by wildmanne39 on 2011-09-21
Hi, I was hoping to find out if that kernel supported the driver, I believe you have to upgrade to 2.6.38-11 for it to be included in the kernel which means if it is in the kernel you do not need compat and having both would cause a conflict but since you have already installed compat again it defeats the purpose of upgrading the kernel.

I need to read through the thread again and see what has already been done.
Thank you

---

### Post by wildmanne39 on 2011-09-21
Hi, what do you mean by change until you reboot? does your wireless light come on? does it connect?
thank you

---

### Post by wildmanne39 on 2011-09-21
Hi, this
> pci:v000010ECd00008176sv*sd*bc*sc*i* 
means that the driver is in the kernel you have installed so compat needs to be uninstalled.

Then post the commands I ask for right after I found out you upgraded your kernel.
Thank you

---

### Post by samamclean on 2011-09-23
So I upgraded to the .28 kernel - the one for Natty. It didn't screw up my display, which is nice. I also got rid of the Compat driver. 

You were right - the driver is in the kernel because the wireless card is noticed when the laptop boots. However - the issues always comes back to "the wireless switch is off". 

I think this is a fundamental issue, and I'm concerned it might be a hardward issue. I never actually booted into windows so ...

---

### Post by samamclean on 2011-09-23
here's why I think the wireless switch issue i the key one 

```
[   16.710723] thinkpad_acpi: radio switch found; radios are enabled
[   16.710734] thinkpad_acpi: possible tablet mode switch found; ThinkPad in laptop mode
[   16.711946] thinkpad_acpi: asked for hotkey mask 0x078dffff, but firmware forced it to 0x008dffff
[   16.870750] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   16.871500] rtlwifi: wireless switch is off
[   16.888273] rtl8192ce:rtl92c_download_fw():<0-0> Failed to request firmware!
[   16.954077] rtl8192ce:rtl92c_download_fw():<0-0> Failed to request firmware!
[   23.524086] IBM TrackPoint firmware: 0x0e, buttons: 3/3

```

and 
```

lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 38:59:f9:e2:1a:5d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=2.6.38-020638-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0500000-f0503fff


```

---

### Post by wildmanne39 on 2011-09-23
Hi, I am sorry it has taken my so long to reply today I been away from my computer most of the day, then I have spent quite a bit of time researching your issue.

Before we go further I suspect the firmware did not get installed correctly, I am not forgetting about the switch, but let's to this simple command.
```
sudo apt-get install --reinstall linux-firmware
```
Then unplug your wired connection and restart your computer.
Thank you

---

### Post by samamclean on 2011-09-23
I removed an reinstall linux-firmware.. no noticeable affects at all. :S

---

### Post by wildmanne39 on 2011-09-23
Hi, with all the kernel upgrades and other things that have been tried we need to go back to the beginning and start with some commands we all ready tried, one thing I will be looking at is to see if you have any blocks due to the switch.

Please post all the information here the littlest thing can be important.
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
```
dmesg | egrep 'rtl|firm'
```
```
modinfo rtl8192ce
```
```
nm-tool
```
Thank you

---

### Post by samamclean on 2011-09-23
Because it's so much copying and pasting - and you've seen all of these results before - I'm going to summarize

rfkill list provides the same response as before. 
lsmod - only two entries now - rtlwifi and rtl8192ce

lspci shows the driver as rtl8192ce, 
scan doesn't work - the card is disconnected

nm-tool says the same driver, and that the wireless card is disconnected. 

So clearly - the driver is in the kernel and those driver issues seem to be somewhat rectified.

Is there a command I can type in that will turn on my wireless card?

---

### Post by samamclean on 2011-09-23
I know that the littlest details are important - but honestly, the results are largely the same Especially for nm-tool, iw-scan, iwconfig, ifconfig. lsmod is simpler, but I told you about that above. 

I think we need to focus on the issue of the wireless card just not being turned on when the machine boots, and how that can be done.

---

### Post by wildmanne39 on 2011-09-23
Hi, I researched this quite a bit this afternoon, and here is a link that may help.
[http://ubuntuforums.org/showthread.php?t=1770202&page=5](http://ubuntuforums.org/showthread.php?t=1770202&page=5)

I am sorry I can not help any further without the information I asked for, even from the beginning you edited out information that maybe important.
Thank you

---

### Post by samamclean on 2011-09-23
I understand - I think we're going in circles here - thanks for the link - hopefully it will help.

---

### Post by wildmanne39 on 2011-09-23
Hi, your welcome! I have been working with networking issue for about 3 months and I just have to see all the information to help someone, if you would like I will private message the person in the link I gave you and ask him to come here and help you, so he can see everything that has been done.

He is the expert and is the best person to help you.
Thank you

---

### Post by samamclean on 2011-09-23
I posted on the forum.. but if you could shoot him a PM it would be awesome. I read through the forum, and nothing the have posted there works, unfortunately.

---

### Post by wildmanne39 on 2011-09-23
Hi, I will do that, it is late where he lives but he is usually on early in them mornings, so I am sure it will be in the morning before he is on.

I will ask him to come here that way he knows what has already been done.
Thank you

---

### Post by samamclean on 2011-09-24
On an interesting note, I brought up two terminals so I could watch syslog while I try to raise the wirless .. when I use fn + f5, it says bring up device - then that the driver rtl18192ce:rtl92c_download_fw():<0 - 0> failed to request firmware.  

The same thing happens when I try to reactivate the wireless card with the physical switch.

I hope this helps in some way?

---

### Post by wildmanne39 on 2011-09-24
Hi, that was also in the error message that is why I gave you that link, read starting with post 46 and I will go read it again also.
Thank you

---

### Post by wildmanne39 on 2011-09-24
Hi, the other thread does not look promising, but it looks like people have it working good in 10.10 possibly.

You do not have the acer-wmi, I looked at that very first thing with rfkill list all that is why I do not believe it is the switch.

Hopefully chiili555, can help sort it out in the morning, you may have to revert back to the 10.10 kernel which you can try by loading 10.10 kernel at the boot menu then you can run these commands and see if it works with the older kernel, but make sure you do not have any other drivers installed first.
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```
Thank you

---

### Post by samamclean on 2011-09-24
when I run  - I get nothing at all. And yes, I've already removed and re-installed linux-firmware. Where can I get the firmware, and would that solve the issue of the driver not asking for the firmware?
ls -al /lib/firmware/rtlwifi

---

### Post by chili555 on 2011-09-24
Firmware is clearly the issue here: > [   13.758829] rtl8192cu: Loading firmware file rtlwifi/rtl8192cfw.bin
[   13.868824] rtl8192cu: Firmware loading failed
[   14.064086] rtl8192cu: Loading firmware file rtlwifi/rtl8192cfw.bin
[   14.065278] rtl8192cu: Firmware loading failedAnd then after you installed compat-wireless:> [   16.888273] rtl8192ce:rtl92c_download_fw():<0-0> Failed to request firmware!
[   16.954077] rtl8192ce:rtl92c_download_fw():<0-0> Failed to request firmware!I don't know for sure if "Failed to request firmware" actually means, it doesn't exist where it's supposed to exist or if there is some underlying problem with the driver. Let's check. According to modinfo, it looks for a specific firmware file in a specific place:```
filename:       /lib/modules/2.6.37-020637-generic/updates/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
[COLOR="Red"]firmware:       rtlwifi/rtl8192cfw.bin[/COLOR]
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
<snip>
```So let's see if you have the firmware in the right place:```
ls /lib/firmware/rtlwifi
ls /lib/firmware/`uname -r`/rtlwifi
```Those backticks are on the left side of my US keyboard on the same key with ~. If you find, as I suspect:> ls: cannot access /lib/firmware/rtlwifi: No such file or directoryThen we'll see if it is elsewhere on your system:```
sudo updatedb
locate rtl8192cfw
```Once we find it, we'll move it. updatedb will take a few moments; please be patient.

---

### Post by samamclean on 2011-09-24
so for rfkill list all

```

0: phy0: Wirless LAN
soft blocked: no
hard blocked: no
```

yet, the wireless card is "disabled" according to half the tools I have.

for lspci -nn | grep 0280

[CODE]
03:00.0 network controller [0280]: Realtek Semiconductor Co. Ltd. Device [10ec:8176] (rev 01)
[\CODE]

also a few other things

for modinfo - it says that the firmware i have is rtlwifi/rtl8192cfw.bin.. mot /var/lib/rtlwifi - so it seems that firmware is there.

---

### Post by chili555 on 2011-09-24
> for modinfo - it says that the firmware i have is rtlwifi/rtl8192cfw.bin.. mot /var/lib/rtlwifi - so it seems that firmware is there.Modinfo is telling you that it requires firmware and where it's going to look for it. Modinfo does *not* tell you if you actually have it. Please check as I suggested.

---

### Post by samamclean on 2011-09-24
In that case, I'm missing the firmware because it's not there when I checked as yhou suggested. installing linux-firmware does nothing.. so where can I find it?

---

### Post by samamclean on 2011-09-24
locate rtl8192cfw came up empty. Which is good news, I think?

---

### Post by chili555 on 2011-09-24
Here is a file called rtlwifi.zip. Download it to your desktop. Right click it and select 'Extract Here.' Now open a terminal and do:```
sudo mkdir /lib/firmware/rtlwifi
sudo cp Desktop/rtlwifi/* /lib/firmware/rtlwifi
```Now reboot and tell me if your wireless is working. 

If not, please post:```
dmesg | grep 8192
ls -al /lib/firmware/rtlwifi
```Thanks and good luck.

---

### Post by samamclean on 2011-09-24
It worked beautifully! absolutely beautifully, at least so far :D

---

### Post by wildmanne39 on 2011-09-24
Hi, I am glad it is working, would you please mark the thread as solved by using thread tools at the top of the page.

Thank you chili555 I appreciate the help greatly.

---

### Post by moneeshk on 2011-10-03
Hi,

I am also using lenove l420 and but wireless on the ubuntu 10.10 is not working please help.
Output of the comands 

[COLOR=#000000][FONT=Times New Roman][FONT=arial]lspci -nnk | grep -iA2 net

[/FONT][/FONT][/COLOR]```

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
--
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Lenovo Device [17aa:21dd]
    Kernel driver in use: r8169

```second command: iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.


```third command: lsmod
```

Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
rfcomm                 33843  4 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
joydev                  8767  0 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_realtek   218460  1 
i915                  295819  3 
drm_kms_helper         30136  1 i915
drm                   168092  3 i915,drm_kms_helper
snd_hda_intel          22235  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
uvcvideo               55911  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
btusb                  11001  2 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
intel_agp              26566  2 i915
i2c_algo_bit            5168  1 i915
psmouse                59033  0 
serio_raw               4022  0 
agpgart                32011  2 drm,intel_agp
thinkpad_acpi          67627  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49102  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
led_class               2633  1 thinkpad_acpi
nvram                   6342  1 thinkpad_acpi
tpm_tis                 7658  0 
tpm                    13803  1 tpm_tis
tpm_bios                5310  1 tpm
video                  18712  1 i915
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19326  2 
r8169                  36553  0 
mii                     4425  1 r8169
libahci                21728  1 ahci


```

---

### Post by wildmanne39 on 2011-10-03
Hi, try what is in post 49, you will need to have a wired internet connection and make sure you install all updates first and restart your computer then follow the directions in post 49.
Thank you

---

