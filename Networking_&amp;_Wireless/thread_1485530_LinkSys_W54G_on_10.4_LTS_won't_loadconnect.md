---
title: "LinkSys W54G on 10.4 LTS won't load/connect"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by kanb on 2010-05-16
I am a [COLOR=Red]***complete novice***[/COLOR] with Ubuntu ... trying it with a "Live CD" on a Compaq Presario 1700 (P3/700MHz/512MB) with a LinkSys  "Wireless-G Notebook Adaptor with SRX400" (Model WPC54GX4 - using Windows drivers LSSRX4.bin & LSSRX42.sys, Airgo Networks Version 2.0.1.19).

The PWR" and "Link" lights are "ON".

This card works fine with WinXP.

I have tried to set it up using the Network Tools and "editing" data into the "Network Manager Applet" (entered SSID, and a "WPA & WPA2 Personal" password), but no improvement.

Here are some outputs from various commands -

***[COLOR=Red]lshw -C network:[/COLOR]***
[FONT=Courier New]  *-network
       description: Ethernet interface
       product: HCF 56k Modem
       vendor: Conexant Systems, Inc.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 08
       serial: 00:50:8b:ac:66:b5
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=160 maxlatency=40 mingnt=20 multicast=yes
       resources: irq:9 ioport:1400(size=256) memory:f4000000-f4003fff  

  *-network UNCLAIMED
       description: Ethernet controller
       product: AGN300 802.11 a/b/g True MIMO Wireless Card
       vendor: Airgo Networks Inc
       physical id: 1
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=248 maxlatency=255 mingnt=24
       resources: memory:24080000-2409ffff memory:24000000-2407ffff[/FONT]

***[COLOR=Red]lspci -nn |grep "'Wireless':[/COLOR]***
[FONT=Courier New]02:00.0 Ethernet controller [0200]: Airgo Networks Inc AGN300 802.11 a/b/g True MIMO Wireless Card [17cb:0002] (rev 01)[/FONT]

***[COLOR=Red]ifconfig:[/COLOR]*** (wlan is not listed)
[FONT=Courier New]eth0    Link encap:Ethernet  HWaddr 00:50:8b:ac:66:b5  
          inet6 addr: fe80::250:8bff:feac:66b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:15 dropped:0 overruns:0 carrier:30
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0x1400 

lo       Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6960 (6.9 KB)  TX bytes:6960 (6.9 KB)[/FONT]

***[COLOR=Red]iwconfig:[/COLOR]***
[FONT=Courier New] lo       no wireless extensions
 eth0   no wireless extensions[/FONT]

***[COLOR=Red]lsmod:[/COLOR]***
[FONT=Courier New]snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
joydev                  8708  0 
pcmcia                 33024  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           20408  2 
snd                    54148 14 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
rsrc_nonstatic         10015  1 yenta_socket
i2c_piix4               8335  0 
serio_raw               3978  0 
soundcore               6620  1 snd
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 28820  0 
squashfs               20680  1 
aufs                  149050  1 
isofs                  29250  1 
nls_iso8859_1           3249  2 
nls_cp437               4919  3 
vfat                    8901  2 
fat                    47767  1 vfat
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  1 
intel_agp              24177  1 
vgastate                8961  1 vga16fb
tulip                  44136  0 
agpgart                31724  1 intel_agp
ramzswap                6362  1 
xvmalloc                4074  1 ramzswap
lzo_decompress          2189  1 ramzswap
lzo_compress            1853  1 ramzswap[/FONT]

---

### Post by NUboon2Age on 2010-05-16
```
*-network UNCLAIMED
description: Ethernet controller
product: AGN300 802.11 a/b/g True MIMO Wireless Card
vendor: Airgo Networks Inc
...
configuration: latency=248 maxlatency=255 mingnt=24
resources: memory:24080000-2409ffff memory:24000000-2407ffff
```

Hmmm...  my experience is extremely limited, but that 

```
*-network UNCLAIMED
``` I haven't seen before, and the fact ```
configuration: latency=248 maxlatency=255 mingnt=24
``` doesn't list a driver makes me think maybe there's no driver loaded.

Try running Jockey, the third party driver manager System->Administration->Hardware Drivers, and see if it suggests a proprietary manager.

---

### Post by kanb on 2010-05-17
> **NUboon2Age said:**
> ```
*-network UNCLAIMED
description: Ethernet controller
product: AGN300 802.11 a/b/g True MIMO Wireless Card
vendor: Airgo Networks Inc
...
configuration: latency=248 maxlatency=255 mingnt=24
resources: memory:24080000-2409ffff memory:24000000-2407ffff
```

Hmmm...  my experience is extremely limited, but that 

```
*-network UNCLAIMED
``` I haven't seen before, and the fact ```
configuration: latency=248 maxlatency=255 mingnt=24
``` doesn't list a driver makes me think maybe there's no driver loaded.

Try running Jockey, the third party driver manager System->Administration->Hardware Drivers, and see if it suggests a proprietary manager.
Thanks, NUboon2AGE,

Ran "Jockey" and it reported.

"No proprietary drivers are in use on this system"

Kanb

---

### Post by marvinudy on 2010-05-17
kanb,

Take a look at the post by 'flash63' on the link listed below.

I followed the 'fix' step by step and it worked fine on a wireless usb 802.11b/g unit that required a rt2870 driver.

best regards,

marvinudy

[http://ubuntuforums.org/showthread.php?t=1236955&highlight=flash63](http://ubuntuforums.org/showthread.php?t=1236955&highlight=flash63)

---

### Post by kanb on 2010-05-17
Thanks for your reply, Marvinudy.

I took a look at the post by 'flash63' and it looks like I will have to learn a LOT more about Ubuntu to "fix" this problem.

Looks like I will have to actually INSTALL Ubuntu to do this and I'm not sure I want to do this.  I am a much more "casual" user than this appears to require.

Maybe I'll just stay with XP for a while longer.

Kanb

---

