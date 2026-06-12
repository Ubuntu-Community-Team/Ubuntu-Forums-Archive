---
title: "Reconnecting to Wireless freezes computer"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by Reded on 2011-11-16
Hey all,

I'm using a Ralink RT3060, and occasionally my Wireless disconnects. It doesn't show it disconnecting in the Network manager (All 4 bars stay nicely lit) But all my online programs go offline. My usual fix is to press disconnect, then reconnect it.

But recently when I do this, I click the network to connect to. First thing, two of them appear (With the same name) And after discovering one of them doesn't work I click the other, which is when my computer freezes up completely, mouse cursor and everything.

Now, two networks appear in network manager (both of the same name, my router). One of them is a WEP network (I stopped using WEP a good few weeks ago), the other is a WPA one. It's the WEP one that freezes me up.

Now, when I use the WPA one, my wireless disconnects everytime I actually do anything to use it - Skype video calling (Screenshare or webcam), downloading, watching an HD YouTube video all disconnect my internet within a few minutes.

I've tried the iwconfig power off command, it just returns this -

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device ra0 ; Operation not supported.

My USB dongle disconnects in the same way too, and the power management off has been done, I've even editted the power.d/wireless file for both ra0 and wlan1 (ra0 being my wireless card, wlan1 being my USB dongle). Still not fixed.

I'll post all the commands off the sticky :-

lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
snd_hrtimer            12744  1 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
vesafb                 13809  1 
snd_hda_codec_hdmi     32040  1 
binfmt_misc            17540  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  7 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  3 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rt3562sta             990799  1 
fglrx                2929009  225 
ppdev                  17113  0 
snd                    68266  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             36962  1 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
k8temp                 13057  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usb_storage            57901  1 
uas                    18027  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
forcedeth              67563  0 
sata_nv                32305  0 
pata_amd               14121  2 

lspci
01:07.0 Network controller: Ralink corp. RT3060 Wireless 802.11n 1T/1R

iwconfig
ra0       Ralink STA  ESSID:"ZyXEL_8376vik"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:02:CF:7F:60:00   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-53 dBm  Noise 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig

ra0       Link encap:Ethernet  HWaddr c8:3a:35:c7:42:a0  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca3a:35ff:fec7:42a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6728814 (6.7 MB)  TX bytes:4398357 (4.3 MB)
          Interrupt:17 

sudo lshw -C Network

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
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.1.1 ip=192.168.1.34 latency=32 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
       resources: irq:17 memory:fa000000-fa00ffff

sudo iwlist scan
ra0       Scan completed :
          Cell 01 - Address: 00:02:CF:7F:60:00
                    Protocol:802.11b/g
                    ESSID:"ZyXEL_8376vik"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-47 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

Ubuntu 11.10 64-Bit.

Thanks for any replies!

---

### Post by Reded on 2011-11-19
Recently it's decided to start disconnecting whenever I use my bandwith (Downloading, Skype Video calling) And two Networks appear in the manager (Both my ZyXel router...) Which is just confusing me even more.

---

### Post by Reded on 2011-11-20
Trying to keep this bumped, getting very annoyed with this wireless issue!

---

### Post by Reded on 2011-11-25
Haven't had a fix for this yet. Mostly the issue of disconnecting when I video-call or even (As I discovered yesterday) Watch a HD video on youtube.

---

### Post by Reded on 2011-11-25
It seems the second network that appears in network manager is a WEP network (One I used before I switched over to WPA a few weeks ago). It's THAT network that causes my computer to freeze.

Disconnection problem is still here though.

---

### Post by Reded on 2011-11-29
Still not fixed Am I doomed to switching to my USB dongle just to do certain things...?

---

### Post by Reded on 2011-11-29
This message appears in dmesg.txt when I disconnect. Maybe this'll help towards a fix.

[161657.004814] SCANNING, suspend MSDU transmission ...
[161657.006901] MlmeScanReqAction -- Send PSM Data frame for off channel RM, SCAN_IN_PROGRESS=1!
[161657.025043] SYNC - BBP R4 to 20MHz.l
[161657.027145] RT35xx: SwitchChannel#1(RF=8, Pwr0=4, Pwr1=5, 1T), N=0xF1, K=0x02, R=0x02
[161657.170118] RT35xx: SwitchChannel#2(RF=8, Pwr0=4, Pwr1=5, 1T), N=0xF1, K=0x07, R=0x02
[161657.314124] RT35xx: SwitchChannel#3(RF=8, Pwr0=4, Pwr1=5, 1T), N=0xF2, K=0x02, R=0x02
[161657.458134] RT35xx: SwitchChannel#4(RF=8, Pwr0=4, Pwr1=5, 1T), N=0xF2, K=0x07, R=0x02
[161657.602126] RT35xx: SwitchChannel#5(RF=8, Pwr0=4, Pwr1=5, 1T), N=0xF3, K=0x02, R=0x02
[161657.746122] RT35xx: SwitchChannel#6(RF=8, Pwr0=4, Pwr1=5, 1T), N=0xF3, K=0x07, R=0x02
[161657.890126] RT35xx: SwitchChannel#7(RF=8, Pwr0=1, Pwr1=5, 1T), N=0xF4, K=0x02, R=0x02
[161658.034127] RT35xx: SwitchChannel#11(RF=8, Pwr0=1, Pwr1=5, 1T), N=0xF6, K=0x02, R=0x02
[161658.036261] SYNC - End of SCAN, restore to channel 11, Total BSS[02]
[161658.036271] ScanNextChannel -- Send PSM Data frame
[161658.036273] bFastRoamingScan ~~~~~~~~~~~~~ Get back to send data ~~~~~~~~~~~~~
[161658.036279] SCAN done, resume MSDU transmission ...
[161658.938088] bImprovedScan ............. Resume for bImprovedScan, SCAN_PENDING .............. 
[161658.938098] SCANNING, suspend MSDU transmission ...
[161658.940170] MlmeScanReqAction -- Send PSM Data frame for off channel RM, SCAN_IN_PROGRESS=1!
[161658.961043] SYNC - BBP R4 to 20MHz.l
[161658.963142] RT35xx: SwitchChannel#8(RF=8, Pwr0=1, Pwr1=5, 1T), N=0xF4, K=0x07, R=0x02
[161659.106121] RT35xx: SwitchChannel#9(RF=8, Pwr0=1, Pwr1=5, 1T), N=0xF5, K=0x02, R=0x02
[161659.250126] RT35xx: SwitchChannel#10(RF=8, Pwr0=1, Pwr1=5, 1T), N=0xF5, K=0x07, R=0x02
[161659.394122] RT35xx: SwitchChannel#11(RF=8, Pwr0=1, Pwr1=5, 1T), N=0xF6, K=0x02, R=0x02
[161659.396277] ScanNextChannel():Send PWA NullData frame to notify the associated AP!
[161659.538123] RT35xx: SwitchChannel#12(RF=8, Pwr0=1, Pwr1=5, 1T), N=0xF6, K=0x07, R=0x02
[161659.682132] RT35xx: SwitchChannel#13(RF=8, Pwr0=3, Pwr1=5, 1T), N=0xF7, K=0x02, R=0x02
[161659.826121] RT35xx: SwitchChannel#11(RF=8, Pwr0=1, Pwr1=5, 1T), N=0xF6, K=0x02, R=0x02
[161659.828258] SYNC - End of SCAN, restore to channel 11, Total BSS[02]
[161659.828272] ScanNextChannel -- Send PSM Data frame
[161659.828275] SCAN done, resume MSDU transmission ...
[161659.831595] RT35xx: SwitchChannel#11(RF=8, Pwr0=1, Pwr1=5, 1T), N=0xF6, K=0x02, R=0x02
[161659.833719] CNTL - All roaming failed, restore to channel 11, Total BSS[02]
[161659.838827] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 373
[161665.004311] MediaState is connected
[161665.004328] ==>rt_ioctl_giwmode(mode=2)
[161665.004335] ==>rt_ioctl_giwfreq  11
[161665.004349] rt28xx_get_wireless_stats --->
[161665.004352] <--- rt28xx_get_wireless_stats

---

### Post by Reded on 2011-11-29
Getting really frustrated with the internet cutting off everytime I Skype/download. Really hope there's a fix for this out there!

---

### Post by Reded on 2011-11-30
Definatly seems to be a Ubuntu issue - Went on Windows on my computer (Had it installed too as a just-in-case for a while) And I got no such disconnection issue.
 
Really, is there nothing I can possibly do to fix this? It's a brand-new Wireless Card, don't really want to try buying another...

---

### Post by Reded on 2011-11-30
This issue alone is causing me to want to just ditch Ubuntu completely - I can't physically do anything I do with my computer without disconnecting.

It's doing it with my USB Dongle too - Power management is off. I really do hope I can get help getting a fix for this, as I do not want to use Windows any time soon. Starting to lose hope though as this thread's been going 2 weeks now and hasn't had any reply whatsoever :(

---

