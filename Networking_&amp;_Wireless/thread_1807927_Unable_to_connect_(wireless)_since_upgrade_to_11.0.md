---
title: "Unable to connect (wireless) since upgrade to 11.04"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by Dava02 on 2011-07-19
Hi

What has changed to the wireless function and possibly the use of the ndiswrapper in 11.04.

I originally install ubuntu 9.10 and immediately upgraded to 10.04. I have just now decided to upgrade to 10.10 and then to 11.04. Everything went ok and all still worked fine up until the upgrade to 11.04.

I've checked my settings and they are fine. The power light is still on my wireless card but no connection?

---

### Post by wildmanne39 on 2011-07-19
> **Dava02 said:**
> Hi

What has changed to the wireless function and possibly the use of the ndiswrapper in 11.04.

I originally install ubuntu 9.10 and immediately upgraded to 10.04. I have just now decided to upgrade to 10.10 and then to 11.04. Everything went ok and all still worked fine up until the upgrade to 11.04.

I've checked my settings and they are fine. The power light is still on my wireless card but no connection?
Hi, please run these commands in a terminal
```
lspci -nn
```
```
rfkill list all
```
```
iwconfig
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Dava02 on 2011-07-20
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
06:09.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
07:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

```
rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
lsmod
Module                  Size  Used by
snd_hrtimer            12680  1 
parport_pc             32111  0 
ppdev                  12849  0 
ndiswrapper           192828  0 
binfmt_misc            13213  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
i915                  450934  3 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  3 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
snd_timer              28659  3 snd_hrtimer,snd_pcm,snd_seq
acer_wmi               23153  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  0 
joydev                 17322  0 
sparse_keymap          13666  1 acer_wmi
drm                   180037  4 i915,drm_kms_helper
snd                    55295  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
psmouse                73312  0 
soundcore              12600  1 snd
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
serio_raw              12990  0 
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
8139too                23208  0 
8139cp                 22497  0 
```

---

### Post by wildmanne39 on 2011-07-20
Hi, try this to turn it on.
```
sudo rmmod -f acer-wmi
```
Also you do not have to use ndiswrapper, you would probably get better speed and stability with the broadcom driver for your card.

---

### Post by Dava02 on 2011-07-20
ah ok. i'll have a fiddle and swap methods.

Thanks very much for the quick help

---

### Post by wildmanne39 on 2011-07-20
> **Dava02 said:**
> ah ok. i'll have a fiddle and swap methods.

Thanks very much for the quick help
Hi, here is a link to install the drivers for your 4318 card.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by Dava02 on 2011-07-26
Hi again

Ok i've now uninstalled the ndiswrapper and installed the b43fwcutter as stated in the link you provided. However after the reboot the wireless adapter is still showing no power. I ran the diagnostic check and there is a soft blocked yes. I've tried to unblock it but it keeps showing as blocked??

---

### Post by wildmanne39 on 2011-07-26
Hi, run this command again now that you have removed ndiswrapper.
```
sudo rmmod -f acer-wmi
```

If it does not connect please run these commands also
```
rfkill list all
```
```
lsmod
```
and post the results.

Please make sure the wired connection is unplugged and go to the right top corner of the screen and make sure enable wireless is checked before you run the first command I gave you.
Thank you

---

