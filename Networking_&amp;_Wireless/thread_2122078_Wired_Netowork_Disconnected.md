---
title: "Wired Netowork Disconnected"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by Dragonatorul on 2013-03-04
I just installed ubuntu 12.04 on a repaired Acer Travel-mate 5320 and everything worked fine for the first run, except for flash, until I got a message that I should reboot because of updates. After the reboot I am unable to connect to my local network and internet. The network port and rooter lights are blinking but the Wired Network disconnected message keeps flashing and my router does not detect the laptop. I will update the thread with more info as soon as I manage to connect wirelessly somehow.

---

### Post by carl4926 on 2013-03-04
Post result of
```
lspci -nnk | grep -iA2 net
```

---

### Post by Dragonatorul on 2013-03-04
Here are some results from commands I saw in previous threads. Hope this helps.

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:1d:72:c3:a3:93  
          inet6 addr: fe80::21d:72ff:fec3:a393/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:2045 dropped:0 overruns:0 frame:24223
          TX packets:401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:97900 (97.9 KB)
          Interrupt:16 

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:488336 (488.3 KB)  TX bytes:488336 (488.3 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:172.20.159.134  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:8096 (8.0 KB)  TX bytes:5947 (5.9 KB)

```


lscpi -nnk |grep -iA2 net
```
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: tg3
--
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Foxconn International, Inc. T77H030.00 Wireless Mini PCIe Card [105b:e003]
	Kernel driver in use: b43-pci-bridge
```


lsmod
```
Module                  Size  Used by
ppp_deflate            12879  0 
zlib_deflate           26623  1 ppp_deflate
bsd_comp               12843  0 
ppp_async              17308  1 
option                 25700  1 
usb_wwan               19532  1 option
usbserial              36882  5 option,usb_wwan
nls_utf8               12494  1 
isofs                  39595  1 
usb_storage            39720  1 
dm_crypt               22572  1 
coretemp               13362  0 
joydev                 17394  0 
acer_wmi               27975  0 
sparse_keymap          13659  1 acer_wmi
pcmcia                 39855  0 
snd_hda_codec_realtek    64959  1 
snd_hda_intel          33029  3 
snd_hda_codec         116477  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
b43                   351542  0 
microcode              18396  0 
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
tifm_7xx1              12938  0 
psmouse                91022  0 
mac80211              475546  1 b43
tifm_core              15069  1 tifm_7xx1
snd_seq_midi           13133  0 
serio_raw              13032  0 
yenta_socket           27465  0 
pcmcia_rsrc            18368  1 yenta_socket
snd_rawmidi            25426  1 snd_seq_midi
cfg80211              181041  2 b43,mac80211
lpc_ich                16993  0 
uvcvideo               72249  0 
pcmcia_core            21512  3 pcmcia,yenta_socket,pcmcia_rsrc
bcma                   34573  1 b43
videobuf2_core         32212  1 uvcvideo
nsc_ircc               23235  0 
videodev              100265  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
irda                  185617  1 nsc_ircc
videobuf2_memops       13213  1 videobuf2_vmalloc
snd_seq_midi_event     14476  1 snd_seq_midi
crc_ccitt              12628  2 ppp_async,irda
rfcomm                 38104  0 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
bnep                   17791  2 
parport_pc             32115  0 
ppdev                  12850  0 
bluetooth             189585  10 rfcomm,bnep
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62675  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13078  0 
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
firewire_ohci          36110  0 
sdhci_pci              18263  0 
sdhci                  32293  1 sdhci_pci
firewire_core          61957  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
i915                  470817  3 
drm_kms_helper         47459  1 i915
wmi                    18745  1 acer_wmi
tg3                   141717  0 
drm                   240232  4 i915,drm_kms_helper
i2c_algo_bit           13317  1 i915
video                  19117  2 acer_wmi,i915
ssb                    50757  1 b43
```

dmesg | egrep 'eth0|b44'
```
[    7.059944] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95787m) rev b002] (PCI Express) MAC address 00:1d:72:c3:a3:93
[    7.059951] tg3 0000:02:00.0: eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    7.059955] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    7.059958] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   24.012492] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.904247] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.904888] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.531755] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[   27.531761] tg3 0000:02:00.0: eth0: Flow control is on for TX and on for RX
[   27.531934] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  245.388198] tg3 0000:02:00.0: eth0: Link is down
[  247.645065] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[  247.645070] tg3 0000:02:00.0: eth0: Flow control is on for TX and on for RX
[  266.152415] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  267.737968] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[  267.737973] tg3 0000:02:00.0: eth0: Flow control is on for TX and on for RX
[  267.738146] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  508.669136] tg3 0000:02:00.0: eth0: Link is down
[  513.004423] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  841.463824] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[  841.463829] tg3 0000:02:00.0: eth0: Flow control is on for TX and on for RX
[  841.464067] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
```

---

### Post by carl4926 on 2013-03-04
I can get your wireless working
Download this folder: [https://docs.google.com/folder/d/0B3e0lLG3OdqEWlNMRFcxbVN5Z2s/edit?usp=sharing](https://docs.google.com/folder/d/0B3e0lLG3OdqEWlNMRFcxbVN5Z2s/edit?usp=sharing)

Place the folder in your /home/username*

Open a terminal and paste this with your mouse

```
sudo mv b43 /lib/firmware
```

Then reboot

BTW: It looks like your wired device should work.

---

### Post by carl4926 on 2013-03-04
This might be easier
[http://dl.dropbox.com/u/10573557/b43_firmware/2013_b43/b43.zip](http://dl.dropbox.com/u/10573557/b43_firmware/2013_b43/b43.zip)

---

### Post by Dragonatorul on 2013-03-04
I don't have a wireless access point I can use, I just used a 3g dongle to post those results. But the wireless should theoretically work with a proprietary wireless driver I manually disabled because it kept searching for wireless networks I won't use. 

My problem is the wired network. It should work, but it doesn't.

---

### Post by carl4926 on 2013-03-04
I suggest using b43 for wireless rather than proprietary (wl)

Try booting with one of the earlier kernels

---

### Post by Dragonatorul on 2013-03-04
Booting with one of the earlier kernels?

---

### Post by Dragonatorul on 2013-03-04
I'm back from the laptop. I've set it aside for a couple of hours and booted again. A friend said I should see a menu before boot-up that would allow me to pick a kernel. I don't see any such menu, just the boot screen and then the login screen. 

Anyway, I'm tempted to say the problem has been resolved, since there are no more flashing wired network disconnected messages and the wired connection seems to be working fine now. I'm pretty sure this wasn't because of the cable, though the plug is missing the clip that fixes it in place. Even when was sure that it was all the way in and properly connected (the lights were flashing and everything) there were still those warnings and the router did not see the laptop. Thank you for the wireless drivers. I will install them right now.

---

### Post by carl4926 on 2013-03-04
If you only have Ubuntu installed you might not see the Grub menu
I think if you hold SHIFT at boot you get a menu
Then choose the 'Advanced options for Ubuntu'
Just FYI/Future ref;

---

### Post by Dragonatorul on 2013-03-04
OK. It worked for an hour or so, just like before, but then it just died. No warning or error. Rebooted, held shift and tried with an earlier kernel. The same error.

I even tried with a different cable. It's just not working.

In System settings > Network, the wired network shows as switching between off and on. This happens on both kernels:
Ubuntu, with Linux 3.5.0-25-generic
Ubuntu, with Linux 3.5.0-23-generic

I'm starting to suspect a hardware problem. Maybe when it warms up the network card crashes.

---

### Post by carl4926 on 2013-03-04
I'm not clever enough to offer much more advice to be honest.
I have a similar device that uses the same driver, but it's never failed yet. I use wireless mostly though.

Are you able to test it in Windows?

---

### Post by Dragonatorul on 2013-03-04
I've just installed the OS so I'll give it a shot reinstalling and testing with windows to confirm it's the hardware. This will have to wait for another day though.

---

