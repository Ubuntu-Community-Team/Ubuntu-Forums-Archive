---
title: "Wifi looks perfectly fine, but doesn't work"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by PhotoShoe on 2013-05-14
Hello,
first sorry about my English :)

I have really weird problem.
I can connect surf and download things from other wifi except for my Home wirless.
I can surf the internet when im connected to my home wireless and at the moment I try to download something it doesnt work any more.
The annoying thing is that it looks like it is connected and it says im connected.
Help? :(
I have a dual boot to windows 7 and my wifi works perfectly thee.
my computer is Intel® Core&#8482; i5 CPU 650 @ 3.20GHz × 4 
32-bit
and connected to wifi with TP-LINK TL-WN821N
EDIT:
now after a few minutes it just stops the conection even if i dont downlaod anything (still looks perfectly connected)

---

### Post by praseodym on 2013-05-14
Please open a terminal with CTRL+ALT+T and show the outputs of the commands:
```

uname -a
lsusb
lsmod
iwconfig
ifconfig -a
rfkill list
```

---

### Post by PhotoShoe on 2013-05-15
```
itay@ubuntu:~$ uname -a
Linux ubuntu 3.5.0-28-generic #48~precise1-Ubuntu SMP Wed Apr 24 21:43:05 UTC 2013 i686 i686 i386 GNU/Linux
itay@ubuntu:~$ lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0d62:2106 Darfon Electronics Corp. Dell L20U Multimedia Keyboard
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 005: ID 0cf3:1002 Atheros Communications, Inc. TP-Link TL-WN821N v2 802.11n [Atheros AR9170]
itay@ubuntu:~$ lsmod
Module Size Used by
vesafb 13518 1 
bnep 17791 2 
rfcomm 38104 0 
nvidia 10287221 41 
bluetooth 189585 10 bnep,rfcomm
snd_hda_codec_hdmi 31778 4 
arc4 12474 2 
snd_hda_codec_realtek 64959 1 
coretemp 13362 0 
kvm_intel 127736 0 
snd_hda_intel 32983 5 
snd_hda_codec 116477 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
kvm 365556 1 kvm_intel
carl9170 77718 0 
snd_hwdep 13277 1 snd_hda_codec
mac80211 475546 1 carl9170
snd_pcm 81124 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi 13133 0 
aesni_intel 17979 1 
snd_rawmidi 25426 1 snd_seq_midi
cryptd 19822 1 aesni_intel
snd_seq_midi_event 14476 1 snd_seq_midi
ath 19436 1 carl9170
aes_i586 16996 1 aesni_intel
snd_seq 51594 2 snd_seq_midi,snd_seq_midi_event
snd_timer 28932 2 snd_pcm,snd_seq
snd_seq_device 14138 3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211 181041 3 carl9170,mac80211,ath
snd 62675 20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 14636 1 snd
psmouse 91022 0 
snd_page_alloc 14109 2 snd_hda_intel,snd_pcm
serio_raw 13032 0 
mei 36404 0 
lpc_ich 16993 0 
microcode 18396 0 
mac_hid 13078 0 
ppdev 12850 0 
video 19117 0 
parport_pc 32115 1 
binfmt_misc 17293 1 
lp 17456 0 
parport 40931 3 ppdev,parport_pc,lp
hid_generic 12485 0 
usbhid 46054 0 
hid 82511 2 hid_generic,usbhid
e1000e 177679 0 
itay@ubuntu:~$ iwconfig
wlan0 IEEE 802.11bgn ESSID:"inbar1" 
Mode:Managed Frequency:2.437 GHz Access Point: 00:78:9E:FB:BF:AA 
Bit Rate=78 Mb/s Tx-Power=20 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=59/70 Signal level=-51 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:70 Invalid misc:39 Missed beacon:0


lo no wireless extensions.


eth0 no wireless extensions.


itay@ubuntu:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 70:71:bc:71:99:6f 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20 Memory:fb100000-fb120000 


lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:227 errors:0 dropped:0 overruns:0 frame:0
TX packets:227 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:22889 (22.8 KB) TX bytes:22889 (22.8 KB)


wlan0 Link encap:Ethernet HWaddr 00:27:19:f2:3c:4f 
inet addr:192.168.1.12 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::227:19ff:fef2:3c4f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2306 errors:0 dropped:0 overruns:0 frame:0
TX packets:1746 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:2443352 (2.4 MB) TX bytes:274909 (274.9 KB)


itay@ubuntu:~$ rfkill list
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

```

thats when im connected to my home wireless and not downloading anything
edit:
now after a few minutes it just stops the conection even if i dont downlaod anything (still looks perfectly connected)

---

### Post by praseodym on 2013-05-15
Try to deactivate the hardware encryption of the driver on-the-fly:
```

sudo modprobe -rfv carl9170
sudo modprobe -v carl9170 nohwcrypt=true
```
Check:
```

sudo iwlist scan
dmesg | grep 9179
```

---

### Post by PhotoShoe on 2013-05-15
after I did the first two commands you told me to do I couldnt recover the interent at all so i Restarted the computer and made the other two:

```
itay@ubuntu:~$ sudo iwlist scan[sudo] password for itay: 
wlan0     Scan completed :
          Cell 01 - Address: 00:78:9E:FB:BF:AA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"inbar1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005f73a9b88d
                    Extra: Last beacon: 476ms ago
                    IE: Unknown: 0006696E62617231
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180206F00C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: C0:AC:54:F5:68:37
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"ravid"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 1920ms ago
                    IE: Unknown: 00057261766964
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD750050F204104A0001101044000102103B00010310470010E85B0B88C0EAAE190B970215506830401021000846405354333138341023000846405354333138341024000631323334353610420007303030303030311054000800060050F204000110110006484F54424F58100800020088103C000101
                    IE: Unknown: DD090010180202F00C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 5E:CE:46:CB:F0:66
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000d3ce139170
                    Extra: Last beacon: 1292ms ago
                    IE: Unknown: 000768707365747570
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: 94:0C:6D:EB:C6:92
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"TP-LINK_E8BEB0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ceadff98b
                    Extra: Last beacon: 184ms ago
                    IE: Unknown: 000E54502D4C494E4B5F453842454230
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000940C6DEBC692960C6DEBC69264002C010808
          Cell 05 - Address: 00:0E:2E:34:09:D1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"VanBuren"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 54 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006a42198192
                    Extra: Last beacon: 276ms ago
                    IE: Unknown: 000856616E427572656E
                    IE: Unknown: 010882848B960C18306C
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 320412244860
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:22:B0:DB:CF:E6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"Bezeq_dbcfe3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f0a108100c
                    Extra: Last beacon: 536ms ago
                    IE: Unknown: 000C42657A65715F646263666533
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180205F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


itay@ubuntu:~$ dmesg | grep 9179



```


OR if you wanted me to do all of the codes together, save the code, here it is:
```
**&#8203;**[FONT=Verdana]itay@ubuntu:~$sudo modprobe -rfv carl9170[/FONT][COLOR=#222222][FONT=Verdana][SIZE=2][sudo]password for itay: [/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]Sorry,try again.[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2][sudo]password for itay: [/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]rmmod/lib/modules/3.5.0-28-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]rmmod/lib/modules/3.5.0-28-generic/kernel/net/mac80211/mac80211.ko[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]rmmod/lib/modules/3.5.0-28-generic/kernel/drivers/net/wireless/ath/ath.ko[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]rmmod/lib/modules/3.5.0-28-generic/kernel/net/wireless/cfg80211.ko[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]itay@ubuntu:~$sudo modprobe -v carl9170 nohwcrypt=true[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]insmod/lib/modules/3.5.0-28-generic/kernel/net/wireless/cfg80211.ko [/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]insmod/lib/modules/3.5.0-28-generic/kernel/drivers/net/wireless/ath/ath.ko [/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]insmod/lib/modules/3.5.0-28-generic/kernel/net/mac80211/mac80211.ko [/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]insmod/lib/modules/3.5.0-28-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.konohwcrypt=true[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]FATAL:Error inserting carl9170(/lib/modules/3.5.0-28-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko):Invalid argument[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]itay@ubuntu:~$sudo iwlist scan[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]lo       Interface doesn't support scanning.[/SIZE][/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana][SIZE=2]eth0     Interface doesn't support scanning.[/SIZE][/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana][SIZE=2]itay@ubuntu:~$dmesg | grep 9179[/SIZE][/FONT][/COLOR]
[FONT=Liberation Serif]
[/FONT]


```


EDIT: still after few minutes the wifi doesnt work anymore, so i connected myself to another one

---

### Post by praseodym on 2013-05-15
Load the driver without parameter:

```
sudo modprobe -v carl9170
```

and change the encryption to pure WPA2-AES

---

### Post by PhotoShoe on 2013-05-15
> **praseodym said:**
> Load the driver without parameter:

```
sudo modprobe -v carl9170
```

and change the encryption to pure WPA2-AES
"[COLOR=#000000][INDENT]and change the encryption to pure WPA2-AES[/INDENT]


[/COLOR]
[COLOR=#000000][B]" ??
[RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by praseodym on 2013-05-15
Type the router IP address (192.168.1.1?!) into your browser and change the mode in the interface (see manual)

---

### Post by PhotoShoe on 2013-05-15
> **praseodym said:**
> Type the router IP address (192.168.1.1?!) into your browser and change the mode in the interface (see manual)

sorry for being new , thanks again for the help..

It just keeps loading and doesnt go anywhere

---

### Post by praseodym on 2013-05-15
Now try:
```

sudo modprobe -rfv carl9170
sudo modprobe -v carl9170 nohwcrypt=1
```

---

### Post by PhotoShoe on 2013-05-15
> **praseodym said:**
> Now try:
```

sudo modprobe -rfv carl9170
sudo modprobe -v carl9170 nohwcrypt=1
```

worked for some time, then stopped again:(

---

### Post by praseodym on 2013-05-15
Tried another USB slot? Do you use a cable extension?

---

### Post by PhotoShoe on 2013-05-15
didnt try another slot, and yes i do use cable extention

---

### Post by praseodym on 2013-05-15
Try it without extension. Same here with a TP-Link stick

---

### Post by rachaelmason on 2013-05-16
thanks for the codes it's really helps

---

