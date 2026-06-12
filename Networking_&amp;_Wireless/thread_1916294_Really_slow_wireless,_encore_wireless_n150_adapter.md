---
title: "Really slow wireless, encore wireless n150 adapter"
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by pandalolwut on 2012-01-27
I just put lubuntu 11.1 on my old desktop (a dell dimension 3000), but when I put in my wireless usb adapter (encore wireless n150 usb adapter), I'm getting really slow internet speeds. It takes anywhere from 20 secs - 5 minutes for me to open google news. Also, if I go to network connections, and edit my connection, the connection is completely lost, and it doesn't reconnect until I restart.
Anyone got any ideas?

---

### Post by pandalolwut on 2012-01-28
Solved my issue, for anyone who encounters similar issues:


[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)


method 3 of this seems to have worked :)

---

### Post by pandalolwut on 2012-01-28
ok, so my joy was a little premature. I rebooted, and again I cant only connect for a bit (usually enough for one webpage),  and then the connection times out each time. The wireless icon is still there, but I can't actually go to any web page. I also can't connect to servers when I try to install stuff through apt-get.

I guess I should post some more information:

Computer model:
Dell Dimension 3000

ubuntu version-
lubuntu, ubuntu 11.1

kernel-
3.0.0-12-generic i686

lsusb-
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
Bus 001 Device 007: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 001 Device 005: ID 05e3:0607 Genesys Logic, Inc. 
Bus 003 Device 002: ID 03f0:0f0c Hewlett-Packard Wireless Keyboard and Optical Mouse receiver
Bus 001 Device 006: ID 046d:0a0e Logitech, Inc. 

ifconfig-
eth0      Link encap:Ethernet  HWaddr 00:11:11:89:b7:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100815 (100.8 KB)  TX bytes:100815 (100.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:e0:4c:9f:6f:a7  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:413 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1667 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:313159 (313.1 KB)  TX bytes:155814 (155.8 KB)

iwconfig-
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"MMWireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:5D:F3:82   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:37   Missed beacon:0



lsmod-
Module                  Size  Used by
arc4                   12473  2 
rfcomm                 38408  0 
ppdev                  12849  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
snd_intel8x0           33318  1 
snd_usb_audio         100880  1 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
dcdbas                 14098  0 
snd_pcm                80468  3 snd_intel8x0,snd_usb_audio,snd_ac97_codec
snd_hwdep              13276  1 snd_usb_audio
snd_usbmidi_lib        24558  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rtl8192cu              97651  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95614  1 rtl8192cu
mac80211              272785  3 rtl8192cu,rtl8192c_common,rtlwifi
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172392  2 rtlwifi,mac80211
snd                    55902  14 snd_intel8x0,snd_usb_audio,snd_ac97_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 41905  0 
hid                    77367  1 usbhid
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i915                  505108  2 
shpchp                 32356  0 
parport_pc             32114  1 
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
ums_cypress            12627  0 
usb_storage            44173  2 ums_cypress
uas                    17699  0 
e100                   36289  0 
floppy                 60310  0 


iwlist scan-
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:5D:F3:82
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"MMWireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001d17f3185
                    Extra: Last beacon: 1881204ms ago
                    IE: Unknown: 000A4D4D576972656C657373
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

---

