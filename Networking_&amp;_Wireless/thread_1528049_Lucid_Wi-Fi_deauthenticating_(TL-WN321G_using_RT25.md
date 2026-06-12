---
title: "Lucid Wi-Fi deauthenticating (TL-WN321G using RT2501USB)"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by teilnehmer on 2010-07-10
Hi everyone, 

I suffer from the same problem as many other users: my wi-fi speed occasionally drops to a crawl with no obvious cause. I tried Wicd as an alternative to Network-Manager and didn't find it changing a thing. As an official fix is not yet underway, and as I saw other people trying their luck with individual solutions, I thought I'd give it a try. 

I use a TP-Link **TL-WN321G** (usb device) that is [listed]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB") as working. 
As output from lsusb I get the RT2501USB driver. 
```

~# lsusb // clipped output
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

```

I attach other important outputs below. 

Is it possible that I'm not using the correct driver? I'd prefer to not use a proprietary one, but if it's necessary to force Ubuntu to use another open one, I'd be willing to try that. 
My router uses WPA+WPA2 security. 

If you think I should just wait for the official fix, I'll happily oblige - it's just that I'd really like decent and reliable wi-fi as soon as possible. 

Thank you!

Jan

[COLOR="DarkOrchid"]UPDATE[/COLOR]: I played around with network-manager (uninstalling, manually editing /etc/network/interfaces, failing that reinstalling network-manager) and during restart I saw the following messages: 
```

[   11.474201] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   11.474391] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   11.474658] usbcore: registered new interface driver rt2500usb

```

-- 
```

~# lsmod
Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
snd_hda_codec_nvhdmi     3840  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203310  1 
arc4                    1153  2 
snd_hda_intel          21941  2 
snd_hda_codec          74201  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
rt73usb                21938  0 
crc_itu_t               1371  1 rt73usb
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2500usb              17768  0 
rt2x00usb               9694  2 rt73usb,rt2500usb
rt2x00lib              26858  3 rt73usb,rt2500usb,rt2x00usb
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               2864  1 rt2x00lib
compat_firmware_class     6554  1 rt2x00lib
vga16fb                11385  0 
vgastate                8961  1 vga16fb
mac80211              225171  2 rt2x00usb,rt2x00lib
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
soundcore               6620  1 snd
nvidia               9961216  38 
cfg80211              144682  2 rt2x00lib,mac80211
usbhid                 36110  0 
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
hid                    67032  1 usbhid
psmouse                63245  0 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
usblp                  10481  0 
shpchp                 28820  0 
i2c_nforce2             5199  0 
agpgart                31724  1 nvidia
lp                      7028  0 
parport                32635  2 ppdev,lp
forcedeth              49556  0 
ahci                   32168  3 
uvesafb                22297  1 

```

```

~# iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"****scrambled****"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:24:FE:A4:F2:2A   
          Bit Rate=54 Mb/s   Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Also, in dmesg I sometimes get
```

~# dmesg | grep -i wlan0
[   15.112296] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.719318] wlan0: deauthenticating from 00:24:fe:a4:f2:2a by local choice (reason=3)
[   48.721744] wlan0: authenticate with 00:24:fe:a4:f2:2a (try 1)
[   48.726236] wlan0: authenticated
[   48.727982] wlan0: associate with 00:24:fe:a4:f2:2a (try 1)
[   48.736784] wlan0: RX AssocResp from 00:24:fe:a4:f2:2a (capab=0x411 status=0 aid=1)
[   48.736795] wlan0: associated
[   48.750770] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   59.364512] wlan0: no IPv6 routers present
[ 1133.981275] wlan0: deauthenticated from 00:24:fe:a4:f2:2a (Reason: 1)
[ 1135.390773] wlan0: authenticate with 00:24:fe:a4:f2:2a (try 1)
[ 1135.393814] wlan0: authenticated
[ 1135.395404] wlan0: associate with 00:24:fe:a4:f2:2a (try 1)
[ 1135.400694] wlan0: RX AssocResp from 00:24:fe:a4:f2:2a (capab=0x411 status=0 aid=1)
[ 1135.400705] wlan0: associated
[ 1882.905767] wlan0: deauthenticating from 00:24:fe:a4:f2:2a by local choice (reason=3)
[ 1887.528929] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1914.961288] wlan0: deauthenticating from 00:24:fe:a4:f2:2a by local choice (reason=3)
[ 1915.162722] wlan0: authenticate with 00:24:fe:a4:f2:2a (try 1)
[ 1915.166222] wlan0: authenticated
[ 1915.167697] wlan0: associate with 00:24:fe:a4:f2:2a (try 1)
[ 1915.173962] wlan0: RX AssocResp from 00:24:fe:a4:f2:2a (capab=0x411 status=0 aid=1)
[ 1915.173970] wlan0: associated
[ 1915.189715] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1926.008526] wlan0: no IPv6 routers present

```
On one occasion, I manually disabled the network to restart it. The other instances were not done by me.

---

