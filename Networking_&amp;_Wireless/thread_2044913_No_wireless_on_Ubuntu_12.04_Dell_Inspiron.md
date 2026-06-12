---
title: "No wireless on Ubuntu 12.04 Dell Inspiron"
date: 2012-08-20
forum: Networking &amp; Wireless
---

### Post by Saurabh2816 on 2012-08-20
I have recently installed Ubuntu 12.04(dual-boot)and I'm not able to connect to internet using Wifi since. Wifi works fine on Windows 7. I have watched a couple of videos on youtube about connecting to the wifi but no help.
I'm doing exaclty as told in this video and nothing else [http://www.youtube.com/watch?v=XN8PrEbmct8](http://www.youtube.com/watch?v=XN8PrEbmct8).

My wifi is WEP 64Bit. (I know it's very insecure but still) 
DELL Inspiron 15R 5520

I read some of the other posts also but no help since last night.
I'm a noob so please help. Really looking forward for some reply.

---

### Post by chili555 on 2012-08-20
We need more information. Please get a wired ethernet connection and open a terminal and copy and paste:```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```A file will be created in your user directory called netinfo.txt. All MAC addresses and encryption keys are obscured. Please copy the text into your reply so we can accurately diagnose the issue and decide the next steps.

---

### Post by Saurabh2816 on 2012-08-20
saurabh@ubuntu:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
[SIZE=2]**Here is the output**[/SIZE]

--2012-08-20 20:46:54--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 23.21.195.136, 23.21.220.40, 23.23.134.47, ...
Connecting to dl.dropbox.com (dl.dropbox.com)|23.21.195.136|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1453 (1.4K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2012-08-20 20:46:55--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Reusing existing connection to dl.dropbox.com:80.
HTTP request sent, awaiting response... 200 OK

[]("http://imageshack.us/photo/my-images/15/saurabh.png/")Length: 1453 (1.4K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 1,453       --.-K/s   in 0s      

2012-08-20 20:46:56 (88.7 MB/s) - `wireless_script' saved [1453/1453]

[sudo] password for saurabh:

Image for reference
[http://imageshack.us/photo/my-images/15/saurabh.png/](http://imageshack.us/photo/my-images/15/saurabh.png/)

---

### Post by Saurabh2816 on 2012-08-20
**NETINFO.TXT FILE CONTAINS THIS**

*************** info trace ****************



**** uname -a ****


Linux ubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"


**** lspci ****


07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:056a]
    Kernel driver in use: r8169
--
08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
    Subsystem: Dell Device [1028:0016]


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0461:4dfa Primax Electronics, Ltd 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0c45:648d Microdia 
Bus 002 Device 003: ID 0a5c:21d7 Broadcom Corp. 


**** iwconfig ****




**** rfkill ****


0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_conexant    62128  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  468651  3 
snd_seq_midi           13324  0 
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
rts5139               351143  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87603  0 
serio_raw              13211  0 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
v4l2_compat_ioctl32    17128  1 videodev
radeon                804372  0 
joydev                 17693  0 
mei                    41616  0 
ttm                    76949  1 radeon
drm_kms_helper         46978  2 i915,radeon
drm                   242038  6 i915,radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  2 i915,radeon
wmi                    19256  1 dell_wmi
mac_hid                13253  0 
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****



[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false


**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1


**** blacklist.conf ****


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


**** dmesg ****


[   14.129344] wmi: Mapper loaded
[   89.823110] type=1400 audit(1345475501.680:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2161 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0


**************** done ********************

---

### Post by Saurabh2816 on 2012-08-22
What should I do now ?
Wireless still not working.

---

### Post by kevjonesin on 2012-12-22
I found the site below helpful in sorting out a WiFi issue. 

Ubuntu 12.04 was failing to connect to a SMC802W v.2 PCI WiFicard. I believe it was lacking the p54pci driver as this is what Precise Puppy 5.4.3 was using to connect via the same card on the same computer. Anyway, it may be relevant to others as well.

The site is in German but translated clearly to English via Google Translate. Here's the link to the translation:

[http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&eotf=1&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FWLAN%2FLinux-backports-modules&act=url](http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&eotf=1&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FWLAN%2FLinux-backports-modules&act=url)

And here's the direct link to the original (German) site:

[http://wiki.ubuntuusers.de/WLAN/Linux-backports-modules](http://wiki.ubuntuusers.de/WLAN/Linux-backports-modules)


p.s. I know I'm 'blowing the dust' off of this thread and that Saurabh2816 has likely gone on to other options, but the page I've linked to was so much more straight forward than others I've been coming across. I figure it's easy enough to try installing their few recommended packages and then if that doesn't work go on to trouble shooting more technical solutions.

---

### Post by Saurabh2816 on 2013-01-04
> **kevjonesin said:**
> I found the site below helpful in sorting out a WiFi issue. 

Ubuntu 12.04 was failing to connect to a SMC802W v.2 PCI WiFicard. I believe it was lacking the p54pci driver as this is what Precise Puppy 5.4.3 was using to connect via the same card on the same computer. Anyway, it may be relevant to others as well.

The site is in German but translated clearly to English via Google Translate. Here's the link to the translation:

[http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&eotf=1&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FWLAN%2FLinux-backports-modules&act=url](http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&eotf=1&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FWLAN%2FLinux-backports-modules&act=url)

And here's the direct link to the original (German) site:

[http://wiki.ubuntuusers.de/WLAN/Linux-backports-modules](http://wiki.ubuntuusers.de/WLAN/Linux-backports-modules)


p.s. I know I'm 'blowing the dust' off of this thread and that Saurabh2816 has likely gone on to other options, but the page I've linked to was so much more straight forward than others I've been coming across. I figure it's easy enough to try installing their few recommended packages and then if that doesn't work go on to trouble shooting more technical solutions.

Hey man thanks for you reply :P. BTW I have now moved on to VirtualBox after that and its much better when you can access both the OS side by side rather than explicitly switching to it,so everything is working fine now.

PS:I have looked into the website and I think it might be useful for future use. :D

---

