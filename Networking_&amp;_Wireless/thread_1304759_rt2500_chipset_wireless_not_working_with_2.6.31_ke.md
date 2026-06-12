---
title: "rt2500 chipset wireless not working with 2.6.31 kernel"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by presencia on 2009-10-29
Hi everyone,

I just upgraded to xubuntu karmic (xubuntu 9.10). With that came a kernel update from 2.6.28 to 2.6.31. I can still choose between the two at bootup through the grup menu but neither works great for me.
In this thread I want to address my problem with the 2.6.31 kernel version: My wireless LAN does not work. (When I boot using the 2.6.28 kernel version, the wireless LAN works perfectly like it did before the update.)

To give you some information:
I am using a four-year old Fujitsu-Siemens Amilo L 1310G laptop computer with a RaLink rt2500 wireless chipset (at least that's what I understand from my lspci output, which includes the following line (among others):
```
02:01.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
```If i type "sudo lspci -v" I get - among other paragraphs - the following
```

02:01.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: RaLink Device 2560
        Flags: bus master, slow devsel, latency 64, IRQ 23
        Memory at d0204000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2
        Kernel driver in use: rt2500pci
        Kernel modules: rt2500pci

```networt-manager tells me that the wireless LAN device is not ready.
Wired networks work fine though.

"iwconfig" prints 
```
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```"iwlist wlan0 scan" prints
```
wlan0     Failed to read scan data : Network is down
```But when I type "sudo ifconfig wlan0 up" I get
```
SIOCSIFFLAGS: Unknown error 132

```"lsmod" prints
```
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
arc4                    1660  2 
snd_atiixp_modem       11940  2 
snd_atiixp             15720  6 
ecb                     2524  2 
snd_ac97_codec        101216  2 snd_atiixp_modem,snd_atiixp
snd_seq_dummy           2656  0 
ac97_bus                1532  1 snd_ac97_codec
rt2500pci              15356  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  3 snd_pcm_oss
snd_pcm                75296  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
rt2x00pci               7900  1 rt2500pci
snd_seq_oss            28576  0 
rt2x00lib              29756  2 rt2500pci,rt2x00pci
snd_seq_midi            6432  0 
input_polldev           3716  1 rt2x00lib
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
mac80211              181236  2 rt2x00pci,rt2x00lib
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
iptable_filter          3100  0 
cfg80211               93052  2 rt2x00lib,mac80211
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              11692  1 iptable_filter
pcmcia                 36808  0 
x_tables               16544  1 ip_tables
yenta_socket           24200  1 
i2c_piix4               9932  0 
eeprom_93cx6            1916  1 rt2500pci
snd                    59204  23 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rsrc_nonstatic         11644  1 yenta_socket
tifm_7xx1               5372  0 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
sdhci_pci               7100  0 
joydev                 10272  0 
tifm_core               7832  1 tifm_7xx1
soundcore               7264  3 snd
sdhci                  17472  1 sdhci_pci
shpchp                 32272  0 
snd_page_alloc          9156  3 snd_atiixp_modem,snd_atiixp,snd_pcm
led_class               4096  2 rt2x00lib,sdhci
psmouse                56180  0 
serio_raw               5280  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
usbhid                 38208  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
b44                    28684  0 
ssb                    35300  1 b44
mii                     5212  1 b44
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp

```Looks like some rt2x00pci module is used - which sounds fine to me. But I know nothing about kernel modules. And last but not least, here comes the tail of my dmesg output
```
[   54.445572] input: rt2500pci as /devices/pci0000:00/0000:00:14.4/0000:02:01.0/input/input8
[   54.470562] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   54.494993] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.632142] [drm] Setting GART location based on new memory map
[   57.633160] [drm] Loading R300 Microcode
[   57.633206] [drm] Num pipes: 4
[   57.633215] [drm] writeback test succeeded in 1 usecs
[   68.478934] type=1505 audit(1256834921.287:14): operation="profile_replace" pid=836 name=/usr/bin/evince
[   68.513985] type=1505 audit(1256834921.323:15): operation="profile_replace" pid=836 name=/usr/bin/evince-previewer
[   68.516260] type=1505 audit(1256834921.327:16): operation="profile_replace" pid=836 name=/usr/bin/evince-thumbnailer
[   69.303421] type=1505 audit(1256834922.111:17): operation="profile_replace" pid=1077 name=/usr/lib/cups/backend/cups-pdf
[   69.304100] type=1505 audit(1256834922.115:18): operation="profile_replace" pid=1077 name=/usr/sbin/cupsd
[   69.441715] type=1505 audit(1256834922.251:19): operation="profile_replace" pid=1078 name=/usr/sbin/tcpdump
[   74.406622] ppdev: user-space parallel port driver
[  232.816222] b44: eth0: Link is up at 100 Mbps, full duplex.
[  232.816228] b44: eth0: Flow control is off for TX and off for RX.
[  232.816412] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1754.991793] atkbd.c: Unknown key pressed (translated set 2, code 0x6d on isa0060/serio0).
[ 1754.991799] atkbd.c: Use 'setkeycodes 6d <keycode>' to make it known.
[ 1755.233371] atkbd.c: Unknown key released (translated set 2, code 0x6d on isa0060/serio0).
[ 1755.233376] atkbd.c: Use 'setkeycodes 6d <keycode>' to make it known.

```I hope there is someone who can help me to fix this problem or give me a hint about what to try next. I would greatly appreciate any helpful comment. And - of course - I will be happy to provide more information if requested.

You could say: Why not just use kernel version 2.6.28. Well, you are right. But the update to karmic broke my sound support for this kernel version. Sound works fine with the 2.6.31 version. I would love to have both, sound AND a wireless connection. So I just start trying to make the newest version work.

---

### Post by presencia on 2009-10-31
Is there hope or is there not? (for getting my wireless to work)

I would appreciate any helpful comment, even if it sais "don't bother, there is no way", in which case I could get the topic off my agenda.

---

### Post by anilkumar.as on 2009-11-01
I have a rt73usb. Same issue. I have been trying to get windows driver for my chipset. If u have windows driver can you try it with ndiswrapper?

---

### Post by presencia on 2009-11-01
Thanks anilkumar,

you have given me hope. So I tried again. Fortunately there were others with the same issue, now that Karmic has been out for a few days. I found this thread in the german ubuntuusers.de forum ([http://forum.ubuntuusers.de/topic/nach-karmic-update-rt2500-klankarte-nicht-bet/#post-2206004](http://forum.ubuntuusers.de/topic/nach-karmic-update-rt2500-klankarte-nicht-bet/#post-2206004)) where someone proposes to type
```
sudo iwconfig wlan0 txpower auto
```After that I had to deactivate wireless connections in the Network Manager menu and activate it again - and now it works! Without installing anything. The only issue: I have to type the above commad everytime I have boot my machine. How can I have that done automatically? Are there any scripts run before Network Manager is started? - were I could put in this command? Or where should I look?
And another question: Can anyone tell me what that command does and why it is working now?

---

### Post by anilkumar.as on 2009-11-01
Nice! It did work well. The command sets transmit power of your wireless card. Even my wired connection is messed up in 9.10. DHCP doesn't work. For both wired and wireless I have to manually configure.

---

