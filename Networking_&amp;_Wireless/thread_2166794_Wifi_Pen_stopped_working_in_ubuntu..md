---
title: "Wifi Pen stopped working in ubuntu."
date: 2013-08-11
forum: Networking &amp; Wireless
---

### Post by eoin_fanning on 2013-08-11
Hi my wifi pen has stopped working in ubuntu. Works fine on another computer. and wired connection works on ubuntu. ive tried everything i can see in forums and even have done full 12.04 lts reinstall. please help if you can.

cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux IXTREME 3.2.0-51-generic-pae #77-Ubuntu SMP Wed Jul 24 20:40:32 UTC 2013 i686 i686 i386 GNU/Linux
```

lspci -nnk | grep -iA2 net
```
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c)
    Subsystem: Packard Bell B.V. Device [1631:e028]
    Kernel driver in use: via-rhine


```

lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1044:8008 Chu Yuen Enterprise Co., Ltd GN-WB01GS
Bus 001 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 002 Device 002: ID 1631:0121 Good Way Technology 
Bus 001 Device 006: ID 040b:650a Weltrend Semiconductor 
Bus 002 Device 003: ID 1631:0601 Good Way Technology 
Bus 002 Device 004: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 002 Device 005: ID 08ff:1600 AuthenTec, Inc. AES1600

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

rfkill list all
```
nothing comes up
```

lsmod
```
Module                  Size  Used by
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
vesafb                 13516  1 
binfmt_misc            17292  1 
snd_hda_codec_realtek   174313  1 
nvidia              10286823  40 
snd_hda_codec_hdmi     31775  1 
psmouse                86520  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_hda_intel          32719  5 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hda_codec         109562  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              13027  0 
i2c_viapro             12969  0 
snd_timer              28931  2 snd_seq,snd_pcm
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 41937  0 
hid                    77428  1 usbhid
snd                    62218  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_timer,snd_seq_device
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
shpchp                 32265  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  0 
via_rhine              27413  0 
firewire_ohci          40172  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_via               13428  0 
sata_via               13495  2 


```

---

### Post by chili555 on 2013-08-11
> ID 1044:8008 Chu Yuen Enterprise Co., Ltd GN-WB01GSPlease see: [https://wiki.debian.org/WiFi/rt73](https://wiki.debian.org/WiFi/rt73)

Your device is supposed to work with the driver rt73usb: ```
$ modinfo rt73usb
filename:       /lib/modules/3.8.0-27-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2E608E96EF83A1F08EC0764
<snip>
alias:          usb:v[COLOR="#FF0000"]1044[/COLOR]p[COLOR="#FF0000"]8008[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
<snip>

```Does your device start working again if you simply load the driver?```
sudo modprobe rt73usb
```If so, let's get it to load automatically:```
sudo -i
echo rt73usb >> /etc/modules
exit
```If that doesn't help, post back with:```
dmesg | grep -e rt2 -e rt7
```Thanks.

---

### Post by eoin_fanning on 2013-08-11
Thank you very much for your help. Nothing happened when i did 
sudo modprobe rt73usb

i just asked for password and then nothing





dmesg | grep -e rt2 -e rt7```
[27862.052764] Registered led device: rt73usb-phy0::radio
[27862.052803] Registered led device: rt73usb-phy0::assoc
[27862.052838] Registered led device: rt73usb-phy0::quality
[27862.055001] usbcore: registered new interface driver rt73usb


```

---

### Post by chili555 on 2013-08-11
Was a wireless interface created?```
iwconfig
```What does this tell us?```
nm-tool
```

---

### Post by eoin_fanning on 2013-08-12
sorry for delay just home from work

```
jester@IXTREME:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jester@IXTREME:~$ sudo modprobe rt73usb
[sudo] password for jester: 
jester@IXTREME:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

jester@IXTREME:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             disconnected
  Default:           no
  HW Address:        00:14:85:D8:FF:82

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             connected
  Default:           yes
  HW Address:        00:16:17:E9:06:4A

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         87.198.111.147
    Prefix:          24 (255.255.255.0)
    Gateway:         87.198.111.1

    DNS:             85.91.1.128
    DNS:             85.91.1.130


jester@IXTREME:~$ 


```

---

### Post by eoin_fanning on 2013-08-12
also please note i think rt73usb was a windows driver i downloaded when trying to fix this myself.  also please note i ordered this [TP Link TL-WDN3800 N600 Wireless Dual Band PCI Express Adapter]("http://www.amazon.co.uk/dp/B00A0VCHQE/ref=pe_385721_37986871_pe_364681_36330151_item")    before i started talking with you in the hope it would fix my problem if you think it would be easier to wait for it to arrive let me know.

---

### Post by chili555 on 2013-08-12
It's probably no easier or harder than the other! 

rt73usb is a native Linux driver.

Please detach the ethernet and then run and post:```
sudo iwlist wlan0 scan
dmesg | grep -e rt2 -e rt7
```Thanks.

---

### Post by eoin_fanning on 2013-08-14
i did everthing you said in order again then

unpluged and ran what you aked see below

Thanks again for your help 

```
jester@IXTREME:~$ sudo modprobe rt73usb
[sudo] password for jester: 
jester@IXTREME:~$ dmesg | grep -e rt2 -e rt7
[11716.875323] Registered led device: rt73usb-phy0::radio
[11716.875357] Registered led device: rt73usb-phy0::assoc
[11716.875390] Registered led device: rt73usb-phy0::quality
[11716.877037] usbcore: registered new interface driver rt73usb
jester@IXTREME:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

jester@IXTREME:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             disconnected
  Default:           no
  HW Address:        00:14:85:D8:FF:82

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             connected
  Default:           yes
  HW Address:        00:16:17:E9:06:4A

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         87.198.127.246
    Prefix:          25 (255.255.255.128)
    Gateway:         87.198.127.129

    DNS:             85.91.1.128
    DNS:             85.91.1.130


jester@IXTREME:~$ sudo iwlist wlan0 scan
wlan0     No scan results

jester@IXTREME:~$ dmesg | grep -e rt2 -e rt7
[11716.875323] Registered led device: rt73usb-phy0::radio
[11716.875357] Registered led device: rt73usb-phy0::assoc
[11716.875390] Registered led device: rt73usb-phy0::quality
[11716.877037] usbcore: registered new interface driver rt73usb
jester@IXTREME:~$ 


```

---

### Post by eoin_fanning on 2013-08-14
The computer had been running for a good while when i came to it and light on wifi pen was flashing when i started at the end it was not flashing anymore.

---

### Post by chili555 on 2013-08-14
> - Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  [COLOR="#FF0000"]State:             connected[/COLOR]
  Default:           yes
  HW Address:        00:16:17:E9:06:4A

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         87.198.127.246
    Prefix:          25 (255.255.255.128)
    Gateway:         87.198.127.129It sure looks like the ethernet is still connected. Please detach the ethernet cable and run and post:```
sudo iwlist wlan0 scan
dmesg | grep wlan
ifconfig
```Network Manager is designed to default to ethernet instead of wireless if it is connected and it is. Thanks.

It looks like you have a public IP address, from a DSL or cable modem instead of a router. What is the wireless device you are trying to connect to?

---

### Post by eoin_fanning on 2013-08-15
i was pretty sure i disconneted when i ran that lst night

```
jester@IXTREME:~$ sudo iwlist wlan0 scan
[sudo] password for jester: 
Sorry, try again.
[sudo] password for jester: 
wlan0     Interface doesn't support scanning.

jester@IXTREME:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

jester@IXTREME:~$ dmesg | grep wlan
jester@IXTREME:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:e9:06:4a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:341561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198071 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:510064195 (510.0 MB)  TX bytes:15383697 (15.3 MB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:983170 (983.1 KB)  TX bytes:983170 (983.1 KB)

jester@IXTREME:~$ 


```

---

### Post by eoin_fanning on 2013-08-15
its a telsey provided by my broad band provider

model:cpva642
type: cpa-znte7
ver:otuk

---

### Post by eoin_fanning on 2013-08-15
its a telsey provided by my broad band provider

model:cpva642
type: cpa-znte7

---

### Post by eoin_fanning on 2013-08-17
Hey great news my s [TP Link TL-WDN3800 N600 Wireless Dual Band PCI Express Adapter]("http://www.amazon.co.uk/dp/B00A0VCHQE/ref=pe_385721_37986871_pe_364681_36330151_item") arrive plugged it in turned on computer and boom i have wireless again! Thanks for all your help and advice it would have been nice to figure out what the problem was. but now i dont have wires running across my house 

Thank you very much

---

### Post by chili555 on 2013-08-18
Glad everything is working.

---

