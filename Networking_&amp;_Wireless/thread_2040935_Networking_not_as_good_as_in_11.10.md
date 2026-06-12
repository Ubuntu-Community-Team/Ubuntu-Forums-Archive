---
title: "Networking not as good as in 11.10"
date: 2012-08-11
forum: Networking &amp; Wireless
---

### Post by peterlauri on 2012-08-11
Hello,

I was using 11.10 before and all networking with vpnc over the Network Manager and wifi using Network Manager was working properly. When connecting to vpnc or wireless DNS and rounting was handled properly. Now on 12.04 (fresh install) the DNS is not populated as it should, and therefor I cannot connect to the services I need.

Same with SOME wireless networks. My hotspot on my phone works, work wireless works. But my home wireless just don't want to work.

It feels like this has to do with resolvconf changes, but I cannot figure out where to start to look. Is there any fix to get back the "old" behavior of 11.10 back to the 12.04 so I don't need to do manual hacks for each time I connect over VPN.

/Peter

PS! The strange thing with the wireless is that the gateway (.1) address is not reachable when over wireless, but when over ethernet. All other devices connected (phone, tab, etc) connects properly to the same network. And if I use Fedora Live CD it also works. And using Ubuntu 11.10 Live CD.

---

### Post by praseodym on 2012-08-11
Hi,

which hardware is in use? Please show

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
```
"resolvconf" can easily be uninstalled:
```

sudo apt-get remove --purge resolvconf
sudo /etc/init.d/networking restart
```

---

### Post by peterlauri on 2012-08-11
I doubt that is is hardware related, as some wireless networks works, and others not. Must have something with how resolving works in new Network Manager, and how routes etc are setup :) But I'm a novice, so no clue...

Here is the output you asked for:

##########################################
############### lspci -nnk | grep -iA2 net
##########################################

```
01:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [8086:0091] (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6230 AGN [8086:5201]
	Kernel driver in use: iwlwifi
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c098]
	Kernel driver in use: r8169


###############
######### lsusb
###############

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 2232:1009  
Bus 002 Device 003: ID 8086:0189 Intel Corp. 
Bus 003 Device 003: ID 05ac:1402 Apple, Inc. 
Bus 003 Device 004: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 003 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 059f:0323 LaCie, Ltd LaCie d2 Drive USB2
Bus 003 Device 006: ID 0411:01d9 BUFFALO INC. (formerly MelCo., Inc.) 

################
###########lsmod
################

Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
vboxdrv               287130  4 vboxpci,vboxnetadp,vboxnetflt
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
nls_utf8               12557  1 
udf                    94441  1 
crc_itu_t              12707  1 udf
usb_storage            49198  3 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224066  1 
tpm_infineon           17536  0 
arc4                   12529  2 
bnep                   18281  2 
uvcvideo               72627  0 
asix                   26919  0 
rfcomm                 47604  12 
videodev               98259  1 uvcvideo
usbnet                 26212  1 asix
btusb                  18288  2 
snd_hda_intel          33773  3 
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
bluetooth             180104  23 bnep,rfcomm,btusb
joydev                 17693  0 
snd_hwdep              13668  1 snd_hda_codec
hid_logitech_dj        18594  0 
parport_pc             32866  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ppdev                  17113  0 
samsung_laptop         13709  0 
snd_seq_midi           13324  0 
iwlwifi               332525  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              506816  1 iwlwifi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
tpm_tis                18804  0 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87692  0 
cfg80211              205544  2 iwlwifi,mac80211
serio_raw              13211  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
mac_hid                13253  0 
ext2                   73795  1 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_crypt               23125  1 
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid
i915                  472941  4 
drm_kms_helper         46978  1 i915
r8169                  62099  0 
drm                   242038  5 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
wmi                    19256  0 
video                  19596  1 i915
```

---

### Post by praseodym on 2012-08-11
Deactivate the N-mode of the wifi driver, additionally (bug):
> 
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

---

### Post by peterlauri on 2012-08-12
You write to disable N mode, and additionally perform the command you wrote. But I assume you mean that the command is how you disable the N mode?

---

### Post by praseodym on 2012-08-12
Right, additionally remove "resolvconf"

---

### Post by peterlauri on 2012-08-12
If I remove the resolvconf package, does that mean I have no automatic dns resolution? Or does it mean it will have same behavior as 11.10?

---

### Post by praseodym on 2012-08-12
It will be the same as in 11.10. "resolvconf" was not default in 11.10, but it is in 12.04.

---

### Post by peterlauri on 2012-08-12
Is there any plans to fix these issues with resolveconf in the near
feature? I have been following some bugs, but I don't know when they are scheduled to be fixed. There are activity in them, but no clear vision if this will be fixed. Meanwhile I guess I will remove
resolvconf... Will Network Manager work as normally then?

---

### Post by praseodym on 2012-08-12
Yes, it will.

---

### Post by peterlauri on 2012-08-12
> **praseodym said:**
> Deactivate the N-mode of the wifi driver, additionally (bug):

This worked like a charm, no need to remove the resolvconf.

---

### Post by peterlauri on 2012-08-12
No my last problem before I have a fully working networking is my VPNC connection with defined routes. 

The normal one, without having defined specific routes and marked the "Use this connection only for resources on its network", is working. But then one with routes have problems resolving names inside the network.

I have noticed this in the syslog, so the name server is detected, but looks like it is connected to specific "domains". When I do "nslookup some.domain.in.the.vpn.network" it does not show anything. I guess because the some.domain.in.the.vpn.network does not match any of the *.in-addr.arpa addresses so it will be searched inside the 192.168.100.1 nameserver.

```

Aug 12 15:38:22 pjotr-samsung dnsmasq[21602]: using nameserver 192.168.100.1#53
Aug 12 15:38:22 pjotr-samsung dnsmasq[21602]: using nameserver 10.159.0.12#53 for domain 87.in-addr.arpa
Aug 12 15:38:22 pjotr-samsung dnsmasq[21602]: using nameserver 10.159.0.12#53 for domain 93.in-addr.arpa
Aug 12 15:38:22 pjotr-samsung dnsmasq[21602]: using nameserver 10.159.0.12#53 for domain 10.in-addr.arpa

```

So what can I do now?

---

### Post by praseodym on 2012-08-12
Check, if the VPN server uses "LZO compression". You should be able to activate it, too, in the network-manager (somewhere in "advanced"?!).

---

### Post by peterlauri on 2012-08-12
> **praseodym said:**
> Check, if the VPN server uses "LZO compression". You should be able to activate it, too, in the network-manager (somewhere in "advanced"?!).

I cannot find that options anywhere in the VPN configuration (under all advanced tabs/windows I could find)...

---

