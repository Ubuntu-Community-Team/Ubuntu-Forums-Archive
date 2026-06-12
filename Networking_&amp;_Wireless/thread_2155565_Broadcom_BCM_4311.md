---
title: "Broadcom BCM 4311"
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by forestdesigns on 2013-06-18
Hey, :)

First of all, I'd like to say thanks to all of you who are helping those of us in need of technical support!

I've recently rid my laptop of XP & have installed 13.04.  I'm happy to have done it, except for the need to get the wifi up & running.  I've been wrestling with this issue for almost a week now, but haven't been able to solve the problem.  I've reinstalled 13.04, installed the 12. 04, & can't seem to solve it permanently. At the moment I have both installed & imagine that I will delete everything again once I know the remedy to the problem!

I'm using an HP nx6310

lspci -nn | grep -e 0200 -e 0280 [FONT=arial]
gives me the following:[/FONT]
02:0e.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

[FONT=arial]I've tried the STA, & the 43 drivers. At the moment I have the ethernet, but the wifi is not showing
up.  I had the wifi for a night, although it never actually found any networks when I know that there
are a few within range.

In "other drivers" I have the following:[/FONT]

Broadcom Corporation: BCM4311 802.11b/g WLAN
Using Broadcom 802.11 Linux STA wireless driver source from bcml-kernel-source(proprietary)

Unknown:Unknown
This device is using a manually installed driver.

[FONT=arial]To be honest I'm not even completely sure what I'm dealing with!  Is the ethernet working with the 
BCM4311 driver?  *totally STUMPED face!*[/FONT]

Thanks for your help in advance. :)

---

### Post by praseodym on 2013-06-18
Uninstall the STA driver and install the package "linux-firmware-nonfree" via software-center.

---

### Post by forestdesigns on 2013-06-18
HOw do I uninstall?  I've seen something about "purge"?

---

### Post by praseodym on 2013-06-18
Try this:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo apt-get install linux-firmware-nonfree 
```
Reboot.

---

### Post by forestdesigns on 2013-06-18
Ok, I now have wifi (again) but it shows no available networks.  My phone shows them but the laptop does not!

Under[FONT=arial] "other drivers" I now have the following:[/FONT]

Broadcom Corporation: BCM4311 802.11b/g WLAN
Do not use this device

Unknown:Unknown
This device is using a manually installed driver.
Do not use this device

---

### Post by praseodym on 2013-06-18
Please show
```

iwconfig
ifconfig -a
lsmod
rfkill list
sudo iwlist scan
dmesg | grep b43
```

---

### Post by forestdesigns on 2013-06-18
IT"S WORKING!!!  :)  Thanks!  I really needed that!  If only I could decipher the results to get online via one of the wifi connections!

I've copied & pasted your Code, I hope it works this way.
Results are as follows:

walker@walker-HP-Compaq-nx6310-RH325ET-ABE:~$ ```
iwconfig
ppp0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          
wwan0     no wireless extensions.

lo        no wireless extensions.

eth1      no wireless extensions.

walker@walker-HP-Compaq-nx6310-RH325ET-ABE:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:17:08:41:d0:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49601 (49.6 KB)  TX bytes:49601 (49.6 KB)

ppp0      Link encap: Point-to-Point Protocol  
          inet addr:213.99.122.76  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:666596 (666.5 KB)  TX bytes:82808 (82.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:d9:3b:1d  
          inet6 addr: fe80::214:a5ff:fed9:3b1d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2486 (2.4 KB)  TX bytes:3454 (3.4 KB)

wwan0     Link encap:Ethernet  HWaddr 02:50:f3:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

walker@walker-HP-Compaq-nx6310-RH325ET-ABE:~$ lsmod
Module                  Size  Used by
ppp_deflate            12806  0 
zlib_deflate           26445  1 ppp_deflate
bsd_comp               12785  0 
ppp_async              17205  1 
crc_ccitt              12627  1 ppp_async
option                 29746  2 
usb_wwan               14830  1 option
cdc_ether              13245  0 
usbnet                 26567  1 cdc_ether
usbserial              27423  7 option,usb_wwan
usb_storage            47684  0 
snd_hda_codec_analog    75266  1 
arc4                   12543  2 
coretemp               13131  0 
joydev                 17097  0 
hp_wmi                 17712  0 
sparse_keymap          13658  1 hp_wmi
b43                   351918  0 
bcma                   39645  1 b43
pcmcia                 39544  0 
microcode              18286  0 
snd_hda_intel          38307  2 
mac80211              526519  1 b43
i915                  535544  3 
snd_hda_codec         117580  2 snd_hda_intel,snd_hda_codec_analog
snd_hwdep              13272  1 snd_hda_codec
psmouse                81038  0 
serio_raw              13031  0 
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
yenta_socket           27095  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
pcmcia_rsrc            18191  1 yenta_socket
parport_pc             27504  0 
cfg80211              436177  2 b43,mac80211
snd_seq_midi_event     14475  1 snd_seq_midi
ppdev                  12817  0 
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202069  10 bnep,rfcomm
ssb_hcd                12749  0 
snd_rawmidi            25114  1 snd_seq_midi
drm_kms_helper         47545  1 i915
video                  18894  1 i915
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
wmi                    18590  1 hp_wmi
lpc_ich                16925  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
drm                   228489  4 i915,drm_kms_helper
mac_hid                13037  0 
snd_timer              24411  2 snd_pcm,snd_seq
i2c_algo_bit           13197  1 i915
snd                    56485  13 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
firewire_ohci          35292  0 
firewire_core          61718  1 firewire_ohci
b44                    31137  0 
crc_itu_t              12627  1 firewire_core
ssb                    50834  3 b43,b44,ssb_hcd
walker@walker-HP-Compaq-nx6310-RH325ET-ABE:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
walker@walker-HP-Compaq-nx6310-RH325ET-ABE:~$ sudo iwlist scan
[sudo] password for walker: 
Sorry, try again.
[sudo] password for walker: 
ppp0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: B4:98:42:6C:CB:EB
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key: on
                    ESSID:"Orange-MF60-6CCBEB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c21fdb28
                    Extra: Last beacon: 11420ms ago
                    IE: Unknown: 00124F72616E67652D4D4636302D364343424542
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706455300010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A0C0000FF00000000000000000000008000000000000000000000
                    IE: Unknown: 3D160B000300000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD630050F204104A0001101044000102103B000103104700104028DF5867735383BD621CF0FE7D6541102100035A544510230006415236303033102400010010420001001054000800060050F2040001101100065A54452D415010080002018C103C000101
          Cell 02 - Address: A4:52:6F:ED:08:D2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:n
                    ESSID:"WLAN_08D1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003e2625634b0
                    Extra: Last beacon: 11420ms ago
                    IE: Unknown: 0009574C414E5F30384431
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010264A21D7F8E0B2D2A3B48A6BEA3A49201021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020084103C000101
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:19:15:D6:D9:E3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key: on
                    ESSID:"Luciana"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e121e6371
                    Extra: Last beacon: 11420ms ago
                    IE: Unknown: 00074C756369616E61
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDA20050F204104A0001101044000102103B0001031047001063041253101920061228001915D6D9E31021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C383637311024000D45562D323030362D30372D32371042000F3132333435363738393031323334371054000800060050F2040001101100174F4253455256412054454C45434F4D2C20415734303632100800020086
          Cell 04 - Address: 62:3D:FF:E9:C8:9C
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key: on
                    ESSID:"vodafoneC89B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000097a010315a
                    Extra: Last beacon: 11420ms ago
                    IE: Unknown: 000C766F6461666F6E6543383942
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1607070000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA20050F204104A0001101044000102103B00010310470010BC329E001DD811B28601623DFFE9C89C1021001D48756177656920546563686E6F6C6F6769657320436F2E2C204C74642E1023001C48756177656920576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F204000110110009487561776569415053100800020084103C000100
                    IE: Unknown: 0B0500000B127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706455320010D10
                    IE: Unknown: DD1E00904C338E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3407070000000000000000000000000000000000000000
          Cell 05 - Address: 6A:7D:5E:7D:39:04
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key: on
                    ESSID:"vodafone3906"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000910ed394d
                    Extra: Last beacon: 11420ms ago
                    IE: Unknown: 000C766F6461666F6E6533393036
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1607070600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA20050F204104A0001101044000102103B00010310470010BC329E001DD811B286016A7D5E7D39041021001D48756177656920546563686E6F6C6F6769657320436F2E2C204C74642E1023001C48756177656920576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F204000110110009487561776569415053100800020084103C000100
                    IE: Unknown: 0B0503000C127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706455320010D10
                    IE: Unknown: DD1E00904C338E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3407070600000000000000000000000000000000000000
          Cell 06 - Address: 40:4A:03:CE:17:0E
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key: on
                    ESSID:"WLAN_DE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003c92edb40
                    Extra: Last beacon: 11420ms ago
                    IE: Unknown: 0007574C414E5F4445
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

wwan0     Interface doesn't support scanning.

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.
```

---

### Post by wildmanne39 on 2013-06-18
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by praseodym on 2013-06-19
It works?

---

### Post by forestdesigns on 2013-06-19
It works! :)  I haven't connected yet, as I don have wifi here at home (I'm using a USB connection), but I'll definetely connect tommorrow via wifi.  Thanks a lot for your help! 

[**[COLOR=#C61919][B]Wild Man**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=508533"), I'll be sure to use the "code" thing in future.  I do have more questions, but I suppose I should post in the relevant sections to follow form.  I've read that I should check the integrety of the iso file I have downloaded, but I haven't been able to figure that one out either.  I've been trying to research & attempt before cluttering the forums with my questions. However, after a week of getting nowhere, I had my problem solved in a few minutes here!  Thanks again, [**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497")!!!

---

