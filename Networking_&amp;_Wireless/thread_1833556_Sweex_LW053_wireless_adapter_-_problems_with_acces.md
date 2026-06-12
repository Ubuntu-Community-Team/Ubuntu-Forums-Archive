---
title: "Sweex LW053 wireless adapter - problems with accessing the internet"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by smartse on 2011-08-26
I installed 11.04 yesterday and have been trying to get my Sweex LW053 adapter to connect me to my wireless network. I've found people saying it works elsewhere in Linux but I can't get it to work. I've tried various things I found suggested in other threads and have installed the windows drivers but without any success so far. When I try to connect it does the same as before I changed any settings - the network is detected but it won't connect. I'll copy all the possibly relevant output from the terminal, with the hope that someone can understand it and help me out.

          nm-tool:
 

 - Device: wlan0 ----------------------------------------------------------------
   Type:              802.11 WiFi
   Driver:            ndiswrapper
   State:             disconnected
   Default:           no
   HW Address:        00:16:0A:1B:E8:00
 

   Capabilities:
 

   Wireless Properties
     WEP Encryption:  yes
     WPA Encryption:  yes
     WPA2 Encryption: yes
 

   Wireless Access Points  
     BTHomeHub2-RRPH: Infra, 00:21:04:A5:55:72, Freq 2412 MHz, Rate 54 Mb/s, Strength 58 WPA WPA2
     BTOpenzone:      Infra, 06:21:04:A5:55:72, Freq 2412 MHz, Rate 54 Mb/s, Strength 58
     BTFON:           Infra, 0A:21:04:A5:55:72, Freq 2412 MHz, Rate 54 Mb/s, Strength 58
 

 iwconfig: (when not connected)
 

 wlan0     IEEE 802.11g  ESSID:off/any   
           Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
           Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm   
           RTS thr=2347 B   Fragment thr=2346 B    
           Power Management:off
           Link Quality:0  Signal level:0  Noise level:0
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 

 iwconfig: (when trying to connect)
 

 wlan0     IEEE 802.11g  ESSID:"BTHomeHub2-RRPH"   
           Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:04:A5:55:72    
           Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm   
           RTS thr=2347 B   Fragment thr=2346 B    
           Power Management:off
           Link Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 

 

 ip addr:  
 

 simon@simon-Inspiron-530s:~$ ip addr
 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN  
     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
     inet 127.0.0.1/8 scope host lo
     inet6 ::1/128 scope host  
        valid_lft forever preferred_lft forever
 2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
     link/ether 00:1a:a0:93:0e:77 brd ff:ff:ff:ff:ff:ff
 3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
     link/ether 00:16:0a:1b:e8:00 brd ff:ff:ff:ff:ff:ff
     inet6 fe80::216:aff:fe1b:e800/64 scope link  
        valid_lft forever preferred_lft forever
 

 ndiswrapper -l:
 

 WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
 rt73 : driver installed
     device (148F:2573) present (alternate driver: rt2500usb)
 

 modprobe blacklist contains:
 

 blacklist bcm43xx
 blacklist b43
 blacklist b43legacy
 blacklist ssb
 blacklist rt2500
 

 sudo lshw -C network:
   *-network
        description: Wireless interface
        physical id: 1
        logical name: wlan0
        serial: 00:16:0a:1b:e8:00
        capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=ndiswrapper+rt73 driverversion=1.56+Ralink,01/15/2008, 1.03.00. link=no multicast=yes wireless=IEEE 802.11g
  

I have a feeling that I haven't blacklisted the rt2500 driver and that's what's causing the problems, but I can't work out how to get rid of it. I'm pretty/very n00bish at this malarky, so if you can try and reply with that in mind I'd be greatful. Thanks!

---

### Post by praseodym on 2011-08-26
Hi, try the following:

```
gksudo gedit /etc/modprobe.d/blacklist
``` without .conf !!!

change

```
blacklist rt2500
```

to

```
blacklist rt2500usb
``` and rename the file to ".conf":

```
sudo mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.conf
```
For this device the driver rt73usb is already inside of the kernel, so no ndiswrapper is needed:

```
sudo modprobe -rf ndiswrapper rt73usb
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo modprobe -v rt73usb
sudo depmod -a
sudo update-initramfs -u
sudo service network-manager restart
```
You may replug the stick and control the following:

```
lsmod
dmesg | grep tail -n25
iwconfig
rfkill list
sudo iwlist scan
cd /etc/modprobe.d/
ls -l
```

---

### Post by praseodym on 2011-08-26
cd /etc/modprobe.d/

ls -l

Please show this first !

---

### Post by smartse on 2011-08-27
Thanks for the reply - I did as you suggested and restarted as well, but it still isn't connecting.

Here is the output after using the lsmod etc. :

simon@simon-Inspiron-530s:~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
arc4                   12473  2 
rt73usb                26854  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              19693  1 rt73usb
rt2x00lib              39075  2 rt73usb,rt2x00usb
mac80211              257001  2 rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
binfmt_misc            13213  1 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
radeon                896428  3 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14054  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
psmouse                73312  0 
soundcore              12600  1 snd
drm                   180037  5 radeon,ttm,drm_kms_helper
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
i2c_algo_bit           13184  1 radeon
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  1 
uas                    17676  0 
floppy                 60032  0 
e1000e                138627  0 
simon@simon-Inspiron-530s:~$ dmesg | grep tail -n25
simon@simon-Inspiron-530s:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
simon@simon-Inspiron-530s:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
simon@simon-Inspiron-530s:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:04:A5:55:72
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-RRPH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002175e10a180
                    Extra: Last beacon: 1172ms ago
                    IE: Unknown: 000F4254486F6D65487562322D52525048
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 06:21:04:A5:55:72
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002175e0fc2a6
                    Extra: Last beacon: 1176ms ago
                    IE: Unknown: 000A42544F70656E7A6F6E65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 0A:21:04:A5:55:72
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"BTFON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002175e102e93
                    Extra: Last beacon: 1176ms ago
                    IE: Unknown: 00054254464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000

simon@simon-Inspiron-530s:~$ cd /etc/modprobe.d/
simon@simon-Inspiron-530s:/etc/modprobe.d$ ls -l
total 32
-rw-r--r-- 1 root root 2507 2011-02-21 07:37 alsa-base.conf
-rw-r--r-- 1 root root  325 2011-04-01 15:05 blacklist-ath_pci.conf
-rw-r--r-- 1 root root   86 2011-08-27 15:18 blacklist.conf
-rw-r--r-- 1 root root  210 2011-04-01 15:05 blacklist-firewire.conf
-rw-r--r-- 1 root root  661 2011-04-01 15:05 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 2011-02-21 07:37 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 2011-08-25 21:13 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 2011-04-01 15:05 blacklist-rare-network.conf
-rw-r--r-- 1 root root 1077 2011-04-01 15:05 blacklist-watchdog.conf
simon@simon-Inspiron-530s:/etc/modprobe.d$ 

Any ideas on what to try next? Thanks again!

---

### Post by praseodym on 2011-08-27
Looks pretty good so far. Deactivate the power management:

```
sudo iwconfig wlan0 power off
sudo service network-manager restart
```
```
dmesg | grep rt7
sudo iwlist scan
iwconfig
```

---

### Post by smartse on 2011-08-27
As before, here is the output from those commands:

simon@simon-Inspiron-530s:~$ sudo iwconfig wlan0 power off
[sudo] password for simon: 
simon@simon-Inspiron-530s:~$ sudo service network-manager restart
network-manager start/running, process 3628
simon@simon-Inspiron-530s:~$ dmesg | grep rt7
simon@simon-Inspiron-530s:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

iwconfig
wlan0     Scan completed :
          Cell 01 - Address: 06:21:04:A5:55:72
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000021a14683180
                    Extra: Last beacon: 184ms ago
                    IE: Unknown: 000A42544F70656E7A6F6E65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 0A:21:04:A5:55:72
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"BTFON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000021a146b5180
                    Extra: Last beacon: 184ms ago
                    IE: Unknown: 00054254464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 00:21:04:A5:55:72
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-RRPH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000021a14711cd0
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000F4254486F6D65487562322D52525048
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101B0000000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000

simon@simon-Inspiron-530s:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"BTHomeHub2-RRPH"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:04:A5:55:72   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24   Missed beacon:0

Thanks

---

### Post by wildmanne39 on 2011-08-27
Hi, I believe you need to change master to managed mode also.

---

### Post by smartse on 2011-08-27
How do I do that?

---

### Post by wildmanne39 on 2011-08-27
Hi, never mind that is not the problem I read the wrong information, I am sorry about that.

---

