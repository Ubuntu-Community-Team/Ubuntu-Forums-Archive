---
title: "Need help with using USB Wireless Adaptor(RT3070) as Access Point on Ubuntu 10.04 LTS"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by kokenn2008 on 2013-01-30
I have a problem of setting access point with an USB Wireless Adaptor(RT3070) on linux 2.6.
I tried the following steps, tut I still cannot find any access point from my iPhone and iPad.
Where is wrong? 

-------------------------------------------
Step 0. Confirm environment

Environment is Ubuntu 10.04 LTS.

```
$ lsusb

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0411:01ee MelCo., Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
$ uname -r

2.6.32-38-generic
```

-------------------------------------------
Step 1. Download linux driver

Download the following driver from [http://www.mediatek.com/](http://www.mediatek.com/)

2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.bz2

-------------------------------------------
Step 2. Modify rtusb_dev_id.c

I added the following line to common/rtusb_dev_id.c


```
    {USB_DEVICE(0x0411,0x01EE)}, /* Buffalo WLI-UC-GNM2 */
#endif /* RT3070 */
```

-------------------------------------------
Step 3. Modify config.mk

Also I changed the setting in os/linux/config.mk

```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y


# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

-------------------------------------------
Step 4. Copy RT2870STA.dat

$sudo cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat

-------------------------------------------
Step 5. Build dirver and insert it

```
$sudo make
$sudo make install
```

go to "os/linux/" directory.

```
$sudo insmod rt5370sta.ko

$ lsmod | grep rt
rt5370sta             717049  0 
gameport                9089  1 snd_ens1371
parport_pc             25962  1 
agpgart                31724  1 intel_agp
parport                32635  3 ppdev,parport_pc,lp
scsi_transport_spi     21096  1 mptspi
```

-------------------------------------------
Step 6. Make adaptor up

Insert my USB Wireless Adaptor (Buffalo WLI-UC-GNM2).

```
$ifconfig -a

ra0       Link encap:Ethernet  HWaddr 10:6f:3f:46:ea:02  
          inet6 addr: fe80::126f:3fff:fe46:ea02/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


```
$sudo ifconfig ra0 up
$iwconfig

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

-------------------------------------------
Step 7. Try to scan access points

Try to make it work as wifi client to scan wifi access point.

```
$ sudo iwconfig ra0 mode Monitor
$ iwconfig

ra0       Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Monitor  Frequency=2.412 GHz  Access Point: 7A:43:85:D5:62:85   
          Bit Rate=150 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
$ iwlist scan
ra0       Scan completed :
          Cell 01 - Address: 00:19:C8:04:XX:XX
                    Protocol:802.11b/g/n
                    ESSID:"XXXXXXXXXXXXXX"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/100  Signal level=-69 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 02 - Address: 9C:D2:4B:B6:XX:XX
                    Protocol:802.11b/g
                    ESSID:"007Z_XXXXXXXXXXX"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=100/100  Signal level=-27 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: Unknown: DD0E0050F204104A0001101044000102
```

-------------------------------------------
Step 8. Try to make adaptor work as access point ( Failed )

```
$ sudo iwconfig ra0 mode managed
$ sudo iwconfig ra0 ap 7A:43:85:D5:62:85
$ sudo iwconfig ra0 key open

```
Now I check available wifi access points by iPhone and iPad.
No access point "11n-AP" found.

```
$ iwconfig

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 7A:43:85:D5:62:85   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```
$ dmesg

[ 5568.409472] #
[ 5568.492660] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 5572.655589] RTMP_TimerListAdd: add timer obj e0a7fa34!
[ 5572.655661] RTMP_TimerListAdd: add timer obj e0a7fa78!
[ 5572.655701] RTMP_TimerListAdd: add timer obj e0a7fabc!
[ 5572.655709] RTMP_TimerListAdd: add timer obj e0a7f9f0!
[ 5572.655713] RTMP_TimerListAdd: add timer obj e0a7f924!
[ 5572.655716] RTMP_TimerListAdd: add timer obj e0a7f968!
[ 5572.655719] RTMP_TimerListAdd: add timer obj e0a4a50c!
[ 5572.655722] RTMP_TimerListAdd: add timer obj e0a39de4!
[ 5572.655725] RTMP_TimerListAdd: add timer obj e0a39e30!
[ 5572.655728] RTMP_TimerListAdd: add timer obj e0a4a5ec!
[ 5572.655731] RTMP_TimerListAdd: add timer obj e0a4a484!
[ 5572.655735] RTMP_TimerListAdd: add timer obj e0a4a5a4!
[ 5572.687769] -->RTUSBVenderReset
[ 5572.689754] <--RTUSBVenderReset
[ 5580.819692] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[ 5580.819733] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[ 5580.821541] Key1Str is Invalid key length(0) or Type(0)
[ 5580.821588] Key2Str is Invalid key length(0) or Type(0)
[ 5580.821633] Key3Str is Invalid key length(0) or Type(0)
[ 5580.821679] Key4Str is Invalid key length(0) or Type(0)
[ 5580.823475] 1. Phy Mode = 5
[ 5580.823481] 2. Phy Mode = 5
[ 5580.824160] NVM is Efuse and its size =2d[2d0-2fc] 
[ 5581.732646] phy mode> Error! The chip does not support 5G band 5!
[ 5581.732732] RTMPSetPhyMode: channel is out of range, use first channel=1 
[ 5581.791312] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 5582.157269] 3. Phy Mode = 9
[ 5582.197224] AntCfgInit: primary/secondary ant 0/1
[ 5582.197228] MCS Set = ff 00 00 00 01
[ 5582.991471] <==== rt28xx_init, Status=0
[ 5583.015043] 0x1300 = 000a4300
[ 5588.900248] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1887
[ 5593.141191] ra0: no IPv6 routers present
[ 5595.133167] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1911
[ 5601.572219] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 2173
[ 5606.928392] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 2173
[ 5636.958410] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 2399
[ 5660.642092] #

```

---

