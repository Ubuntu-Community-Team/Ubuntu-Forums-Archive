---
title: "Wireless + Karmic = no go"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by razta on 2009-12-02
Hello all,
Just taken the plunge and completely moved away from Windows by installing Ubuntu on my main machine.

Wireless USB NIC has been recognized out of the box. The only problem is, is when I try to connect to my wireless AP, I enter my WPA TKIP password and after a while it asks me again. I tried WPA AES and same thing.

Any ideas? 

iwconfig output:
```

wlan0     IEEE 802.11bgn  Mode:Managed  Frequency:2.437 GHz  
          Access Point: Not-Associated   Tx-Power=12 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


``` 

Thanks in advance.

---

### Post by Gerhardus on 2009-12-03
I too am having a similar issue. My laptop works fine running UNR, but another laptop I have with a broken screen I decided to turn into a mythbox is able to find my wireless network but the wpa won't authenticate. After weeks of trying I ended up setting it aside to take a break from my frustration.... I then through a desktop system together, and taking a wireless card that is in an old system I now use as a server and putting in this, even this card isn't working.... The card that I put into this desktop I had working when running ubuntu 8.10 on the system I now use as a server, I don't understand how a card that used to work wouldn't continue to do so.

I'm running wpa-psk for authentication

in my logs I'm getting a message at the attempts that says

wpa_supplicant[954]:Association request to the driver failed

it's the only thing that seems to make sense to me as to a reason for not connecting

---

### Post by peepingtom on 2009-12-03
USB adapter guy: post output of lsusb and lsmod

PCI guy: lspci and lsmod . Do you mean server as in "Ubuntu Server" and you use SSH to administer it?

neither of you told us what wifi card or driver you used, the commands I just listed will tell us that.

---

### Post by razta on 2009-12-03
lusb:
```
ryan@ryan-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 002: ID 04f2:0618 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 002: ID 0df6:0017 Sitecom Europe B.V. WL-182
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsmod:
```
ryan@ryan-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
snd_hda_codec_nvhdmi     4828  1 
snd_hda_codec_realtek   203328  1 
rt2870sta             488820  0 
arc4                    1660  2 
ecb                     2524  2 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
input_polldev           3716  1 rt2x00lib
mac80211              181236  2 rt2x00usb,rt2x00lib
iptable_filter          3100  0 
cfg80211               93052  2 rt2x00lib,mac80211
crc_ccitt               1852  1 rt2800usb
joydev                 10272  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
psmouse                56500  0 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
serio_raw               5280  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
nvidia               9586440  36 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
agpgart                34988  1 nvidia
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
acer_wmi               15936  0 
led_class               4096  2 rt2x00lib,acer_wmi
k8temp                  4188  0 
shpchp                 32272  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
btusb                  11856  2 
sbp2                   22888  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
i2c_nforce2             6784  0 
usb_storage            52576  0 
usbhid                 38208  0 
video                  19380  0 
output                  2780  1 video
ohci1394               29900  0 
ieee1394               86596  2 sbp2,ohci1394
forcedeth              54152  0 

```

end of dmesg:
```
[   23.623412] wlan0: authenticated
[   23.623415] wlan0: associate with AP 00:40:10:20:00:03
[   23.625779] wlan0: RX AssocResp from 00:40:10:20:00:03 (capab=0x411 status=0 aid=1)
[   23.625782] wlan0: associated
[   23.635225] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.812009] eth0: no IPv6 routers present
[   34.424012] wlan0: no IPv6 routers present
[   68.940578] wlan0: disassociating by local choice (reason=3)
[   78.000023] Clocksource tsc unstable (delta = -261716983 ns)
[  725.697838] wlan0: authenticate with AP 00:40:10:20:00:03
[  725.699850] wlan0: authenticated
[  725.699855] wlan0: associate with AP 00:40:10:20:00:03
[  725.702107] wlan0: RX AssocResp from 00:40:10:20:00:03 (capab=0x411 status=0 aid=1)
[  725.702114] wlan0: associated
[  770.963056] wlan0: disassociating by local choice (reason=3)
[ 1111.097349] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

Some things I tried:
Using WEP
Setting SSID manually
Setting IP manually

Any help is much appreciated,
Thank you.

---

### Post by linux6994 on 2009-12-03
I had the same troubles, with multiple load attempts and cards. I ended up loading Linux Mint 8 which is Karmic based and all is well. Just a thought.

---

### Post by Gerhardus on 2009-12-03
The server I'm running is ubuntu and remotely administered through ssh.... but that's not where the wireless card is. The wireless card was in the box that I now use as a server, but when it was a desktop running 8.10 the wireless worked. I just put the card into a different pc, running desktop 8.10, and the wireless isn't working... eventually I'm going to convert it to a mythbox, but for now just want wireless working on it... before I do.

the driver listed in lspci is

05:09.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

and the lsmod iformation I got is

Module                  Size  Used by
binfmt_misc             8356  1 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
arc4                    1660  2 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
ecb                     2524  2 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0 
ath5k                 124260  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
mac80211              181236  1 ath5k
led_class               4096  1 ath5k
ath                     8060  1 ath5k
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211               93052  3 ath5k,mac80211,ath
soundcore               7264  1 snd
shpchp                 32272  0 
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
ppdev                   6688  0 
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
psmouse                56500  0 
serio_raw               5280  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
e100                   32452  0 
mii                     5212  1 e100
floppy                 54916  0 
i915                  221064  2 
drm                   159584  2 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video


The Card can see my network, but doesn't seem to be able to authenticate.

Thank you for your time.

---

### Post by ComputerHermit on 2009-12-03
Welcome to my world 

[http://ubuntuforums.org/showthread.php?t=1342259](http://ubuntuforums.org/showthread.php?t=1342259)

I went back to 8.10 this is my 
Ubuntu testimonial & experience

---

### Post by bones16v on 2009-12-03
My wireless doesn't work at all. This started the day before I upgraded, but it only worked half the time.  Now it doesn't work at all, except like twice in the last week it came on while I was connected with ethernet.  HELP?

---

