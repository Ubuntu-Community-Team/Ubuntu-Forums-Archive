---
title: "Just another networking problem"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by martin11235 on 2013-07-08
Hello,

Im facing some problems with networking at home... THe weird thing is I'm able to connect to my wifi at work. There it works perfectly, but when i come home nothing works...
Coble is not working at all! And my wifi fails after aproximately 1 minutes of internet connection....I can thou connect to router, there is no problem only internet access is having some trouble...And as I said cable is totally useless cannot connect even to router. I never had this problem b4 and windows7 is wroking totally fine. I tried static instead of DHCP didnt help...

Maybe the problem may be that i installed this ubuntu in work connected to wi-fi and when i came home this was happening...
Now Im getting  warrnings  while booting ubuntu like "trying to connect to nework" then ubuntu is waiting 60sec and then starts without network cofiguration. When i login i dont even have my internet minicion on the menu top right. I must 'sudo iocnfig eth0 up' to activate it.

This is my ifconfig:
eth0      Link encap:Ethernet  HWaddr b8:88:e3:8f:3a:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55402 (55.4 KB)  TX bytes:55402 (55.4 KB)


wlan0     Link encap:Ethernet  HWaddr 84:a6:c8:c3:cf:0d  
          inet addr:10.0.0.139  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::86a6:c8ff:fec3:cf0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4724 (4.7 KB)  TX bytes:74922 (74.9 KB)

and this is /etc/network/interface :



#opback network interface


auto lo eth0


iface lo inet loopback






# The primary network interface


iface eth0 inet dhcp


Any ideas? I dont wanna reinstall ubuntu only because of that...

---

### Post by praseodym on 2013-07-08
Reset the file via
```

gksudo gedit /etc/network/interfaces
```
to```

auto lo [COLOR="#FF0000"]#without eth0 here[/COLOR]
iface lo inet loopback
```
only and reboot

---

### Post by martin11235 on 2013-07-08
Ok i changed /etc/network/interfaces only to hose two lines andit stopped warnning me while booting. But i still cannot access anything through cable and im sure wifi will crash any moment...In few hours i go to work and there it will work perfectly im sure :/

---

### Post by praseodym on 2013-07-08
Hardware check:
```

lspci -nnk | grep -iA2 net
lsmod
cat /etc/resolv.conf
route -n
```

---

### Post by martin11235 on 2013-07-20
I was on hollyday so my replay is kinda late, here are outputs from commamds

lspci -nnk | grep -iA2 net
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Lenovo Device [17aa:397f]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0888] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4262]
    Kernel driver in use: iwlwifi


```

lsmod
```

Module                  Size  Used by
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_realtek    79855  1 
parport_pc             32867  0 
rfcomm                 47562  12 
bnep                   18240  2 
ppdev                  17114  0 
fglrx                5192292  0 
arc4                   12530  2 
iwlwifi               399614  0 
snd_hda_intel          34063  3 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
rts5139               350620  0 
coretemp               13642  0 
i915                  535221  2 
mac80211              555272  1 iwlwifi
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
drm_kms_helper         49259  1 i915
uvcvideo               78117  0 
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
btusb                  22432  0 
snd_seq_midi_event     14900  1 snd_seq_midi
videobuf2_core         33025  1 uvcvideo
drm                   290595  3 i915,drm_kms_helper
kvm                   422160  0 
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
videodev              125126  2 uvcvideo,videobuf2_core
bluetooth             211812  24 rfcomm,bnep,btusb
lp                     17800  0 
snd_timer              29990  2 snd_pcm,snd_seq
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
ideapad_laptop         18235  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13565  1 i915
soundcore              15092  1 snd
amd_iommu_v2           19228  1 fglrx
psmouse               102506  0 
cfg80211              208382  2 iwlwifi,mac80211
mei                    41410  0 
parport                46563  3 parport_pc,ppdev,lp
ghash_clmulni_intel    13221  0 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
cryptd                 20531  1 ghash_clmulni_intel
sparse_keymap          13891  1 ideapad_laptop
serio_raw              13216  0 
joydev                 17694  0 
lpc_ich                17145  0 
mac_hid                13254  0 
video                  19653  1 i915
microcode              23030  0 
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
ahci                   25869  2 
libahci                27338  1 ahci
r8169                  62705  0 


```

cat /etc/resolv.conf
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
```


route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.254.0.109    0.0.0.0         UG    0      0        0 wlan0
10.254.0.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0


```

Thanks

---

### Post by praseodym on 2013-07-20
Deactivate the N-mode of the driver (bug):

```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

