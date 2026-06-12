---
title: "Unstable wired connection on Ubuntu 11.10"
date: 2012-03-21
forum: Networking &amp; Wireless
---

### Post by Greyvend on 2012-03-21
Hello. I apologize if this problem is already solved, but I've seen only threads about same problem with wireless connection.
So, my wired connection often drops out(or how is it called in English :roll:) when I surf the Internet. Also the speed is very unstable. Sometimes it is same as in Win7 but often it is very slow (5-10 times slower).
Here are some logs I've seen requested on similar problems. 
```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

```

lsmod
Module                  Size  Used by
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
binfmt_misc            17540  1 
saa7134_alsa           18602  1 
tuner_simple           18551  1 
tuner_types            24318  1 tuner_simple
tda9887                14154  1 
tda8290                22616  0 
tuner                  27428  2 
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
ir_sony_decoder        12549  0 
snd_hda_codec_hdmi     32040  1 
ir_jvc_decoder         12546  0 
rc_avermedia           12508  0 
snd_hda_codec_realtek   330815  1 
snd_hda_intel          33390  3 
ir_rc6_decoder         12546  0 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
ir_rc5_decoder         12546  0 
saa7134               181851  1 saa7134_alsa
ir_nec_decoder         12546  0 
rc_core                26963  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,rc_avermedia,ir_rc6_decoder,ir_rc5_decoder,saa7134,ir_nec_decoder
videobuf_dma_sg        19354  2 saa7134_alsa,saa7134
snd_seq_midi           13324  0 
videobuf_core          26390  2 saa7134,videobuf_dma_sg
v4l2_common            16454  2 tuner,saa7134
fglrx                2928969  158 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hwdep              13668  1 snd_hda_codec
videodev               92992  3 tuner,saa7134,v4l2_common
snd_pcm                96714  4 saa7134_alsa,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  19 saa7134_alsa,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
tveeprom               21249  1 saa7134
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mxm_wmi                12979  0 
wmi                    19256  1 mxm_wmi
mei                    41480  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  52788  0 
xhci_hcd               82820  0 

```

```

lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169

```

---

### Post by lz1dsb on 2012-03-21
The first output you provide is normal. iwconfig is a command that is used to configure wireless interfaces. So it's normal to get this. i.e. the wired interface shouldn't have any "wireless extensions".
[http://www.linuxcommand.org/man_pages/iwconfig8.html](http://www.linuxcommand.org/man_pages/iwconfig8.html)

Could you provide an output of the command ipconfig before and after you get this error. Just to check first what your IP configuration is. Than we'll start it from there.

---

### Post by Greyvend on 2012-03-21
Well, it's hard to define, when it disconnects, because it happens randomly and restores in a few minutes, and I think it also depends on target address. Here is ifconfig(ipconfig is only on Windows, or am I wrong?)

```

ifconfig
eth0      Link encap:Ethernet  HWaddr 50:e5:49:3a:68:ea  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38144 errors:0 dropped:38144 overruns:0 frame:38144
          TX packets:37860 errors:0 dropped:489 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40611434 (40.6 MB)  TX bytes:4813930 (4.8 MB)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:154502 (154.5 KB)  TX bytes:154502 (154.5 KB)

```
Edit: I caught ifconfig immediately after one of web-sites failed to load
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 50:e5:49:3a:68:ea  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41600 errors:0 dropped:41600 overruns:0 frame:41600
          TX packets:41166 errors:0 dropped:511 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44481679 (44.4 MB)  TX bytes:5244281 (5.2 MB)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1299 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:169092 (169.0 KB)  TX bytes:169092 (169.0 KB)

```
As you see, these configs are pretty similar.
Btw browser shows such an explanation: "The server at [www.google.ru](www.google.ru) can't be found, because the DNS lookup failed". And error msg is: Error 105 (net::ERR_NAME_NOT_RESOLVED): Unable to resolve the server's DNS address.

---

### Post by Greyvend on 2012-03-22
Well, it seems that my problem is already solved. I've tried the solution and for now it works completely.
Here is the link : [http://ubuntuforums.org/showthread.php?t=1913099&highlight=r8168](http://ubuntuforums.org/showthread.php?t=1913099&highlight=r8168)
Note for people, who will find this thread: this solution of unstable connection is for those, who has Realtek 8168 series network card and wrong kernel driver booting. You may check it by typing 
lspci -nnk | grep -iA2 net in terminal.

Thanks for the help!

---

### Post by lz1dsb on 2012-03-22
That's rather interesting. So it's really a driver issue in this case. I was thinking that it could be something related with the IP network or settings...
It's nice that you've also published the solution so that we all can benefit from it. :guitar:

---

### Post by lz1dsb on 2012-03-22
An yes, I forgot. You could mark this thread as SOLVED.

---

