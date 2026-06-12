---
title: "Can't find my wireless connection anymore"
date: 2012-10-15
forum: Networking &amp; Wireless
---

### Post by Luixy117 on 2012-10-15
Hello all, 
I installed Ubuntu 12.04 with wubi on my Toshiba Satellite L650 a few days ago and everything worked fine.
Now all of a sudden it doesn't find my wireless network(it still finds other wireless networks).
I've checked if my router is hidden but it's fine.
Can anyone help me?:(

---

### Post by sandyd on 2012-10-15
a) Can you still view the wireless network on another computer?

b) Can you check if
```

sudo iwlist scan
```
detects the network?

c) Post the output of

```

lspci | grep Network
lsmod
ifconfig

```

---

### Post by Luixy117 on 2012-10-15
a)
Yes I created the thread with a tablet.

b) No, it doesn't, it actually only detects 3 networks (with GUI it finds 5)

c)

1.
luixy@ubuntu:~$ lspci | grep Network
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

2.
luixy@ubuntu:~$ lsmod
Module                  Size  Used by
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
joydev                 17693  0 
vesafb                 13844  1 
snd_hda_codec_hdmi     32474  1 
btusb                  18288  2 
bluetooth             180104  23 rfcomm,bnep,btusb
snd_hda_codec_conexant    62358  1 
snd_hda_intel          33773  4 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17390  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                97443  0 
serio_raw              13211  0 
intel_ips              18174  0 
wl                   2568210  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
fglrx                3263886  133 
toshiba_acpi           18582  0 
sparse_keymap          13890  1 toshiba_acpi
wmi                    19256  1 toshiba_acpi
lib80211               14381  2 lib80211_crypt_tkip,wl
snd                    78855  18 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
toshiba_bluetooth      12807  0 
video                  19596  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41718  0 

3.
luixy@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:6c:70:ca:98  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

eth1      Link encap:Ethernet  HWaddr e8:39:df:3e:b6:ca  
          inet6 addr: fe80::ea39:dfff:fe3e:b6ca/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1504 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:122656 (122.6 KB)  TX bytes:122656 (122.6 KB)

Thanks in advance:)

---

### Post by Meschi on 2012-10-15
found this thread, maybe it helps you:
[http://ubuntuforums.org/showthread.php?t=2071260](http://ubuntuforums.org/showthread.php?t=2071260)

P.S. had the same problems but as i wanted to install ubuntu new anyway my problem was automatically solved by performing the fresh installation

---

### Post by VK7AY on 2012-10-16
Have been thru it all, try checking your PC Bios and check that the Network Adapter is showing ENABLED.. Found my own was Disabled, no idea how or why immediate working result.
My system HP Pavilion Laptop, i7, Win 7 with Ubuntu 12.4 installed within by Wubi , 10 months ago, 2 weeks ago failed to connect to Wifi, Wired Connection OK.
May be able to grow finger nails back now.
Best wishes,
donver.

---

### Post by Luixy117 on 2012-11-15
Yeah, I'm sorry this took so long this weeks have been really stressing... I've tried to reinstall ubuntu several times with wubi 
and now with a boot-USB. It detects the wifi-networks of my neighbours but not mine... could it be the Bluetooth-adapter or something?

---

### Post by Luixy117 on 2012-11-15
oh right i do not have a hardware switch and every time I install Ubuntu it automatically turns on both Bluetooth and Wireless Adapter switches

---

