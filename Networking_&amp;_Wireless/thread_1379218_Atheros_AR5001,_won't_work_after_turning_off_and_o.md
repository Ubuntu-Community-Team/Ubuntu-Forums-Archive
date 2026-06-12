---
title: "Atheros AR5001, won't work after turning off and on"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by Jarige on 2010-01-12
I've got a little netbook, and all works fine, except for one small thing. I'm able to connect to a wireless network with my Atheros AR5001 just fine. However, if I right click on the network icon, and disable network or wireless and enable it again, wireless won't work anymore. I can't see and connect to any network at all. Except when using airodump-ng from the famous aircrack-ng tool set. When using airodump I'm able to see any network and their specs just fine. I don't even have to be in monitor mode to do airodump-ng (the wireless must be off in the network manager though).

Is there any way of getting my wireless back when I turn it on again?

Greatly appreciated if you'd help :)

---

### Post by adam814 on 2010-01-12
You could try pulling and re-inserting the modules.  I assume your card uses madwifi since it's Atheros.
If so try this:
```
sudo modprobe -r ath_pci && sudo modprobe -r ath_hal && sudo modprobe ath_hal && sudo modprobe ath_pci
```

---

### Post by Jarige on 2010-01-12
Thanks for your reply, I executed the command, but I got an error. 

```
FATAL: Module ath_pci not found.
```

---

### Post by adam814 on 2010-01-12
Well, I guess you're not using that driver then.  Could you post the output of these commands?
```
lspci
sudo lshw -C network
lsmod
```
That should give a little more information on what's going on exactly

---

### Post by Jarige on 2010-01-12
Thanks for your reply, these are the massive outputs:


lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```
sudo lshw -C network  :

```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:9f:8d:b2
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:3000(size=256) memory:31010000-31010fff(prefetchable) memory:31000000-3100ffff(prefetchable) memory:31020000-3103ffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:68:c6:73:61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.108 latency=0 multicast=yes wireless=IEEE 802.11bg
resources: irq:18 memory:35200000-3520ffff

```


lsmod:

```
Module                  Size  Used by
usb_storage            52576  3 
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
iptable_filter          3100  0 
uvcvideo               59080  0 
ip_tables              11692  1 iptable_filter
videodev               36736  1 uvcvideo
x_tables               16544  1 ip_tables
v4l1_compat            14496  2 uvcvideo,videodev
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  4 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1660  2 
snd_seq_dummy           2656  0 
ecb                     2524  2 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
psmouse                56500  0 
ath5k                 124260  0 
serio_raw               5280  0 
mac80211              181140  1 ath5k
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath                     8060  1 ath5k
acerhdf                 8116  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
led_class               4096  1 ath5k
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
cfg80211               93052  3 ath5k,mac80211,ath
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
r8169                  32064  0 
mii                     5212  1 r8169
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp

```

I hope you can help me :)

---

### Post by adam814 on 2010-01-12
Try this then:
```
sudo modprobe -r ath5k && sudo modprobe ath5k
```

---

### Post by Jarige on 2010-01-12
lol,you needed all those outputs for just that small command :P
The command worked, thanks :D
But I'm not sure whether it works permanently, does it?. I tested it a minute ago, and after turning wireless off and on again it started connecting :D
And the place where the problems is the most annoying is somewhere else. I can only test this in two days, so you'll hear from me then.

So far, thanks for your efforts :D

---

### Post by adam814 on 2010-01-12
As it turns out I could have gotten by with just either the 2nd or 3rd one, but I thought it would be easier to have all the info there at once.

It's probably not a permanent fix exactly, but it seems like your wireless driver doesn't like having the device powered off.  I believe I have to do that with mine, although I don't turn off wifi that often and then need it before a reboot.

If nothing else hopefully it's a decent workaround until someone with more knowledge about the ath5k driver can work something else out.

---

### Post by Jarige on 2010-01-12
Thanks, its quite a decent workaround indeed since the only reason for me to turn off wireless is to change my mac addres from commandline anyway :)

I'll leave the info here, and hope someone else knows what to do. In the meantime, I'm a lot happier with this workaround :)

---

### Post by adam814 on 2010-01-12
Hmm...you should be able to change your MAC address without powering off your wireless.  You just need to do an "ifconfig <interface> down" first.  Then you can do "ifconfig <interface> hw ether <mac address>" to change it.

---

### Post by Jarige on 2010-01-12
Hm, I'll keep that in mind. I use the program macchanger, only because I recently found out that it was also possible with ifconfig. Macchanger is a little easier, but I'll safe that command for when I'm not connected to the internet.
But is right clicking the networkicon and deactivating wireless equivalent to turning wireless of the hardware way (button)?

---

### Post by adam814 on 2010-01-12
I'm familiar with macchanger as well.  It should work just the same - "ifconfig <interface> down" then use macchanger, then "ifconfig <interface> up".

Yes and no.  It *may* work for what you need to change the MAC address.  I use wicd so I can't test that myself.  But it doesn't pull the module or power off the hardware.  If you're doing it to save power it might save some, but not as much as turning it off with the button.

---

### Post by Jarige on 2010-01-12
Ok, thank you very much :D
Your answers were very clear. I saved the commands in case I forget them, but since their easy I don't think I will :)
Now I'll just wait for some ath5k driver expert :)

---

### Post by Jarige on 2010-01-22
This bug still affects me every day and its driving me nuts! I don't even know what it is, and how to report it. This is quite a serious bug that might affect people who buy Netbooks with Ubuntu preinstalled.

---

