---
title: "I broke Network Manager..."
date: 2012-06-15
forum: Networking &amp; Wireless
---

### Post by joealanbrooks on 2012-06-15
So I copy-pasted some terminal command I found on some webpage to disable Network Manager.  Now I can't find the page or remember what it was I ran.

I've purged and reinstalled Network Manager but still can't connect to the internet.  Both wired and wireless are shown in the status bar, and I can connect to networks, but pings stall and webpages don't load.

What could I possibly have done?  Any help is greatly appreciated.

---

### Post by praseodym on 2012-06-15
Try
> 
sudo service network-manager restart

---

### Post by joealanbrooks on 2012-06-15
No, it wasn't that... I guess it was more of a command to keep Network Manager from ever starting.  It used a method I'd never heard of before.  I guess I blacklisted something somewhere.

[edit] Using wicd gives the same problem: I can get an IP but can't load a webpage.

---

### Post by praseodym on 2012-06-15
So, please show:

```
lspci -nnk | grep -iA2 net
lsmod
lsusb
```
Use the "Arrow-Up"-Cursor--Key to go back to the command you used

---

### Post by joealanbrooks on 2012-06-15
Unfortunately the command isn't in my terminal history.  

```
joe@joe-htpc:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Realtek Semiconductor Co., Ltd. TEG-ECTX Gigabit PCI-E Adapter [Trendnet] [10ec:8168]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:05.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
    Subsystem: Ralink corp. Device [1814:2860]
    Kernel driver in use: rt2800pci

joe@joe-htpc:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
udf                    94317  1 
crc_itu_t              12707  1 udf
vesafb                 13844  1 
arc4                   12529  2 
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  4 
snd_usb_audio         122982  1 
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  4 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_timer              29990  2 snd_seq,snd_pcm
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
eeprom_93cx6           12725  1 rt2800pci
binfmt_misc            17540  1 
snd                    78855  22 snd_hda_codec_hdmi,snd_usb_audio,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer,snd_seq_device
psmouse                87692  0 
serio_raw              13211  0 
uvcvideo               72627  0 
joydev                 17693  0 
videodev               98259  1 uvcvideo
hid_logitech_dj        18593  0 
soundcore              15091  1 snd
v4l2_compat_ioctl32    17128  1 videodev
sp5100_tco             13791  0 
nvidia              12319264  40 
mac_hid                13253  0 
wmi                    19256  0 
edac_core              53746  0 
k10temp                13166  0 
edac_mce_amd           23709  0 
i2c_piix4              13301  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid
pata_atiixp            13204  0 
r8169                  62099  0 

joe@joe-htpc:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:0826 Logitech, Inc. 
Bus 006 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
```

---

### Post by praseodym on 2012-06-16
Try:

```
sudo service network-manager stop
sudo service wicd restart
```
Choose **wlan0** as interface name and **wext** as driver.

---

### Post by joealanbrooks on 2012-06-16
Okay cool, that did fix wicd, at least for a second.  Thanks.  So I guess this is just a Network Manager issue.

I also get a message from time to time telling me aptd crashed, usually upon booting... Dunno if that's related but after I restarted just now, it popped up, and now I'm having trouble getting wicd to load pages, even after stopping network-manager and restarting the wicd service.

The command I originally ran to broke this I think edited some config file for some other package and added something about network-manager to it.

---

### Post by praseodym on 2012-06-16
Check:

```
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/NetworkManager.conf
```
Try to uninstall the NM for Wicd only?!

---

### Post by joealanbrooks on 2012-06-16
```
joe@joe-htpc:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

joe@joe-htpc:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false
```Purged network-manager, wicd still not co-operating. :(

[edit] Hm... On a whim, I disabled "IP Flood Detection" in the settings of my router, and that did the trick.  Reinstalled network-manager and it's working.  Still doesn't make sense to me since a different installation of Ubuntu running on this exact same hardware has no problem with it enabled.  

I may have this problem come up again when I move this computer to a different network, but for now I'm satisfied.

Thanks for your help, prasesodym!

---

