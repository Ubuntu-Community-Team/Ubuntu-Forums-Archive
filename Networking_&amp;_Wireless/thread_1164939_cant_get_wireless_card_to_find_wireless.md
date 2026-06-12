---
title: "cant get wireless card to find wireless"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by rhyz on 2009-05-20
i have a buffalo melco wli-pcm-L11 works fine. but when this is plugged in i get another wireless device.

wistron neweb bcm4306 802.11b/g which i belive is the built in broadcom.

when the melco is taken out the other card does not shoe i have installed ndiswrapper and the driver and as far as i can tell all went well.

i would like to be using the built in broadcom and i think i am almost there with getting it to work.

iwconfig

```

rhys@rhys-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"xxx"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: xxx   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=14/92  Signal level=-70 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:14
          Tx excessive retries:16  Invalid misc:0   Missed beacon:0

```

iwlist scanning

```

rhys@rhys-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:07:40:A0:69:17
                    ESSID:"0007409647D8"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Signal level:-71 dBm  Noise level:-80 dBm
                    Encryption key:on
                    Extra: Last beacon: 64460ms ago
          Cell 02 - Address: 00:1C:DF:76:C6:C9
                    ESSID:"Avenue23"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:-87 dBm  Noise level:-89 dBm
                    Encryption key:on
                    Extra: Last beacon: 64460ms ago

```


thanks in advance

---

### Post by superprash2003 on 2009-05-20
is this a laptop?? most laptops come with a wireless switch ( as in , one with an on/off option) , so ensure that is set to ON

---

### Post by rhyz on 2009-05-20
yes it is a laptop and there is a switch and it is in the on position
also tried the off position :)

there is a wireless led but that never lights up

---

### Post by rhyz on 2009-05-21
Bumpidge :)

---

### Post by superprash2003 on 2009-05-21
try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

