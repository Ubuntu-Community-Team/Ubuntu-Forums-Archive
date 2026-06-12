---
title: "Incessant Wireless Disconnect/Reconnect"
date: 2011-04-10
forum: Networking &amp; Wireless
---

### Post by Bradley Rowe on 2011-04-10
Howdy,

I've been having difficulty diagnosing a problem I've been having w/ my wireless card.  Every ten seconds or so, my wireless connection drops and then reconnects again about 10 seconds later.  Sometimes it's more time, sometimes less, but most often around 10 seconds.  When connected, things are fine and just as fast as you'd expect.  Just this pattern of disconnect and reconnect.

I don't think it's interference from other networks or devices or generally crappy signal because other wireless devices in the house are working fine in exactly the same spot, I've moved the computer having trouble substantially closer to the AP w/ no change in this behavior (although signal quality goes up), and I've switched up the wireless channel.  Behavior persists.  I suppose it could be the card, although it's brand new.

I've noticed this bug#548992, and it seems like some people are reporting a similar behavior, but it doesn't seem quite it.

Anyway, I'm enclosing full documentation of the behavior below.  I'd appreciate if anyone could take a glance and offer an opinion.

Also, I've been working w/ Ubuntu for about a week now, so be gentle.

Thanks,

Brad
```

1) Machine Brand/Model

Dell Optiplex GX270 (Desktop/Tower)

2) Wireless Brand, Model and Wireless Chipset

01:0a.0 Network controller: RaLink RT2561/RT61 802.11g PCI
        Subsystem: Linksys WMP54G ver 4.1
 
3) Check Interface:

wlan0     IEEE 802.11bg  ESSID:"MY NETWORK NAME"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 68:7F:74:CA:6A:71
          Bit Rate=24 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4) Modules
Module                  Size  Used by
binfmt_misc             6599  1
snd_intel8x0           25664  2
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
arc4                    1165  2
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0
rt61pci                19187  0
crc_itu_t               1383  1 rt61pci
rt2x00pci               6029  1 rt61pci
i915                  295435  4
rt2x00lib              27307  2 rt61pci,rt2x00pci
snd_rawmidi            17783  1 snd_seq_midi
led_class               2633  1 rt2x00lib
snd_seq_midi_event      6047  1 snd_seq_midi
mac80211              231959  2 rt2x00pci,rt2x00lib
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
drm_kms_helper         30200  1 i915
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0
cfg80211              144694  2 rt2x00lib,mac80211
drm                   168060  4 i915,drm_kms_helper
parport_pc             26058  1
snd                    49038  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  5402  0
intel_agp              26566  2 i915
eeprom_93cx6            1345  1 rt61pci
soundcore                880  1 snd
i2c_algo_bit            5168  1 i915
shpchp                 29886  0
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
video                  18712  1 i915
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
lp                      7342  0
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0
e1000                  97525  0
hid                    67742  1 usbhid
floppy                 54311  0

5) Kernal boot messages

[266005.837418] wlan0: authenticate with 68:7f:74:ca:6a:71 (try 1)
[266005.839796] wlan0: authenticated
[266005.839857] wlan0: associate with 68:7f:74:ca:6a:71 (try 1)
[266005.842109] wlan0: RX AssocResp from 68:7f:74:ca:6a:71 (capab=0x411 status=0 aid=2)
[266005.842115] wlan0: associated
[266015.849802] wlan0: deauthenticating from 68:7f:74:ca:6a:71 by local choice (reason=3)
[266017.087957] wlan0: authenticate with 68:7f:74:ca:6a:71 (try 1)
[266017.089387] wlan0: authenticated
[266017.089414] wlan0: associate with 68:7f:74:ca:6a:71 (try 1)
[266017.091924] wlan0: RX AssocResp from 68:7f:74:ca:6a:71 (capab=0x411 status=0 aid=2)
[266017.091928] wlan0: associated
[266027.097978] wlan0: deauthenticating from 68:7f:74:ca:6a:71 by local choice (reason=3)
[266028.334883] wlan0: authenticate with 68:7f:74:ca:6a:71 (try 1)
[266028.336314] wlan0: authenticated
[266028.336340] wlan0: associate with 68:7f:74:ca:6a:71 (try 1)
[266028.338850] wlan0: RX AssocResp from 68:7f:74:ca:6a:71 (capab=0x411 status=0 aid=2)
[266028.338854] wlan0: associated
[266038.347295] wlan0: deauthenticating from 68:7f:74:ca:6a:71 by local choice (reason=3)
[266039.584058] wlan0: authenticate with 68:7f:74:ca:6a:71 (try 1)
[266039.585478] wlan0: authenticated
[266039.585502] wlan0: associate with 68:7f:74:ca:6a:71 (try 1)
[266039.588396] wlan0: RX AssocResp from 68:7f:74:ca:6a:71 (capab=0x411 status=0 aid=2)
[266039.588401] wlan0: associated

(...this goes on and on and on.  just a brief excerpt to give you a flavor...)

6) Network Configuration

  *-network:0
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: wlan0
       version: 00
       serial: 68:7f:74:69:76:64
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=2.6.35-28-generic firmware=N/A ip=192.168.1.98 latency=64 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:fead8000-feadffff
  *-network:1
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:13:72:a9:e5:05
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:18 memory:feae0000-feafffff ioport:df40(size=64)

7) Scan for Networks

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 68:7F:74:CA:6A:71
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=32/70  Signal level=-78 dBm
                    Encryption key:on
                    ESSID:"MY NETWORK NAME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009db7a83e53
                    Extra: Last beacon: 9908ms ago
                    IE: Unknown: 0009546865427269646765
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

8) Ubuntu Version

Description:    Ubuntu 10.10


9) Kernal

2.6.35-28-generic i686


10) Restart Network

 * Reconfiguring network interfaces...                                          
SIOCDELRT: No such process
ssh stop/waiting
ssh start/running, process 18719

11)  grep wlan0 SYSLOG

Apr  9 17:58:09 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr  9 17:58:09 Tank kernel: [239927.448053] wlan0: authenticate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:58:09 Tank kernel: [239927.449474] wlan0: authenticated
Apr  9 17:58:09 Tank kernel: [239927.449498] wlan0: associate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:58:09 Tank kernel: [239927.451999] wlan0: RX AssocResp from 68:7f:74:ca:6a:71 (capab=0x411 status=0 aid=1)
Apr  9 17:58:09 Tank kernel: [239927.452014] wlan0: associated
Apr  9 17:58:09 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr  9 17:58:09 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Apr  9 17:58:09 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Apr  9 17:58:09 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Apr  9 17:58:19 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Apr  9 17:58:19 Tank kernel: [239937.457116] wlan0: deauthenticating from 68:7f:74:ca:6a:71 by local choice (reason=3)
Apr  9 17:58:19 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 17:58:21 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr  9 17:58:21 Tank kernel: [239938.696493] wlan0: authenticate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:58:21 Tank kernel: [239938.697917] wlan0: authenticated
Apr  9 17:58:21 Tank kernel: [239938.697942] wlan0: associate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:58:21 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr  9 17:58:21 Tank kernel: [239938.700469] wlan0: RX AssocResp from 68:7f:74:ca:6a:71 (capab=0x411 status=0 aid=1)
Apr  9 17:58:21 Tank kernel: [239938.700474] wlan0: associated
Apr  9 17:58:21 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Apr  9 17:58:21 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Apr  9 17:58:21 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Apr  9 17:58:31 Tank kernel: [239948.705414] wlan0: deauthenticating from 68:7f:74:ca:6a:71 by local choice (reason=3)
Apr  9 17:58:31 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Apr  9 17:58:31 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 17:58:32 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr  9 17:58:32 Tank kernel: [239949.942064] wlan0: authenticate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:58:32 Tank kernel: [239949.943824] wlan0: authenticated
Apr  9 17:58:32 Tank kernel: [239949.943861] wlan0: associate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:58:32 Tank kernel: [239949.946101] wlan0: RX AssocResp from 68:7f:74:ca:6a:71 (capab=0x411 status=0 aid=1)
Apr  9 17:58:32 Tank kernel: [239949.946107] wlan0: associated
Apr  9 17:58:32 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr  9 17:58:32 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Apr  9 17:58:32 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Apr  9 17:58:32 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Apr  9 17:58:42 Tank kernel: [239959.954699] wlan0: deauthenticating from 68:7f:74:ca:6a:71 by local choice (reason=3)
Apr  9 17:58:42 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Apr  9 17:58:42 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 17:58:43 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr  9 17:58:43 Tank kernel: [239961.199214] wlan0: authenticate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:58:43 Tank kernel: [239961.200647] wlan0: authenticated
Apr  9 17:58:45 Tank NetworkManager[15618]: <info> (wlan0): roamed from BSSID 68:7F:74:CA:6A:71 (MY NETWORK NAME) to (none) ((none))
Apr  9 17:58:53 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr  9 17:58:53 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 17:58:54 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr  9 17:58:54 Tank kernel: [239972.441787] wlan0: authenticate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:58:54 Tank kernel: [239972.443209] wlan0: authenticated
Apr  9 17:58:54 Tank kernel: [239972.443235] wlan0: associate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:58:54 Tank kernel: [239972.445801] wlan0: RX AssocResp from 68:7f:74:ca:6a:71 (capab=0x411 status=0 aid=1)
Apr  9 17:58:54 Tank kernel: [239972.445806] wlan0: associated
Apr  9 17:58:54 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr  9 17:58:54 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Apr  9 17:58:54 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Apr  9 17:58:54 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Apr  9 17:58:57 Tank NetworkManager[15618]: <info> (wlan0): roamed from BSSID (none) ((none)) to 68:7F:74:CA:6A:71 (MY NETWORK NAME)
Apr  9 17:59:04 Tank kernel: [239982.454883] wlan0: deauthenticating from 68:7f:74:ca:6a:71 by local choice (reason=3)
Apr  9 17:59:04 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Apr  9 17:59:04 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 17:59:06 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr  9 17:59:06 Tank kernel: [239983.695913] wlan0: authenticate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:59:06 Tank kernel: [239983.697342] wlan0: authenticated
Apr  9 17:59:06 Tank kernel: [239983.697369] wlan0: associate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:59:06 Tank kernel: [239983.699920] wlan0: RX AssocResp from 68:7f:74:ca:6a:71 (capab=0x411 status=0 aid=1)
Apr  9 17:59:06 Tank kernel: [239983.699924] wlan0: associated
Apr  9 17:59:06 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr  9 17:59:06 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Apr  9 17:59:06 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Apr  9 17:59:06 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Apr  9 17:59:16 Tank kernel: [239993.703174] wlan0: deauthenticating from 68:7f:74:ca:6a:71 by local choice (reason=3)
Apr  9 17:59:16 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Apr  9 17:59:16 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 17:59:17 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr  9 17:59:17 Tank kernel: [239994.941380] wlan0: authenticate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:59:17 Tank kernel: [239994.943743] wlan0: authenticated
Apr  9 17:59:17 Tank kernel: [239994.943805] wlan0: associate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:59:17 Tank kernel: [239994.946059] wlan0: RX AssocResp from 68:7f:74:ca:6a:71 (capab=0x411 status=0 aid=1)
Apr  9 17:59:17 Tank kernel: [239994.946065] wlan0: associated
Apr  9 17:59:17 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr  9 17:59:17 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Apr  9 17:59:17 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Apr  9 17:59:17 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Apr  9 17:59:27 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Apr  9 17:59:27 Tank kernel: [240004.952547] wlan0: deauthenticating from 68:7f:74:ca:6a:71 by local choice (reason=3)
Apr  9 17:59:27 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 17:59:28 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr  9 17:59:28 Tank kernel: [240006.193535] wlan0: authenticate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:59:28 Tank kernel: [240006.194959] wlan0: authenticated
Apr  9 17:59:28 Tank kernel: [240006.194984] wlan0: associate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:59:28 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr  9 17:59:28 Tank kernel: [240006.197551] wlan0: RX AssocResp from 68:7f:74:ca:6a:71 (capab=0x411 status=0 aid=1)
Apr  9 17:59:28 Tank kernel: [240006.197555] wlan0: associated
Apr  9 17:59:28 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Apr  9 17:59:28 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Apr  9 17:59:28 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Apr  9 17:59:38 Tank kernel: [240016.202286] wlan0: deauthenticating from 68:7f:74:ca:6a:71 by local choice (reason=3)
Apr  9 17:59:38 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Apr  9 17:59:38 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 17:59:39 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr  9 17:59:39 Tank kernel: [240017.440481] wlan0: authenticate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:59:39 Tank kernel: [240017.441901] wlan0: authenticated
Apr  9 17:59:39 Tank kernel: [240017.441927] wlan0: associate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:59:39 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr  9 17:59:39 Tank kernel: [240017.444460] wlan0: RX AssocResp from 68:7f:74:ca:6a:71 (capab=0x411 status=0 aid=1)
Apr  9 17:59:39 Tank kernel: [240017.444465] wlan0: associated
Apr  9 17:59:39 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Apr  9 17:59:39 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Apr  9 17:59:39 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Apr  9 17:59:49 Tank kernel: [240027.451143] wlan0: deauthenticating from 68:7f:74:ca:6a:71 by local choice (reason=3)
Apr  9 17:59:49 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Apr  9 17:59:49 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 17:59:51 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr  9 17:59:51 Tank kernel: [240028.688771] wlan0: authenticate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:59:51 Tank kernel: [240028.690229] wlan0: authenticated
Apr  9 17:59:51 Tank kernel: [240028.690265] wlan0: associate with 68:7f:74:ca:6a:71 (try 1)
Apr  9 17:59:51 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr  9 17:59:51 Tank kernel: [240028.692803] wlan0: RX AssocResp from 68:7f:74:ca:6a:71 (capab=0x411 status=0 aid=1)
Apr  9 17:59:51 Tank kernel: [240028.692808] wlan0: associated
Apr  9 17:59:51 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Apr  9 17:59:51 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Apr  9 17:59:51 Tank NetworkManager[15618]: <info> (wlan0): supplicant connection state:  group handshake -> completed

(...again, a short excerpt)
                                                                         [ OK ]

```

---

### Post by Bradley Rowe on 2011-04-12
Thought I'd bump this thread just to make sure a few more eyes got a chance to see this thread.

---

### Post by aschweig on 2011-05-18
I had some wireless problems that I eventually solved. Don't know if it will help you:

[http://ubuntuforums.org/showthread.php?t=1753298](http://ubuntuforums.org/showthread.php?t=1753298)

---

### Post by Bradley Rowe on 2011-05-19
Hey,

Thanks for your reply.  Unfortunately (or fortunately), I gave up on this issue some time back and just setup a wired connection.  It's less than ideal, but it's acceptable for the time being.

Brad

---

