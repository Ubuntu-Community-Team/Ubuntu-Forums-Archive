---
title: "Problems with &quot;ASUS usb-n13&quot; usb wlan stick"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by epsilon@home on 2011-09-03
Hi,
Im a newbe and im having some troubles with my ASUS USB-N13 device.
I found some installation manuals and threads (e.g. [http://ubuntuforums.org/showthread.php?t=1419504](http://ubuntuforums.org/showthread.php?t=1419504)).
After three days of trying, i am finally able to see the available networks and i can connect to a network (after the passwd-promt it says "connected") but i think im not really online. After some minutes the  green LED on the device turn off (and stay off).

Anyone an idea?

Please consider that im really new to ubuntu (and linux).

```
lsusb
``````

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```and
```
lsmod | grep -e rt2 -e rt3
``````
rt2870sta             410104  0 
crc_ccitt              12595  2 rt2870sta,irda

```Thanx!

---

### Post by praseodym on 2011-09-03
Hello,

you stick is not shown in "lsusb". Please try another slot until it is shown.

---

### Post by epsilon@home on 2011-09-04
Oh Im sorry!
Didnt copy correctly...

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 003: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by praseodym on 2011-09-04
Ok, there it is. Please show:

```
modinfo rt2870sta | egrep 'versi|filen'
iwconfig
lsmod #completely
sudo iwlist scan
iwlist chan
rfkill list
dmesg | egrep 'rt3|rt2'
```

---

### Post by epsilon@home on 2011-09-05
Hi,
don`t know what I`ve changed but since todays morning my asus-stick works fine :popcorn:
But I still want to know if it is correctly installed.

input
```
modinfo rt2870sta | egrep 'versi|filen'
```output
```
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
srcversion:     93C0C58E1A016FE5BD4DC9F
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 
```input
```
iwconfig
```output
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"MY-SSID"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: MY-ACCESSPOINT  
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:MY-KEY
          Link Quality=100/100  Signal level:-59 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```input
```
lsmod #completely

```output
```
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
binfmt_misc            13213  1 
vesafb                 13449  1 
snd_atiixp_modem       18624  0 
snd_via82xx            24685  2 
gameport               15027  1 snd_via82xx
snd_via82xx_modem      18305  5 
snd_intel8x0m          18493  0 
snd_ac97_codec        105614  4 snd_atiixp_modem,snd_via82xx,snd_via82xx_modem,snd_intel8x0m
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  7 snd_atiixp_modem,snd_via82xx,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
nvidia               7098106  24 
snd_rawmidi            25269  2 snd_mpu401_uart,snd_seq_midi
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
i2c_viapro             12969  0 
snd_timer              28659  2 snd_pcm,snd_seq
via_ircc               26953  0 
rt2870sta             410104  1 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
irda                  185091  1 via_ircc
snd                    55295  23 snd_atiixp_modem,snd_via82xx,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_mpu401_uart,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         14073  5 snd_atiixp_modem,snd_via82xx,snd_via82xx_modem,snd_intel8x0m,snd_pcm
parport_pc             32111  1 
crc_ccitt              12595  2 irda,rt2870sta
soundcore              12600  1 snd
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  0 
uas                    17676  0 
via_rhine              27131  0 
pata_via               13368  2 
floppy                 60032  0 

```input
```
iwlist scan

```output
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: MY-ADDRESS
                    Protocol:802.11g/n
                    ESSID:"MY-SSID"
                    Mode:Managed
                    Channel:6
                    Quality:89/100  Signal level:-55 dBm  Noise level:-95 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:12:BF:E1:5F:12
                    Protocol:802.11b/g
                    ESSID:"T\xFClay"
                    Mode:Managed
                    Channel:2
                    Quality:7/100  Signal level:-87 dBm  Noise level:-95 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 1C:BD:B9:90:53:84
                    Protocol:802.11b/g/n
                    ESSID:"dlink"
                    Mode:Managed
                    Channel:6
                    Quality:31/100  Signal level:-77 dBm  Noise level:-95 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1A:4F:97:64:8E
                    Protocol:802.11b/g
                    ESSID:"WLAN-001A4F97648E"
                    Mode:Managed
                    Channel:11
                    Quality:13/100  Signal level:-85 dBm  Noise level:-95 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```input
```
iwlist chan
```output
```
lo        no frequency information.

eth0      no frequency information.

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
          Current Frequency=2.437 GHz (Channel 6)

```input
```
rfkill list
dmesg | egrep 'rt3|rt2'
```output
```
[   20.270105] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   21.302539] usbcore: registered new interface driver rt2870
[   23.964105] <==== rt28xx_init, Status=0
[   24.986944] <==== rt28xx_init, Status=0
[  273.078315] <==== rt28xx_init, Status=0

```

---

### Post by praseodym on 2011-09-05
This looks good. For better and more stable connection with Draft-N I recommend using pure WPA2-AES encryption and change the channel to "1".

---

### Post by epsilon@home on 2011-09-05
Ok.
Thank you!

---

