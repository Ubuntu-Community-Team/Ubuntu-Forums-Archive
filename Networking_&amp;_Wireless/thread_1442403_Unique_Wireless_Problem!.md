---
title: "Unique Wireless Problem!"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by mrmoore on 2010-03-29
I am about dizzy digging through forums trying to solve this and while I have seen many many wireless probs, I haven't seen anything quite like this one.

I have 9.10 on an old Inspiron B130 and while I have been able to connect to many OTHER wireless routers I can't connect to MINE! lol

The router is encrypted (as are others I've connected to) and when I try to connect I can see good signal strength, there are a few packets received and sent and yet it never connects. Here is some info, maybe someone has an answer.

Oh, and did I mention that from time to time it WILL connect?! Not in a while though.

Mac's and other Windows PC's connect just fine.

Address: 00:23:69:58:56:FA
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

michael@michael-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
b44                    28652  0 
ssb                    35524  1 b44
ndiswrapper           185532  0 
snd_hda_codec_idt      59876  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
joydev                 10240  0 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
iptable_filter          3100  0 
arc4                    1660  0 
snd_seq_midi            6464  0 
ip_tables              11692  1 iptable_filter
ecb                     2524  0 
snd_rawmidi            22176  1 snd_seq_midi
x_tables               16544  1 ip_tables
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
dell_wmi                2564  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              181140  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               93052  1 mac80211
dell_laptop             8128  0 
psmouse                56500  0 
led_class               4096  0 
dcdbas                  7292  1 dell_laptop
serio_raw               5280  0 
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
lp                      8964  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
mii                     5212  1 b44
video                  19380  1 i915
output                  2780  1 video
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp

Threw the last in to see ndiswrapper which I've heard so much about. Need anymore info? Give me a holler!

Thanks all

Mike

---

### Post by kyletstrand on 2010-03-29
Are you able to bypass the router and get a decent connection hardwired?

>  Signal level:-47 dBm  Noise level:-96 dBm

These numbers seem a little low which might be causing the intermittent connection to your router.  Not sure about that at all really though.  I'm gonna look it up.

What's your ip address when you're connected to your network and when you're hardwired?

---

### Post by kyletstrand on 2010-03-30
Ok, Signal and noise should be good.  I was wrong in about that, but at least I learned something new.

---

### Post by mrmoore on 2010-03-30
> **kyletstrand said:**
> Are you able to bypass the router and get a decent connection hardwired?



These numbers seem a little low which might be causing the intermittent connection to your router.  Not sure about that at all really though.  I'm gonna look it up.

What's your ip address when you're connected to your network and when you're hardwired?


Yes, I can connect hardwired. I can't test the ip address right now, I will try tomorrow if you think it will help, as I said though, it does connect slightly for a short bit (tiny transfer of data). If I attempt to connect to an encrypted router without the right password there is no such transfer.

---

### Post by kyletstrand on 2010-03-30
Yeah, not sure, just thought maybe it could maybe offer some insight.

Have you tried uninstalling and reinstalling the drivers on this partition?

---

