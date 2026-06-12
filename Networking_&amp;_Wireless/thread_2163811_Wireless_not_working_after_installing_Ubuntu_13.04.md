---
title: "Wireless not working after installing Ubuntu 13.04"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by JesUbik on 2013-07-19
So my network connection is not working at all after formating my computer and installing Ubuntu 13.04.

Before formating, I was using Windows 7 in one partition and Ubuntu 12.04 in another. I installed windows first and had to download some drivers to have network, video, etc, working properly. And Ubuntu 12.04 automatically had everything working by itself.

So I formated my computer, installed Ubuntu 13.04 and can't setup the internet connection. 

Here is the output for ifconfig in terminal:

jessies-SpaceShip:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:d6:78:d0   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 


eth1      Link encap:Ethernet  HWaddr c0:cb:38:4b:51:13   
          inet6 addr: fe80::c2cb:38ff:fe4b:5113/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17 


lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:65536  Metric:1 
          RX packets:3696 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3696 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:297080 (297.0 KB)  TX bytes:297080 (297.0 KB) 







----

Also, I checked for the drivers at Software and Updates and it looked like that:


Software and updates > additional drivers > 


Broadcom corporation: BCM4313 802.11b/g/n Wireless LAN Controller
(this device is using an alternative driver:)
	Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source


----

I know that this is probably a very begginer question but english is not my native language and I've been searching for solutions in this very old and small netbook.

Does any of you know how to get it working, please? 

Thank you (:

---

### Post by praseodym on 2013-07-19
Hi,

uninstall the STA driver and its config via:```


sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```
Download this firmware file and save it in "Downloads".
[http://media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz)
Installation via:
```
sudo tar ~/Downloads/xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```
Shutdown for 10 minutes currentless and reboot.

---

### Post by JesUbik on 2013-07-19
Thank you for the quick anwer, praseodym.

So I was able to uninstall the STA driver with the first command line. But couldn't perform the rest of it. 

This is the output:

jessica@jessies-SpaceShip:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove &#8216;/etc/modprobe.d/blacklist-bcm43.conf&#8217;: No such file or directory
jessica@jessies-SpaceShip:~$ sudo rm /etc/modprobe.d/broadcom-sta-common.conf
rm: cannot remove &#8216;/etc/modprobe.d/broadcom-sta-common.conf&#8217;: No such file or directory
jessica@jessies-SpaceShip:~$ sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf
rm: cannot remove &#8216;/etc/modprobe.d/broadcom-sta-dkms.conf&#8217;: No such file or directory
jessica@jessies-SpaceShip:~$ sudo tar ~/Downloads/xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware
tar: invalid option -- '/'
Try `tar --help' or `tar --usage' for more information.
jessica@jessies-SpaceShip:~$

---

### Post by praseodym on 2013-07-19
Sorry typo:

```
sudo tar xvf ~/Downloads/5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware
```is the right command

---

### Post by JesUbik on 2013-07-19
Ok! Installed it!

But Ubuntu keeps not turning wifi on... Maybe is there something about my broadcom [COLOR=#000000]BCM4313 [/COLOR]board?

Thank you very much (:

---

### Post by praseodym on 2013-07-19
Check:
```

dmesg | egrep 'bcma|brcm'
iwconfig
sudo iwlist scan
lsmod
```

---

### Post by JesUbik on 2013-07-19
jessica@jessies-SpaceShip:~$ dmesg | egrep 'bcma|brcm' 
[   10.729042] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08 
[   10.729070] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0) 
[   10.729091] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0) 
[   10.729132] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0) 
[   10.745459] bcma: bus0: Bus registered 
[   11.646670] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17 
[   17.289181] brcmsmac bcma0:0: brcms_ops_start: brcms_up() returned -132 
jessica@jessies-SpaceShip:~$ iwconfig 
eth0      no wireless extensions. 


lo        no wireless extensions. 


wlan0     IEEE 802.11bgn  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
           
jessica@jessies-SpaceShip:~$ sudo iwlist scan 
[sudo] password for jessica: 
eth0      Interface doesn't support scanning. 


lo        Interface doesn't support scanning. 


wlan0     Interface doesn't support scanning : Network is down 


jessica@jessies-SpaceShip:~$ lsmod 
Module                  Size  Used by 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm 
joydev                 17377  0 
arc4                   12615  2 
snd_hda_codec_idt      70256  1 
brcmsmac              550698  0 
cordic                 12574  1 brcmsmac 
brcmutil               14755  1 brcmsmac 
mac80211              606457  1 brcmsmac 
cfg80211              510937  2 brcmsmac,mac80211 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo 
videobuf2_memops       13202  1 videobuf2_vmalloc 
videobuf2_core         40513  1 uvcvideo 
videodev              129260  2 uvcvideo,videobuf2_core 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel 
bcma                   41051  1 brcmsmac 
snd_hda_intel          39619  3 
snd_hda_codec         136453  2 snd_hda_codec_idt,snd_hda_intel 
snd_hwdep              13602  1 snd_hda_codec 
snd_pcm                97451  2 snd_hda_codec,snd_hda_intel 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi 
snd_rawmidi            30180  1 snd_seq_midi 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi 
snd_timer              29425  2 snd_pcm,snd_seq 
i915                  600351  8 
wmi                    19070  1 dell_wmi 
video                  19390  1 i915 
drm_kms_helper         49394  1 i915 
mac_hid                13205  0 
snd                    68876  15 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device 
dell_laptop            17369  0 
drm                   286313  4 i915,drm_kms_helper 
lpc_ich                17061  0 
dcdbas                 14397  1 dell_laptop 
soundcore              12680  1 snd 
i2c_algo_bit           13413  1 i915 
microcode              22881  0 
mei                    41158  0 
lp                     17759  0 
intel_ips              17978  0 
parport                46345  3 lp,ppdev,parport_pc 
psmouse                95870  0 
serio_raw              13215  0 
atl1c                  41071  0 
ums_realtek            17949  0 
usb_storage            57204  1 ums_realtek 
jessica@jessies-SpaceShip:~$

---

### Post by praseodym on 2013-07-19
The card is "off":
> ```

wlan0 IEEE 802.11bgn ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=[COLOR="#FF0000"]off[/COLOR]
Retry long limit:7 RTS thrff Fragment thrff
Power Management on 
```
Any button/switch/key/key combination? Try also:
```

sudo rfkill unblock all
rfkill list
```

---

### Post by JesUbik on 2013-07-19
jessica@jessies-SpaceShip:~$ sudo rfkill unblock all 
jessica@jessies-SpaceShip:~$ rfkill list 
0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: yes



I don't have any switch... just F2 for turning wifi on or off but it seems not to work with Linux

---

### Post by JesUbik on 2013-07-19
HA I can see avaliable wifi networks!

---

### Post by praseodym on 2013-07-19
Check "rfkill list" now.

---

### Post by JesUbik on 2013-07-19
Ok.
Now I can see my wifi router, but can't connect.

---

### Post by praseodym on 2013-07-19
Reset your BIOS to default settings.

---

### Post by JesUbik on 2013-07-19
[COLOR=#000000]jessica@jessies-SpaceShip:~$ sudo rfkill unblock all [/COLOR]
[COLOR=#000000]jessica@jessies-SpaceShip:~$ rfkill list [/COLOR]
[COLOR=#000000]0: phy0: Wireless LAN [/COLOR]
[COLOR=#000000]Soft blocked: no [/COLOR]
[COLOR=#000000]Hard blocked: no[/COLOR]

---

### Post by praseodym on 2013-07-19
Now you should be able to connect.

---

### Post by JesUbik on 2013-07-19
I can see my network signal, but when I insert my password it shows a message saying that authentication is required by the Wi Fi network.

---

### Post by praseodym on 2013-07-19
Do you have blanks in you ESSID and/or PW? Or other "strange" characters?

---

### Post by JesUbik on 2013-07-19
not blank, but I do have some strange ones. :T

---

### Post by praseodym on 2013-07-19
[http://wiki.ubuntuusers.de/wlan/sonderzeichen](http://wiki.ubuntuusers.de/wlan/sonderzeichen)

Check the 1st grey box for allowed characters

---

### Post by JesUbik on 2013-07-19
Ok. All of them are allowed (:
(but still not connecting. ugh.)

---

### Post by praseodym on 2013-07-20
Ok,
lets check
```
iwconfig
iwlist chan
sudo iwlist scan
cat /etc/resolv.conf
route -n
ifconfig -a
lsmod
```

---

### Post by caersith on 2013-07-20
I can't help much but I wonder If the network is from mac (adhoc)? If it is, try to change the password to  something like this $1234567890 on mac, and in the ubuntu exclude the $  when you input the password.

---

### Post by JesUbik on 2013-07-20
ok

```

jessica@jessies-spaceship:~$ iwconfigeth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
jessica@jessies-spaceship:~$ iwlist chan
eth0      no frequency information.


lo        no frequency information.


wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
jessica@jessies-spaceship:~$ sudo iwlist scan
[sudo] password for jessica: 
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: D4:CA:6D:21:AD:AB
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-3 dBm  
                    Encryption key:on
                    ESSID:"glaeser"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000084659ea9b0
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 0007676C6165736572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4E1003FFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160A050000000000000000000000000000000000000000
                    IE: Unknown: DD2A000C42000000011E00100000006610050000443443413644323141444142000000000000000005029909
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E1003FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340A050000000000000000000000000000000000000000
          Cell 02 - Address: C8:3A:35:30:8D:08
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"ksa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001068163bf0
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 00036B7361
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0400000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:15:6D:65:AB:4F
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:11 Mb/s; 36 Mb/s
                    Mode:Master
                    Extra:tsf=000001502ee40184
                    Extra: Last beacon: 21548ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01029648
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: DD2A000C42000000011E00100000006618050000000000000000000000000000000000000000000005027609
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 04 - Address: 02:15:6D:65:AB:4F
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:11 Mb/s; 36 Mb/s
                    Mode:Master
                    Extra:tsf=000001502ee404e6
                    Extra: Last beacon: 21548ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01029648
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: DD2A000C42000000011E00100000006618050000000000000000000000000000000000000000000005027609
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 05 - Address: 02:15:6D:65:AB:51
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"LT_H_03"
                    Bit Rates:11 Mb/s; 36 Mb/s
                    Mode:Master
                    Extra:tsf=000001502ee40626
                    Extra: Last beacon: 21548ms ago
                    IE: Unknown: 00074C545F485F3033
                    IE: Unknown: 01029648
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: DD2A000C42000000011E00100000006618050000000000000000000000000000000000000000000005027609
          Cell 06 - Address: 02:15:6D:65:AB:50
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:11 Mb/s; 36 Mb/s
                    Mode:Master
                    Extra:tsf=000001502ee40752
                    Extra: Last beacon: 21548ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01029648
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD2A000C42000000011E00100000006618050000000000000000000000000000000000000000000005027609
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 07 - Address: 00:1A:3F:6E:B5:12
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"JSOARES"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002d7d82181
                    Extra: Last beacon: 388ms ago
                    IE: Unknown: 00074A534F41524553
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000001A3F6EB512021A3F6EB51264002C010808
          Cell 08 - Address: 00:1A:3F:8D:80:2E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Link_A_B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002a4801b41ed
                    Extra: Last beacon: 21120ms ago
                    IE: Unknown: 00084C696E6B5F415F42
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0102
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 09 - Address: 00:1A:3F:86:EF:0C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"WiFi Schimidt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002d091506d80
                    Extra: Last beacon: 320ms ago
                    IE: Unknown: 000D5769466920536368696D696474
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
          Cell 10 - Address: 00:0C:42:67:17:A6
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:11 Mb/s; 36 Mb/s
                    Mode:Master
                    Extra:tsf=000000a1dc158184
                    Extra: Last beacon: 844ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01029648
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: DD2A000C42000000011E00100000006618050000000000000000000000000000000000000000000005027109
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 11 - Address: 00:15:6D:65:42:81
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:11 Mb/s
                    Mode:Master
                    Extra:tsf=00000001657ba372
                    Extra: Last beacon: 764ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010196
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: DD2A000C42000000011E00000000006605040000000000000000000000000000000000000000000005027B09
                    IE: Unknown: DD180050F2020101000003A5000027A500004254BC0062436600
          Cell 12 - Address: 99:99:99:99:99:99
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"VLH_01"
                    Bit Rates:11 Mb/s
                    Mode:Master
                    Extra:tsf=00000001657ba4c4
                    Extra: Last beacon: 764ms ago
                    IE: Unknown: 0006564C485F3031
                    IE: Unknown: 010196
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: DD36000C42000000011E000000000066050400000000000000000000000000000000000000000000030A424F4D4D54454D504F3205027B09
          Cell 13 - Address: 02:15:6D:65:42:82
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:11 Mb/s
                    Mode:Master
                    Extra:tsf=00000001657ba60a
                    Extra: Last beacon: 764ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010196
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: DD2A000C42000000011E00000000006605040000000000000000000000000000000000000000000005027B09
                    IE: Unknown: DD180050F2020101000003A5000027A500004254BC0062436600
          Cell 14 - Address: 02:15:6D:65:42:81
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:11 Mb/s
                    Mode:Master
                    Extra:tsf=00000001657ba75c
                    Extra: Last beacon: 760ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010196
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD2A000C42000000011E00000000006605040000000000000000000000000000000000000000000005027B09
                    IE: Unknown: DD180050F2020101000003A5000027A500004254BC0062436600
          Cell 15 - Address: 00:0C:42:67:14:C6
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:11 Mb/s; 36 Mb/s
                    Mode:Master
                    Extra:tsf=000000a1dbe835f4
                    Extra: Last beacon: 544ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01029648
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: DD2A000C42000000011E00100000006618050000000000000000000000000000000000000000000005028F09
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 16 - Address: 00:15:6D:65:AB:45
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:11 Mb/s; 36 Mb/s
                    Mode:Master
                    Extra:tsf=00000001657d3242
                    Extra: Last beacon: 540ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01029648
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: DD2A000C42000000011E00000000006605040000000000000000000000000000000000000000000005028F09
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 17 - Address: 02:15:6D:65:AB:45
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"MINARDI"
                    Bit Rates:11 Mb/s; 36 Mb/s
                    Mode:Master
                    Extra:tsf=00000001657d40b6
                    Extra: Last beacon: 536ms ago
                    IE: Unknown: 00074D494E41524449
                    IE: Unknown: 01029648
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: DD2A000C42000000011E00000000006605040000000000000000000000000000000000000000000005028F09
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00


jessica@jessies-spaceship:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
jessica@jessies-spaceship:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
jessica@jessies-spaceship:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:d6:78:d0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:74 errors:0 dropped:325 overruns:325 frame:325
          TX packets:348 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:6627 (6.6 KB)  TX bytes:61552 (61.5 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65160 (65.1 KB)  TX bytes:65160 (65.1 KB)


wlan0     Link encap:Ethernet  HWaddr c0:cb:38:4b:51:13  
          inet6 addr: fe80::c2cb:38ff:fe4b:5113/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2700 (2.7 KB)  TX bytes:3100 (3.1 KB)


jessica@jessies-spaceship:~$ lsmod
Module                  Size  Used by
ums_realtek            17949  0 
dm_crypt               22820  1 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
joydev                 17377  0 
arc4                   12615  2 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
snd_hda_codec_idt      70256  1 
brcmsmac              550698  0 
snd_hda_intel          39619  3 
snd_hda_codec         136453  2 snd_hda_codec_idt,snd_hda_intel
cordic                 12574  1 brcmsmac
brcmutil               14755  1 brcmsmac
snd_hwdep              13602  1 snd_hda_codec
mac80211              606457  1 brcmsmac
snd_pcm                97451  2 snd_hda_codec,snd_hda_intel
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
cfg80211              510937  2 brcmsmac,mac80211
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
lpc_ich                17061  0 
bcma                   41051  1 brcmsmac
intel_ips              17978  0 
snd                    68876  15 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
dell_laptop            17369  0 
dcdbas                 14397  1 dell_laptop
soundcore              12680  1 snd
psmouse                95870  0 
serio_raw              13215  0 
mei                    41158  0 
dell_wmi               12681  0 
lp                     17759  0 
microcode              22881  0 
parport                46345  3 lp,ppdev,parport_pc
sparse_keymap          13890  1 dell_wmi
usb_storage            57204  2 ums_realtek
wmi                    19070  1 dell_wmi
i915                  600351  8 
ahci                   25731  2 
libahci                31364  1 ahci
video                  19390  1 i915
i2c_algo_bit           13413  1 i915
drm_kms_helper         49394  1 i915
drm                   286313  4 i915,drm_kms_helper
atl1c                  41071  0 
jessica@jessies-spaceship:~$ 





```

---

### Post by praseodym on 2013-07-31
There are no nameservers in your /etc/resolv.conf:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

