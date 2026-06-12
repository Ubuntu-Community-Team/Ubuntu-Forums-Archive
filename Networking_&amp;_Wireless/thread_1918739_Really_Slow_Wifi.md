---
title: "Really Slow Wifi"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by -Ziggy- on 2012-02-01
I'm having problems with my wi-fi and I am pretty sure it is a Linux problem, because I'm using the same wifi in another computer with Windows and I don't have any wi-fi problem with that one. 

The problem I'm having is that my wi-fi, although sometimes works flawesly, other times turns out to be reaaally slow (as low as 5 Kb/s). It happens sometimes, from one minute to another, without any cause I can identify. And the wi-fi even disconnects automatically sometimes!

I've done lspci | grep Network and the result I get is this:
Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

I've tried Ubuntu 11.04 and 11.10 and the problem is still the same. I also tried upgrading the kernel to 2.6.39 and have madwifi installed. What else can I do?

---

### Post by praseodym on 2012-02-01
Hi,

please show:
```
uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
sudo iwlist scan
grep ath /etc/modprobe.d/*
```

---

### Post by Cookieh on 2012-02-01
Firstly, Im not that great at Atheros, but try to enter it in Master mode as MadWifi supports proprietary code (via HAL) but covers more chipsets and also supports the "master" mode.

Secondly, try to run these at terminal at copy & paste them back here:

Code:
```
lsmod
```
```
iwconfig
```
```
ifconfig -a
```
```
sudo lshw -c network
```
```
rfkill list all
```

---

### Post by -Ziggy- on 2012-02-01
> uname -a
2.6.39-020639rc4-generic #201104191410 SMP Tue Apr 19 15:45:56 UTC 2011 i686 i686 i386 GNU/Linux



> lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8367]
	Kernel driver in use: r8169
--
05:01.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
	Subsystem: Atheros Communications Inc. TRENDnet TEW-443PI Wireless PCI Adapter [168c:2051]
	Kernel driver in use: ath5k
	Kernel modules: ath5k



> lsmod
Module                  Size  Used by
snd_seq_dummy          12716  0 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17447  1 
fat                    55812  1 vfat
binfmt_misc            17374  1 
vboxnetadp             13348  0 [permanent]
vboxnetflt             27855  0 [permanent]
vboxdrv               238417  2 vboxnetadp,vboxnetflt,[permanent]
parport_pc             32578  0 
dm_crypt               23043  0 
ppdev                  12869  0 
snd_hda_codec_via      58295  1 
nvidia               9766978  60 [permanent]
snd_hda_intel          33132  2 
snd_hda_codec          93180  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13413  1 snd_hda_codec
snd_pcm                81557  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13170  0 
snd_rawmidi            25327  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51702  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
snd_timer              29140  2 snd_pcm,snd_seq
snd_seq_device         14160  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
ipheth                 13340  0 
snd                    56136  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath5k                 145805  0 
soundcore              12600  1 snd
lp                     13412  0 
ath                    19681  1 ath5k
mac80211              270528  1 ath5k
cfg80211              158228  3 ath5k,ath,mac80211
psmouse                65817  0 
parport                41188  3 parport_pc,ppdev,lp
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
asus_atk0110           18012  0 
serio_raw              13094  0 
joydev                 17679  0 
btrfs                 578616  0 
zlib_deflate           26725  1 btrfs
libcrc32c              12543  1 btrfs
hid_microsoft          12703  0 
usbhid                 42613  0 
hid                    77797  2 hid_microsoft,usbhid
usb_storage            44354  1 
floppy                 60478  0 
uas                    17784  0 
r8169                  49333  0 
pata_marvell           12756  0 



> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"WLAN_81"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:02:CF:B7:95:C8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:126  Invalid misc:276   Missed beacon:0



> sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:02:CF:B7:95:C8
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"WLAN_81"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002bd84c0fe0
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 0007574C414E5F3831
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

vboxnet0  Interface doesn't support scanning.



> grep ath /etc/modprobe.d/*
/etc/modprobe.d/blacklist-ath_pci.conf:# which ath5k cannot recover. To prevent this condition, stop
/etc/modprobe.d/blacklist-ath_pci.conf:blacklist ath_pci



> ifconfig -a
eth0      Link encap:Ethernet  direcciónHW 00:23:54:5c:c9:df  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:44 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:9336 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:9336 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:472467 (472.4 KB)  TX bytes:472467 (472.4 KB)

vboxnet0  Link encap:Ethernet  direcciónHW 0a:00:27:00:00:00  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  direcciónHW 00:23:cd:f7:43:56  
          Direc. inet:192.168.1.41  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::223:cdff:fef7:4356/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:148115 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:89504 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:196013133 (196.0 MB)  TX bytes:11767679 (11.7 MB)



> sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:54:5c:c9:df
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:d800(size=256) memory:f8eff000-f8efffff memory:f8ee0000-f8eeffff memory:fe9f0000-fe9fffff
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wlan0
       version: 01
       serial: 00:23:cd:f7:43:56
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.39-020639rc4-generic firmware=N/A ip=192.168.1.41 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:febf0000-febfffff



> rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no



:)

---

### Post by -Ziggy- on 2012-02-02
Any help, please?

---

### Post by 1turk2rule on 2012-02-02
I have the same problem on my asus eee pc 1005ha netbook.I run both win7 and ubuntu 11.10 and with win7 my wifi speed is perfect but when i use ubuntu the dl speed doesnt even reach 5kb/s. (I use a BT router)  please help

---

### Post by -Ziggy- on 2012-02-03
OK, last try. Can somebody help please?

---

### Post by kurt18947 on 2012-02-03
> **-Ziggy- said:**
> OK, last try. Can somebody help please?

I'm not sure I'll have time to research but have you looked at turning hardware encryption off?  Atheros chips have a problem like you're having and using software encryption instead of hardware encryption solves the speed problem.

Okay, this is a different adapter that uses ath9k instead of ath5k but it might be worth a shot.  Here's a thread about a similar problem:
[http://ubuntuforums.org/showthread.php?t=1877120&highlight=hwcrypt](http://ubuntuforums.org/showthread.php?t=1877120&highlight=hwcrypt)
You could probably try similar but substitute ath5k for ath9k and see if it helps.  If it doesn't NDISwrapper while not my favorite solution might be worth a try as well but it may well make a hash of your existing WiFi configuration.

---

### Post by raja.genupula on 2012-02-03
look at this thread also . 

[http://ubuntuforums.org/showthread.php?t=1917310](http://ubuntuforums.org/showthread.php?t=1917310)

---

