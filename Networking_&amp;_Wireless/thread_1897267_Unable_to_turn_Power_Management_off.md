---
title: "Unable to turn Power Management off"
date: 2011-12-18
forum: Networking &amp; Wireless
---

### Post by Reded on 2011-12-18
Hey all, yet another thread about the seemingly linux-proof Ralink 3060 Chipset.

After a lot of fiddling to make my Wireless card work, I've been getting power management-style issues with it. That is, whenever I do anything that takes more bandwidth (Watching videos on YouTube, Video calling, downloading large files) My wireless disconnects itself. With my old card, this could be fixed by doing iwconfig wlan0 power off. With this card, however, I get this message:

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device ra0 ; Operation not supported.

The driver for it requires compiling, and I've scoured the internet to make sure the .dat file is 100% right, as far as I can see. 

The thing is, this only happens in Network Manager. I've tried Wicd and that works beautifully, however when THAT disconnects (My internet disconnects occasionally anyway) It has a habit of freezing my entire computer up, so I've tried to steer clear of using that.

Usual list of commands off the sticky :-

lspci

01:07.0 Network controller: Ralink corp. RT3060 Wireless 802.11n 1T/1R

iwconfig

ra0       Ralink STA  ESSID:"ZyXEL_8376vik"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.472 GHz  Access Point: 00:02:CF:7F:60:00   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-39 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig

ra0       Link encap:Ethernet  HWaddr c8:3a:35:c7:42:a0  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca3a:35ff:fec7:42a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25709 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8750101 (8.7 MB)  TX bytes:3841896 (3.8 MB)
          Interrupt:17 


lsmod

Module                  Size  Used by
nls_iso8859_1          12713  2 
nls_cp437              16991  2 
vfat                   17585  2 
fat                    61475  1 vfat
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
vesafb                 13809  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
snd_hda_intel          33390  7 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
rt3562sta             927802  1 
edac_core              53746  0 
edac_mce_amd           23709  0 
snd_rawmidi            30547  1 snd_seq_midi
ppdev                  17113  0 
snd_seq_midi_event     14899  1 snd_seq_midi
k8temp                 13057  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2928969  205 
parport_pc             36962  1 
snd                    68266  22 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usb_storage            57901  2 
usbhid                 47198  0 
uas                    18027  0 
hid                    95463  1 usbhid
forcedeth              67563  0 
sata_nv                32305  0 
pata_amd               14121  2 


sudo lshw -C network

  *-network               
       description: Wireless interface
       product: RT3060 Wireless 802.11n 1T/1R
       vendor: Ralink corp.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: ra0
       version: 00
       serial: c8:3a:35:c7:42:a0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.0.0 ip=192.168.1.33 latency=32 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
       resources: irq:17 memory:fa000000-fa00ffff

iwlist scan

ra0       Scan completed :
          Cell 01 - Address: 00:02:CF:7F:60:00
                    Protocol:802.11b/g
                    ESSID:"ZyXEL_8376vik"
                    Mode:Managed
                    Frequency:2.472 GHz (Channel 13)
                    Quality:100/100  Signal level:-39 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


Ubuntu 11.10 64-bit, latest Kernel, though it's done it for the last two Kernel updates too.

Had nothing but issues with this card, but I think this is the last one that needs fixing, for now. Thanks for any responses, well appreciated as always!

---

### Post by Reded on 2011-12-18
Network manager also freezes the computer up when it reconnects after a disconnection now.

---

### Post by Reded on 2011-12-20
Bumping-had this issue for way too long, really hope for a fix that doesn't involve buying a new wireless card!

---

### Post by Reded on 2011-12-21
Not managed to fix this yet. Tried changing values in /usr/lib/pm-utils/power.d/wireless (Had instructions on another thread of mine), still getting it (With BOTH my Wireless Card and my Dongle now... Dongle gets iwconfig power off before I use it).

Starting to wonder whether it's computer or router now :(

---

### Post by Reded on 2011-12-29
Bumping, still not fixed this.

---

