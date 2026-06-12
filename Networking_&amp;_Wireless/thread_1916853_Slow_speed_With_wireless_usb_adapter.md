---
title: "Slow speed With wireless usb adapter"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by roblikestacos on 2012-01-28
Hello
I just installed Ubuntu 11.10 on my desktop and i plugged in my TL-WN422G wirelesss adapter... the problem comes when i try to open a web with mozilla, it takes like 2 minutes and all my downloads are too slow... with windows 7 i had like 500 kb/s now i have like 10kb/s i tried disabling ipv6.. that doesn't work for me.. i think there is a problem with the drivers or something.. what should i do?
Thanks in advance.:D

---

### Post by varunendra on 2012-01-29
Hi roblikestacos, Welcome to the forums :)

Please open a terminal (Ctrl+Alt+T) and run and post outputs of the following commands:
```
uname -mr
lsusb
sudo lshw -C network
lsmod
ifconfig -a
iwconfig
cat /etc/resolv.conf
ping -c 4 google.com
```

To post the outputs, click on the **# **symbol at the top of the edit box (in which you create new posts) to generate [ code]..[ /code] tags, then copy-paste (only) the outputs in-between the code tags.

---

### Post by roblikestacos on 2012-01-29
Hi varunendra :), here it is
Uname -mr:
```
3.0.0-12-generic i686
```
lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0cf3:1006 Atheros Communications, Inc. TP-Link TL-WN322G v3 / TL-WN422G v2 802.11g [Atheros AR9271]
Bus 002 Device 003: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 004 Device 002: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 004 Device 003: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 004 Device 004: ID 413c:2010 Dell Computer Corp. Keyboard
```
sudo lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:95:2f:69
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=1.1-2 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:ff00(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:3
       logical name: wlan0
       serial: 74:ea:3a:87:24:fe
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=3.0.0-12-generic firmware=1.3 ip=192.168.1.107 link=yes multicast=yes wireless=IEEE 802.11bgn
lsmod:
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
arc4                   12473  2 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
ath9k_htc              90775  0 
mac80211              272785  1 ath9k_htc
ath9k_common           13599  1 ath9k_htc
ath9k_hw              293893  2 ath9k_htc,ath9k_common
ath                    19387  2 ath9k_htc,ath9k_hw
dcdbas                 14098  0 
cfg80211              172392  3 ath9k_htc,mac80211,ath
joydev                 17393  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_hda_codec_realtek   254125  1 
binfmt_misc            17292  1 
snd_hda_intel          24262  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
psmouse                73673  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              12990  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28932  2 snd_seq,snd_pcm
snd                    55902  16 snd_hda_codec_hdmi,snd_rawmidi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
radeon                925020  3 
soundcore              12600  1 snd
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm                   192226  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  0 
uas                    17699  0 
floppy                 60310  0 
e1000e                139775  0
```
ifconfig -a
```
eth0      Link encap:Ethernet  direcciónHW 00:1a:a0:95:2f:69  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:20 Memoria:fdfc0000-fdfe0000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  direcciónHW 74:ea:3a:87:24:fe  
          Direc. inet:192.168.1.107  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::76ea:3aff:fe87:24fe/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:246 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:316 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:243932 (243.9 KB)  TX bytes:48734 (48.7 KB)
iwconfig
eth0      Link encap:Ethernet  direcciónHW 00:1a:a0:95:2f:69  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:20 Memoria:fdfc0000-fdfe0000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  direcciónHW 74:ea:3a:87:24:fe  
          Direc. inet:192.168.1.107  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::76ea:3aff:fe87:24fe/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:246 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:316 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:243932 (243.9 KB)  TX bytes:48734 (48.7 KB)
```

roberto@roberto-Inspiron-530:~$ iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"INFINITUM6db7"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 4C:54:99:7D:FD:08   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:3   Missed beacon:0
```
cat /etc/resolv.conf
```
# Generated by NetworkManager
nameserver 192.168.1.254
```
ping -c 4 google.com 
```
PING google.com (74.125.227.17) 56(84) bytes of data.
64 bytes from 74.125.227.17: icmp_req=1 ttl=54 time=54.0 ms

--- google.com ping statistics ---
4 packets transmitted, 1 received, 75% packet loss, time 17066ms
rtt min/avg/max/mdev = 54.065/54.065/54.065/0.000 ms
```

Sorry if it's wrong, i copied a .txt to my cellphone and then i wrote the code manually.
Some parts seems to be in spanish, i hope that isn't a problem..
Thanks :)

---

### Post by varunendra on 2012-01-29
> **roblikestacos said:**
> i copied a .txt to my cellphone and then i wrote the code manually.
Some parts seems to be in spanish, i hope that isn't a problem..
No problem at all:) Actually you did quite an impressive job if you did it manually :)

Onto the problem-

1) Try this-
```
sudo modprobe -rfv ath9k_htc
sudo modprobe -v ath9k_htc nohwcrypt=1
```
Do NOT restart, wait a couple of minutes and connect again to see if the speed improves. Post back whatever be the result.

2) It may not be related, but IPv6 doesn't seem to be disabled yet (if I am understanding the "Dirección inet6:..." part correctly). If it doesn't worsen things, you can safely turn it off permanently. Just to be sure.. You can do so using any of these methods:
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

If successfully disabled, you won't see any 'inet6...' line in the output of ifconfig.

---

### Post by roblikestacos on 2012-01-29
hello :D
nope, it seems that it doesn't worked...

sudo modprobe -rfv ath9k_htc
```
rmmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
rmmod /lib/modules/3.0.0-12-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
rmmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
rmmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.0.0-12-generic/kernel/net/wireless/cfg80211.ko
```
sudo modprobe -v ath9k_htc nohwcrypt =1
```
insmod /lib/modules/3.0.0-12-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.0.0-12-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko nohwcrypt =1
FATAL: Error inserting ath9k_htc (/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko): Invalid argument
```
i see the Fatal error, that could be the problem.. but i don't know what it means.. maybe you know..
thanks in advance :)

---

### Post by roblikestacos on 2012-01-29
hey there, i just installed something called ath9k.. now i try this
sudo modprobe -rfv ath9k_htc
sudo modprobe -v ath9k_htc nohwcrypt=1
the outpost is the same except for the fatal error, but it still doesn't work, the internet speed stays at 1 - 10 kb/s :(
only when i connect to another network it jumps to 4 mb/s but then it slows down... i checked that with the system monitor...

---

### Post by varunendra on 2012-01-29
> **roblikestacos said:**
> hello :D
nope, it seems that it doesn't worked... hmm.. people usually show such a big smile only if their problem is solved,.... you seem different ;)

However, just a minor mistake you need to correct-
> **roblikestacos said:**
> modprobe -v ath9k_htc [COLOR=Red]**nohwcrypt =1**[/COLOR]
.. there should be [COLOR=Red]NO SPACE[/COLOR] between 'nohwcrypt' and '=1'
So retry with that correction (or just copy-paste the commands to avoid typing errors), and post back how it goes.

> **roblikestacos said:**
> **Invalid argument**[/CODE]i see the Fatal error, that could be the problem.. but i don't know what it means.. maybe you know..
now you know too.. 'nohwcrypt=1' was the argument which modprobe couldn't understand since it was typed incorrectly. :)

 Let me tell you in advance though - this is most often a hit or miss case - that is, may work, maybe not. There can be several reasons for  slow speeds, and hardware encryption is just one of them which we are  trying to disable here.

---

### Post by roblikestacos on 2012-01-30
Hey there, i just tried that, and everything seems fine, no errors this time, but also is still not working.. what else can i try? 
Thanks in advance.
PS: I just posted that smile because i was positive about this, now i think there is no fix for that hahaha

---

### Post by varunendra on 2012-01-31
Only a few more things I can think of:

[LIST=1]
[*]Disable IPv6 using any of the two guides I linked in my earlier post, and
[*]Upgrade to latest kernel (3.0.0.15)
[*]A shot in the dark (which I haven't seen to work in ages!) would be setting MTU value in network  manager to 1492.
[*]As a last attempt (with the least chance of any satisfactory results), try windows (xp) driver with ndiswrapper. (see [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and [here]("https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html"))
[/LIST]
If you try ndiswrapper, read the guide carefully. You'll have to unload the native ath9k_htc driver (modprobe -rfv ath9k_htc) and load the ndiswrapper driver manually (modprobe -v ndiswrapper). Although I'm least hopeful with that approach, I'd definitely try to help as much as I can if you decide to go for it.

With these I think I've reached the limit of my wits.

---

### Post by youngforyou on 2012-03-16
[QUOTE=varunendra;11653081]Only a few more things I can think of:

[LIST=1]
[*]Disable IPv6 using any of the two guides I linked in my earlier post, and
[*]Upgrade to latest kernel (3.0.0.15)
[/LIST]
 Hi, varunendra,

Hope you can see my post, which is my first post here:p
I have another problem about wireless access in Ubuntu 11.04.

After I installed the driver of the wireless card, everything went fine. The speed of downloading from internet can even reach 2 Mb/s. 

But I don't know why it gets very slow after one day, like 20 Kb/s:mad:. The most wired thing is that, if I use a external usb hub which is also connected to the same usb bus, again I get a high speed wireless access!

So, the problem seems to be, I cannot directly connect the wireless card to my usb port, but if I can use a external hub, everything goes fine. 

Do you have any idea about this?:lolflag:

---

### Post by varunendra on 2012-03-17
> **youngforyou said:**
> Do you have any idea about this?
Please check your original thread, I've posted there: [http://ubuntuforums.org/showthread.php?p=11772204](http://ubuntuforums.org/showthread.php?p=11772204)

---

