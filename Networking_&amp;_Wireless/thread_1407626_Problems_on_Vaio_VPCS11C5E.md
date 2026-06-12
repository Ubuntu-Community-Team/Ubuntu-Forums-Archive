---
title: "Problems on Vaio VPCS11C5E"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by kerheol on 2010-02-15
I've just installed Ubuntu 9.10 on a Vaio VPCS11C5E (2.6.31-19-generic)

Wifi doesn't work (neither sound or brightness commands). 

```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 35
       serial: 00:23:14:1e:d8:28
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:36 memory:dd100000-dd101fff
  *-network
       description: Ethernet interface
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 00:24:be:66:ae:8b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A ip=192.168.1.103 latency=0 multicast=yes
       resources: irq:37 memory:db100000-db13ffff ioport:4000(size=128)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

```
$ sudo ifconfig -a
eth0      Link encap:Ethernet  direcciónHW 00:24:be:66:ae:8b  
          Direc. inet:192.168.1.103  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::224:beff:fe66:ae8b/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:5165546 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:3211297 errores:0 perdidos:0 overruns:0 carrier:1
          colisiones:0 long.colaTX:1000 
          Bytes RX:6215843650 (6.2 GB)  TX bytes:323411397 (323.4 MB)
          Interrupción:37 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:229 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:229 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:27745 (27.7 KB)  TX bytes:27745 (27.7 KB)

pan0      Link encap:Ethernet  direcciónHW da:ca:56:af:7f:da  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

vboxnet0  Link encap:Ethernet  direcciónHW 0a:00:27:00:00:00  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  direcciónHW 00:23:14:1e:d8:28  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  direcciónHW 00-23-14-1E-D8-28-00-00-00-00-00-00-00-00-00-00  
          [NO FLAGS]  MTU:0  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
$ lsmod
Module                  Size  Used by
nls_iso8859_1           5280  1 
nls_cp437               6976  1 
vfat                   13184  1 
fat                    59832  1 vfat
usb_storage            66016  1 
binfmt_misc            10220  1 
ppdev                   8232  0 
vboxnetadp              6528  0 
vboxnetflt             14288  0 
vboxdrv              1777740  2 vboxnetadp,vboxnetflt
joydev                 13088  0 
bridge                 56384  0 
stp                     3012  1 bridge
iptable_filter          3872  0 
bnep                   15168  2 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
snd_hda_intel          31880  2 
snd_hda_codec          87584  1 snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm                93160  2 snd_hda_intel,snd_hda_codec
arc4                    2144  2 
ecb                     3296  2 
iwlagn                124832  0 
iwlcore               133600  1 iwlagn
lp                     11908  0 
mac80211              210008  2 iwlagn,iwlcore
snd_timer              26992  1 snd_pcm
uvcvideo               65260  0 
snd                    77096  9 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
sony_laptop            38104  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
nvidia              10316904  39 
sdhci_pci               8928  0 
sdhci                  20484  1 sdhci_pci
led_class               5256  2 iwlcore,sdhci
v4l2_compat_ioctl32    13344  1 videodev
soundcore               9088  1 snd
cfg80211              109144  3 iwlagn,iwlcore,mac80211
psmouse                57124  0 
serio_raw               6596  0 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
atl1c                  36516  0 
btusb                  14260  2 
parport                40528  2 ppdev,lp
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
video                  23612  0 
ohci1394               33780  0 
output                  3680  1 video
intel_agp              32816  0 
ieee1394              100896  1 ohci1394
```

Ethernet works correctly.

Can someone help me or just give me some path to follow?

---

### Post by kerheol on 2010-02-15
Sound works now with last alsa drivers and adding

```
options snd-hda-intel model=sony-assamd
```

to /etc/modprobe.d/alsa-base.conf

Anyone can help with WiFi pls???

---

### Post by Sylslay on 2010-02-15
looks like wlan0 is on list, (it has some driver for wi-fi card)

meaby try:

switch on/off manual swiitch for wifi, and 

ifconfig wlan0 up

iwlist wlan0 scanning

iwlist wlan0 scanning >net.txt 

switch to channel witch You need.

iwconfig wlan0 channel 11

---

### Post by kerheol on 2010-02-16
> **Sylslay said:**
> looks like wlan0 is on list, (it has some driver for wi-fi card)

meaby try:

switch on/off manual swiitch for wifi, and 

ifconfig wlan0 up

iwlist wlan0 scanning

iwlist wlan0 scanning >net.txt 

switch to channel witch You need.

iwconfig wlan0 channel 11

Didn't work...

```
$ifconfig wlan0 up
SIOCSIFFLAGS: No existe el fichero ó directorio

```

"No existe el fichero ó directorio" => File doesn't exist

```
$iwlist wlan0 scanning
wlan0     Interface doesn't support scanning : Network is down
```

```
$iwconfig wlan0 channel 11
```

(no output)

---

### Post by kerheol on 2010-02-16
Solved!! So simple.. (if you know what to do, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496496](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496496))

```
$sudo apt-get install linux-backports-modules-karmic
```

---

### Post by pugacioff on 2010-02-26
> **kerheol said:**
> Sound works now with last alsa drivers and adding

```
options snd-hda-intel model=sony-assamd
```

to /etc/modprobe.d/alsa-base.conf

Anyone can help with WiFi pls???

Hello, which version of alsa drivers did you install? I'm running kubuntu lucid alpha 3 and sound doesn't work yet. 

btw, do you have a model w/ backlit keyboard? did you figure out how to turn off the light? mine is vpc S11F7E.

---

### Post by pugacioff on 2010-02-26
> **pugacioff said:**
> Hello, which version of alsa drivers did you install? I'm running kubuntu lucid alpha 3 and sound doesn't work yet.

I have to correct this. Sound does work, but volume was ridiculously low! adjusting it in alsamixer solved the issue.

---

### Post by zopen on 2010-02-27
> **kerheol said:**
> Sound works now with last alsa drivers and adding

```
options snd-hda-intel model=sony-assamd
```to /etc/modprobe.d/alsa-base.conf

Anyone can help with WiFi pls???

I have also a VPCS11C5E. My problems with wifi were automatically solved by installing wicd. After that it was detected and working. 


Please, Can you repeat your process to add alsa?.  I don't have success with this :(

---

### Post by kerheol on 2010-03-06
download last drivers from [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

---

