---
title: "Atheros AR5212 won't connect to wifi network"
date: 2013-02-03
forum: Networking &amp; Wireless
---

### Post by ritchierope on 2013-02-03
Hello Everyone,

i am having a very troubling problem with my Atheros AR5212 wireless card. The issue is that since ubuntu 12.04 (any derivative) I cannot connect to my router.  As network manager asks for my password, I paste it from leafpad, the icon indicates that it is connecting but then it won't. (in addition it also kills the wifi connection on every laptop for 1-2 minutes)

I have been googling around for 2 days to solve it, the only thing that helped was installing the madwifi driver, which only worked till I yesterday suspended the computer, then the issue came back again, even after restart. Since then even if I do the steps again, the card won't connect.

Here's the guide I used for installing:  (worked brilliantly on elementary Luna beta - based on 12.04 LTS)
```
http://ubuntucrack.blogspot.hu/2010/07/howto-install-madwifi-drivers-for.html
```It seems to me that the system still wants to use the ath driver instead of madwifi.
It's an IBM ThinkPad T43, I am using xubuntu 12.04.

lspci:
```
04:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
```lspci -nn | grep 'Wireless Brand'
```
04:02.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212 802.11abg NIC [168c:1014] (rev 01)
```ifconfig
```

wifi0     Link encap:UNSPEC  HWaddr 00-0E-9B-A3-CB-4F-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5454 errors:0 dropped:0 overruns:0 frame:1035
          TX packets:1037 errors:7 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:2609512 (2.6 MB)  TX bytes:76898 (76.8 KB)
          Interrupt:21 

```iwconfig
```

wifi0     no wireless extensions.

lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"\x08p\xD4\xB2\x8A)TH\x9A\x0A\xBC\xD5\x0E\x18\xA8D\xAC[\xF3\x8EL\xD7-\x9B\x09B\xE5\x06\xC43\xAF\xCD"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:153  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```iwconfig wlan0
```

wlan0     No such device

```lsmod
```

Module                  Size  Used by
btusb                  17948  0 
joydev                 17393  0 
rfcomm                 38139  4 
bnep                   17830  2 
bluetooth             158479  11 btusb,rfcomm,bnep
pcmcia                 39826  0 
snd_intel8x0           33455  4 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  3 snd_intel8x0,snd_ac97_codec
ppdev                  12849  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
radeon                733824  2 
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                96718  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
thinkpad_acpi          73942  1 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              13027  0 
snd                    62218  17 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,thinkpad_acpi,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
nsc_ircc               23240  0 
soundcore              14635  1 snd
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
irda                  185517  1 nsc_ircc
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
drm                   197641  4 radeon,ttm,drm_kms_helper
nvram                  14029  1 thinkpad_acpi
parport_pc             32114  1 
video                  19068  0 
crc_ccitt              12627  1 irda
wlan_scan_sta          21921  1 
ath_rate_sample        17279  1 
mac_hid                13077  0 
i2c_algo_bit           13199  1 radeon
ath_pci               187734  0 
wlan                  221056  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               398486  3 ath_rate_sample,ath_pci
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
floppy                 60184  0 
tg3                   137273  0 

```lsmod | grep "wlan_scan_sta"
```

wlan_scan_sta          21921  1 
wlan                  221056  4 wlan_scan_sta,ath_rate_sample,ath_pci

```lsmod | grep "ath_rate_sample"
```

ath_rate_sample        17279  1 
wlan                  221056  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               398486  3 ath_rate_sample,ath_pci

```lsmod | grep "ath_pci"
```

ath_pci               187734  0 
wlan                  221056  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               398486  3 ath_rate_sample,ath_pci

```dmesg
[http://pastebin.com/fq0Mq8Lt](http://pastebin.com/fq0Mq8Lt)

sudo lshw -C network
```

PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 00:11:25:49:5e:8d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5751m-v3.40a ip=192.168.9.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:a8200000-a820ffff
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: wifi0
       version: 01
       serial: 00:0e:9b:a3:cb:4f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: irq:21 memory:a8400000-a840ffff
```iwlist scan
```

wifi0     Interface doesn't support scanning.

lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:0F:B5:E3:AA:0A
                    ESSID:"zoleHOME"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-40 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f0101001dff7f
          Cell 02 - Address: 00:0F:B5:E3:AA:0A
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-46 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f0101001dff7f
          Cell 03 - Address: F4:EC:38:FE:77:D4
                    ESSID:"HerczegNet"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101010003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f01010000ff7f
          Cell 04 - Address: 00:02:6F:4A:D9:B3
                    ESSID:"VECSES-1"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-71 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:02:6F:4A:D9:D0
                    ESSID:"VECSES-3"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=10/70  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s
                    Extra:bcn_int=100

```Description:    Ubuntu 12.04.2 LTS
3.2.0-37-generic i686


Thank you for your help in advance!

---

### Post by ritchierope on 2013-02-12
After doing the installation according to the guide a couple of times it seems to be working stable now, it connects after every login fine. Now I only want to know why I had to go through all this to get it working. I had no problem with this wireless card in any of the ubuntu versions but now I have with every one after 12.04.

As I have read madwifi was a dead project already, I don't know how it is going to work in the future, but I seriously hope that the native linux driver of the card gets fixed sometime.

---

