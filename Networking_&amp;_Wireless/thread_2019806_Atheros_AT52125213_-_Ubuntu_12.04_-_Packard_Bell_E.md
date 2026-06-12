---
title: "Atheros AT5212/5213 - Ubuntu 12.04 - Packard Bell Easynote R1010"
date: 2012-07-07
forum: Networking &amp; Wireless
---

### Post by jst65 on 2012-07-07
Hello,

I need help using wifi on this old laptop.

I figured out what commands to type by reading some old posts and the sticky "How to post a wireless issue" so I hope i am doing good.

Here are the commands:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod | grep "ath5k"
dmesg | grep "ath5k"
```And their output:
```

stefano@EasyNote:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux EasyNote 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux
stefano@EasyNote:~$ lspci -nnk | grep -iA2 net
00:06.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Wireless Network Adapter [168c:0013] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7084]
    Kernel modules: ath5k
--
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
    Subsystem: Packard Bell B.V. Device [1631:c015]
    Kernel driver in use: via-rhine
stefano@EasyNote:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
stefano@EasyNote:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

stefano@EasyNote:~$ rfkill list all
stefano@EasyNote:~$ lsmod | grep "ath5k"
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211
stefano@EasyNote:~$ dmesg | grep "ath5k"
[   25.009926] ath5k 0000:00:06.0: enabling device (0000 -> 0002)
[   25.009942] ath5k 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   25.010025] ath5k 0000:00:06.0: registered as 'phy0'
[   25.010033] ath5k phy0: request_irq failed
[   25.010062] ath5k: probe of 0000:00:06.0 failed with error -16
stefano@EasyNote:~$ 

```Thank you in advance.

---

### Post by jst65 on 2012-07-08
I would blame these lines:

```
[   25.009942] ath5k 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   25.010025] ath5k 0000:00:06.0: registered as 'phy0'
[   25.010033] ath5k phy0: request_irq failed
```

Still don't know what to do. Please help

---

### Post by praseodym on 2012-07-08
Hi,

deactivate the hardware encryption of the driver:

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
```
Reboot, or reload the driver:

```
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
Check afterwards:
```
route -n
iwconfig wlan0
ifconfig wlan0
sudo iwlist scan
cat /etc/resolv.conf
```

---

### Post by billyb0b on 2012-07-11
Thanks a lot! 
It worked for my Atheros AR5213A (PCMCIA) on Xubuntu 12.04.

```

cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux nb2 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 i686 i386 GNU/Linux

 dmesg | grep "ath5k"
[   94.916488] ath5k 0000:04:00.0: enabling device (0000 -> 0002)
[   94.916518] ath5k 0000:04:00.0: PCI INT A -> Link[C0C9] -> GSI 10 (level, low) -> IRQ 10
[   94.916636] ath5k 0000:04:00.0: registered as 'phy0'
[   95.431147] ath5k phy0: Atheros AR5213A chip found (MAC: 0x59, PHY: 0x43)
[   95.431153] ath5k phy0: RF5112B multiband radio found (0x36)

```The only issue I have with this PCMCIA wifi card is, that I need to re-plug it after each (re)boot. Otherwise it cannot be found with lshw -c network, ifconfig or iwconfig.
Does anyone know how to get this solved?

Thanks!
b0b

---

### Post by praseodym on 2012-07-11
Try to reset the BIOS to default settings.

---

### Post by billyb0b on 2012-07-11
I already tried it without success. The bios version of this notebook is also uptodate.
My nb has two PCMCIA slots. After a reboot I need to change the PCMCIA slot to get the card working. It doesn't help to use the same slot.

```

dmesg | grep pcmcia
[   11.674158] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [io  0x4000-0x4fff]
[   11.674164] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x4fff: excluding 0x4000-0x40ff 0x4400-0x44ff 0x4800-0x48ff 0x4c00-0x4cff
[   11.707975] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [mem 0x90000000-0x901fffff]
[   11.707982] pcmcia_socket pcmcia_socket0: cs: memory probe 0x90000000-0x901fffff: excluding 0x90000000-0x9001ffff 0x90080000-0x9009ffff 0x90100000-0x9011ffff
[   11.708003] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [mem 0x24000000-0x2dffffff pref]
[   11.754593] pcmcia_socket pcmcia_socket0: cs: memory probe 0x24000000-0x2dffffff: excluding 0x24000000-0x2dffffff
[   11.921007] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge window: [io  0x4000-0x4fff]
[   11.921013] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x4fff: excluding 0x4000-0x40ff 0x4400-0x44ff
[   12.115255] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge window: [mem 0x90000000-0x901fffff]
[   12.115263] pcmcia_socket pcmcia_socket1: cs: memory probe 0x90000000-0x901fffff: excluding 0x90000000-0x9001ffff 0x90080000-0x9009ffff 0x90100000-0x9011ffff
[   12.115284] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge window: [mem 0x24000000-0x2dffffff pref]
[   12.115289] pcmcia_socket pcmcia_socket1: cs: memory probe 0x24000000-0x2dffffff: excluding 0x24000000-0x2dffffff
[   12.981096] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x100-0x107 0x140-0x14f 0x170-0x177 0x1f0-0x1f7 0x370-0x37f
[   12.982944] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3e8-0x3ff 0x4d0-0x4d7
[   12.983664] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   12.984643] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   12.985339] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   12.985379] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa01fffff
[   12.985421] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   12.985458] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.990709] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x100-0x107 0x140-0x14f 0x170-0x177 0x1f0-0x1f7
[   13.493746] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x3e8-0x3ff 0x4d0-0x4d7
[   13.494466] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   13.495093] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   13.495792] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   13.495831] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa01fffff
[   13.506852] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: clean.
[   13.506893] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[  221.856151] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0


```

---

### Post by praseodym on 2012-07-11
Check
> lsmod
when it is not working.

---

### Post by billyb0b on 2012-07-12
lsmod when it is NOT working:

```

lsmod
Module                  Size  Used by
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                729591  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 38139  4 
snd_timer              28931  2 snd_pcm,snd_seq
bnep                   17830  2 
pcmcia                 39791  0 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
snd                    62064  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87213  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
irda                  185517  0 
serio_raw              13027  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13199  1 radeon
crc_ccitt              12595  1 irda
parport_pc             32114  1 
shpchp                 32325  0 
video                  19068  0 
wmi                    18744  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
tg3                   137273  0 
floppy                 60310  0 


```lsmod when it IS working

```

Module                  Size  Used by
arc4                   12473  2 
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                729591  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 38139  4 
snd_timer              28931  2 snd_pcm,snd_seq
bnep                   17830  2 
pcmcia                 39791  0 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
snd                    62064  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87213  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
irda                  185517  0 
serio_raw              13027  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13199  1 radeon
crc_ccitt              12595  1 irda
parport_pc             32114  1 
shpchp                 32325  0 
video                  19068  0 
wmi                    18744  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
tg3                   137273  0 
floppy                 60310  0 


```For what ever reason the ath5k module is not loaded after a (re)boot.

---

### Post by billyb0b on 2012-07-12
I think this is a hardware / bios / firmware related issue. 

I just recognized that the issue only occurs if I REboot the notebook. If I do a cold start of the nb, the ath5k module is loaded directly and wifi is available.

---

### Post by praseodym on 2012-07-13
Force the module to load at boot-up:

> echo ath5k | sudo tee -a /etc/modules

---

### Post by billyb0b on 2012-07-13
No, it doesn't work either.

Here my modified /etc/modules

```

cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp





ath5k


```lsmod after changing the /etc/modules and reboot:
```

Module                  Size  Used by
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
radeon                729591  2 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rfcomm                 38139  4 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
pcmcia                 39791  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
ttm                    65344  1 radeon
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
snd                    62064  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87213  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              13027  0 
irda                  185517  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13199  1 radeon
parport_pc             32114  1 
crc_ccitt              12595  1 irda
shpchp                 32325  0 
video                  19068  0 
ath5k                 145127  0 
wmi                    18744  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
tg3                   137273  0 
floppy                 60310  0 


```lsmod after changing the /etc/modules, reboot and then plug in-out the PCMCIA card:
```

Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
radeon                729591  2 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rfcomm                 38139  4 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
pcmcia                 39791  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
ttm                    65344  1 radeon
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
snd                    62064  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87213  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              13027  0 
irda                  185517  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13199  1 radeon
parport_pc             32114  1 
crc_ccitt              12595  1 irda
shpchp                 32325  0 
video                  19068  0 
ath5k                 145127  0 
wmi                    18744  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
tg3                   137273  0 
floppy                 60310  0 

```

---

### Post by jst65 on 2012-07-16
Thank you for your replies.

I eventually got it to work even if none of the suggestions worked for me (I'm the OP), but still have some problems I am going to explain.

[I]First of all I have to tell you that in the meantime I switched to Mint 11, which AFAIK is, or was, based on Ubuntu.
I think there are no differences in dealing with this problem and I also wanted to keep track on this thread instead of dropping it and open another one on Mint forum.
If I am doing wrong please just tell me and don't forget I am a novice Linux user.[/I]

After some more research in the forum I just put **acpi=force** option in kernel boot and now it works.
Seems like I have also disabled USB ports this way - maybe there is a better option to use, I will face this problem later.

Now wifi works, but I have serious "disconnect/reconnect" issues as soon as I transfer data (copying files on the NAS, doing a sudo apt-get update...).

Here you can see what happens: these events keep repeating over and over.

```
Jul 15 23:26:25 EasyNote wpa_supplicant[710]: CTRL-EVENT-CONNECTED - Connection 
to 00:0c:f6:db:21:c8 completed (reauth) [id=0 id_str=]
Jul 15 23:26:25 EasyNote NetworkManager[561]: <info> (wlan0): supplicant 
connection state:  4-way handshake -> group handshake
Jul 15 23:26:25 EasyNote NetworkManager[561]: <info> (wlan0): supplicant 
connection state:  group handshake -> completed
Jul 15 23:26:27 EasyNote wpa_supplicant[710]: CTRL-EVENT-DISCONNECTED bssid=00:
0c:f6:db:21:c8 reason=0
Jul 15 23:26:27 EasyNote NetworkManager[561]: <info> (wlan0): supplicant 
connection state:  completed -> disconnected
Jul 15 23:26:27 EasyNote kernel: [ 3636.552087] wlan0: deauthenticated from 00:
0c:f6:db:21:c8 (Reason: 3)
Jul 15 23:26:27 EasyNote kernel: [ 3636.552469] cfg80211: All devices are 
disconnected, going to restore regulatory settings
Jul 15 23:26:27 EasyNote kernel: [ 3636.552475] cfg80211: Restoring regulatory 
settings
Jul 15 23:26:27 EasyNote kernel: [ 3636.552483] cfg80211: Calling CRDA to 
update world regulatory domain
Jul 15 23:26:27 EasyNote kernel: [ 3636.563152] cfg80211: Ignoring regulatory 
request Set by core since the driver uses its own custom regulatory domain 
Jul 15 23:26:27 EasyNote kernel: [ 3636.563164] cfg80211: World regulatory 
domain updated:
Jul 15 23:26:27 EasyNote kernel: [ 3636.563167] cfg80211:     (start_freq - 
end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 15 23:26:27 EasyNote kernel: [ 3636.563172] cfg80211:     (2402000 KHz - 
2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 15 23:26:27 EasyNote kernel: [ 3636.563177] cfg80211:     (2457000 KHz - 
2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 15 23:26:27 EasyNote kernel: [ 3636.563182] cfg80211:     (2474000 KHz - 
2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 15 23:26:27 EasyNote kernel: [ 3636.563186] cfg80211:     (5170000 KHz - 
5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 15 23:26:27 EasyNote kernel: [ 3636.563191] cfg80211:     (5735000 KHz - 
5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 15 23:26:27 EasyNote NetworkManager[561]: <info> (wlan0): supplicant 
connection state:  disconnected -> scanning
Jul 15 23:26:28 EasyNote wpa_supplicant[710]: Trying to associate with 00:0c:
f6:db:21:c8 (SSID='SitecomDB21C8' freq=2442 MHz)
Jul 15 23:26:28 EasyNote NetworkManager[561]: <info> (wlan0): supplicant 
connection state:  scanning -> associating
Jul 15 23:26:28 EasyNote kernel: [ 3637.404864] wlan0: authenticate with 00:0c:
f6:db:21:c8 (try 1)
Jul 15 23:26:28 EasyNote kernel: [ 3637.406395] wlan0: authenticated
Jul 15 23:26:28 EasyNote kernel: [ 3637.406467] wlan0: associate with 00:0c:f6:
db:21:c8 (try 1)
Jul 15 23:26:28 EasyNote kernel: [ 3637.410082] wlan0: RX AssocResp from 00:0c:
f6:db:21:c8 (capab=0xc31 status=0 aid=1)
Jul 15 23:26:28 EasyNote kernel: [ 3637.410090] wlan0: associated
Jul 15 23:26:28 EasyNote NetworkManager[561]: <info> (wlan0): supplicant 
connection state:  associating -> associated
Jul 15 23:26:28 EasyNote wpa_supplicant[710]: Associated with 00:0c:f6:db:21:
c8
Jul 15 23:26:29 EasyNote NetworkManager[561]: <info> (wlan0): supplicant 
connection state:  associated -> 4-way handshake
Jul 15 23:26:29 EasyNote wpa_supplicant[710]: WPA: Key negotiation completed 
with 00:0c:f6:db:21:c8 [PTK=CCMP GTK=CCMP]
Jul 15 23:26:29 EasyNote wpa_supplicant[710]: CTRL-EVENT-CONNECTED - 
Connection to 00:0c:f6:db:21:c8 completed (reauth) [id=0 id_str=]
Jul 15 23:26:29 EasyNote NetworkManager[561]: <info> (wlan0): supplicant 
connection state:  4-way handshake -> group handshake
Jul 15 23:26:29 EasyNote NetworkManager[561]: <info> (wlan0): supplicant 
connection state:  group handshake -> completed
Jul 15 23:26:32 EasyNote wpa_supplicant[710]: CTRL-EVENT-DISCONNECTED
```

Thank you

---

### Post by ergosteur on 2012-11-07
> **praseodym said:**
> Hi,

deactivate the hardware encryption of the driver:

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
```
Reboot, or reload the driver:

```
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
Check afterwards:
```
route -n
iwconfig wlan0
ifconfig wlan0
sudo iwlist scan
cat /etc/resolv.conf
```
Thanks, disabling the hardware encryption worked for me.

---

