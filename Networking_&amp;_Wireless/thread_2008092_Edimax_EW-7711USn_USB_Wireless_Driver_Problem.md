---
title: "Edimax EW-7711USn USB Wireless Driver Problem"
date: 2012-06-22
forum: Networking &amp; Wireless
---

### Post by erdibav on 2012-06-22
Hi
I m new to Ubuntu, Linux and this Forum
I just install  Ubuntu 10.04 with Wubi. Everything work nice but my USB Wireless Adaptor.
[http://www.edimax.com/en/support_detail.php?pl1_idSelect=support.php%3Fpl1_id%3D1%26mwsp%3D1&pl1_id=1&pd_id=303&button=Go](http://www.edimax.com/en/support_detail.php?pl1_idSelect=support.php%3Fpl1_id%3D1%26mwsp%3D1&pl1_id=1&pd_id=303&button=Go)

I have downloaded driver from;
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)
and follow the README file but when it comes "/sbin/insmod rt2870sta.ko" throws "insmod: error inserting 'rt2870sta.ko': -1 File exists" error


This is my iwconfig;
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on


And lsmod

rt2800usb              33496  0 
rt2x00usb              11164  1 rt2800usb
rt2x00lib              32165  2 rt2800usb,rt2x00usb
led_class               3764  1 rt2x00lib
mac80211              238928  2 rt2x00usb,rt2x00lib
cfg80211              148725  2 rt2x00lib,mac80211
crc_ccitt               1675  1 rt2800usb
rt2870sta             626667  0 

I m using my ethernet card to connect but wireless adapter would be nice and tidy cable mass. What is wrong with this, any help? Thanks

---

### Post by wildmanne39 on 2012-06-22
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by chili555 on 2012-06-22
I think my buddy the Wild Man would like you to add another step:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot with the ethernet detached and give us your report.

---

### Post by erdibav on 2012-06-22
Thanks for your interest, after blacklist rt2800usb, disconnect usb adapter and reboot. All i get is this. And "rfkill list all" returns nothing.
```
root@ubuntu:/home/erdi# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux ubuntu 2.6.32-41-generic #90-Ubuntu SMP Tue May 22 11:29:51 UTC 2012 x86_64 GNU/Linux

``````

root@ubuntu:/home/erdi# lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Kernel driver in use: r8169
    Kernel modules: r8169
root@ubuntu:/home/erdi# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1d57:ac01  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046e:52cc Behavior Tech. Computer Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


``````

root@ubuntu:/home/erdi# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



``````

root@ubuntu:/home/erdi# lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
snd_hda_codec_atihdmi     3023  1 
joydev                 11104  0 
snd_hda_codec_realtek   279104  1 
snd_hda_intel          25805  2 
snd_hda_codec          85791  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ppdev                   6375  0 
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             29958  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
usbhid                 41116  0 
softcursor              1565  1 bitblit
hid                    83888  1 usbhid
fglrx                2353486  31 
psmouse                65040  0 
serio_raw               4918  0 
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                12757  1 
vgastate                9857  1 vga16fb
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
intel_agp              29319  0 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
usb_storage            50633  0 
r8169                  39714  0 
mii                     5237  1 r8169


```Thanks again

---

### Post by chili555 on 2012-06-22
Previously, you had rt2800usb *AND* rt2870sta loaded. They conflict. The usual fix is to blacklist rt2800usb and let rt2870sta do the work. Now, even rt2870sta is missing. Let's load it explicitly:```
sudo modprobe rt2870sta
```Does that help?```
iwconfig
```

---

### Post by wildmanne39 on 2012-06-22
Hi, chili555 is correct, > I think my buddy the Wild Man would like you to add another step:
I did suspect that as well, it has been a long time since I have seen this card with 10.04 so I just wanted to double check.
Thanks

---

### Post by erdibav on 2012-06-22
Now i can scan networks around me but cant connect. its trying about 1 - 2 mins and ask pass again. Double check pass and i can connect with my phone to wireless network. This iwconfig  while its trying to connect
```

root@ubuntu:/home/erdi# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"AirTies_Air4340"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 18:28:61:02:E5:98   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=100/100  Signal level:-31 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by wildmanne39 on 2012-06-22
Hi, please post the output of:
```
nm-tool
sudo iwlist scan
lsmod | grep rt2
dmesg | egrep 'rt2|wlan|wpa|etork'
```

EDIT: You can not be connected to the internet through this computer with your wired connection or phone to be able to connect with your wireless so please disconnect all other connections before trying to connect with your usb adapter and before running the above commands. 
Thanks

---

### Post by erdibav on 2012-06-22
Im trying to connect  ESSID:"AirTies_Air4340"
```


root@ubuntu:/home/erdi# nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:21:85:5B:76:DB

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.92
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220


- Device: wlan0  [Auto AirTies_Air4340] ----------------------------------------
  Type:              802.11 WiFi
  Driver:            usb
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:1F:1F:E3:3B:9F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    AirTies_Air4340: Infra, 18:28:61:02:E5:98, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ARI:             Infra, D0:15:4A:02:57:6A, Freq 2437 MHz, Rate 54 Mb/s, Strength 2 WPA
    RT-204_e_n:      Infra, 00:1C:A8:0A:82:88, Freq 2412 MHz, Rate 54 Mb/s, Strength 18 WPA WPA2
    selma:           Infra, 00:1A:2B:92:24:76, Freq 2412 MHz, Rate 54 Mb/s, Strength 23 WPA
    USR9114:         Infra, 00:14:C1:3A:4E:8D, Freq 2462 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    Babil_Film:      Infra, 00:1A:2A:87:82:70, Freq 2462 MHz, Rate 22 Mb/s, Strength 2 WPA
    Felicita Garden 1: Infra, 74:EA:3A:EC:87:7B, Freq 2437 MHz, Rate 36 Mb/s, Strength 7 WPA WPA2
    KARNAD:          Infra, 00:1A:2A:85:27:37, Freq 2462 MHz, Rate 22 Mb/s, Strength 31 WPA WPA2



``````



root@ubuntu:/home/erdi# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:2B:92:24:76
                    Protocol:802.11b/g
                    ESSID:"selma"
                    Mode:Managed
                    Channel:1
                    Quality:26/100  Signal level:-79 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 18:28:61:02:E5:98
                    Protocol:802.11b/g/n
                    ESSID:"AirTies_Air4340"
                    Mode:Managed
                    Channel:6
                    Quality:100/100  Signal level:-27 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1A:2A:85:27:37
                    Protocol:802.11b/g
                    ESSID:"KARNAD"
                    Mode:Managed
                    Channel:11
                    Quality:26/100  Signal level:-79 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:22 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1A:2A:2E:6D:AE
                    Protocol:802.11b/g
                    ESSID:"ei"
                    Mode:Managed
                    Channel:11
                    Quality:13/100  Signal level:-85 dBm  Noise level:-97 dBm
                    Encryption key:off
                    Bit Rates:22 Mb/s



``````


root@ubuntu:/home/erdi# lsmod | grep rt2
rt2870sta             525366  1 


```
```


root@ubuntu:/home/erdi# dmesg | egrep 'rt2|wlan|wpa|etork'
[    9.379139] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    9.384091] usbcore: registered new interface driver rt2870
[   22.032510] wlan0: no IPv6 routers present



```

---

### Post by wildmanne39 on 2012-06-22
Hi, unplug your wired connection then see if it will connect, I also recommend changing the encryption in your router to just wpa2.

I believe you may be having issues because of the _ in your network name remove it in the router and network manager then reboot and see if it connects.

EDIT: After you do all of that if it does not connect post the output of:
```
sudo cat /var/log/syslog | grep wlan | tail -n45
```
Thanks

---

### Post by erdibav on 2012-06-22
I remove _. And change to WPA2.
It s solved.
Thank you Wildmanne39 a lot. It takes days to solve for a linux starter.

---

### Post by wildmanne39 on 2012-06-22
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

