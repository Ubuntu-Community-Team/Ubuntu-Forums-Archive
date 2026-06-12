---
title: "PLEASE help with mceusb IR blaster"
date: 2009-12-20
forum: Mythbuntu
---

### Post by jmlott on 2009-12-20
I am now batting 0 for 3 on getting remotes to work with my new system.

The Asrock ION 330ht comes with an MCE remote and built-in reciever... that has no Linux drivers
I got an HD-PVR that came with a remote and IR blaster... there are no working drivers for it
Slightly frustrated, I bought a GP-IR02BK USB MCE remote/blaster combo thinking it would surely work since I read that mceusb devices were well supported... remote works, blaster doesnt

... ](*,)

Seriously, WTF? I just want something that will control my Motorola Comcast STB so I can actually use my brand new system to record freakin TV shows. Is that so much to ask?

Can someone please tell me what to buy? What will work out of the box 100% of the time with Mythbuntu 9.10? Note: I dont have a firewire port and no way to add one, so that option is out.

I apologize for the extreme frustration vented in this post, but I have been trying to get this working for 2 weeks straight. I am literally losing sleep over it.

---

### Post by nasha on 2009-12-21
Hauppauge MCE Remote Kit has worked fine for me everytime.

There will be no out of the box solution, as you will need to configure the blaster to use the correct remote config file for your STB.

I would say that if you've had issues with numerous remotes however, especially MCE based ones, that your not doing something correctly in setting lirc up?

Nasha

---

### Post by jmlott on 2009-12-21
Hi Nasha,

Thanks for the reply. I will look into the Hauppauge MCE remote kit. When I said "works out of the box", of course I know there will have to be some setup with LIRC. I just mean I dont want to have to jump through any hoops or compile any special kernel modules that may or may not work with every system. I want something that has a lircd.conf readily available that all I have to do is cp it over, load the module, and start lirc. 

As far as setting up lirc for my current hardware, yes, it is completely possible that I have done something wrong. If anyone would like to help me verify my setup, I would be extremely grateful.... unfortunately, my past cries for help have gone unheard, so I have no expectations there.

As I said, the first 2 attempts are useless ATM. There is no lirc support for the MCE remote that comes with the ION 330HT and the hacky lirc modules that some people claim to work with the hdpvr are impossible to compile on an Ubuntu 9.10 system.

Here is my current setup with the GP-IR02BK MCE Remote/Blaster:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS="--release"

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Motorola Cable box"
#TRANSMITTER="DCT2000"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="motorola/dch3200.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Microsoft Windows Media Center V2 (usb) : Motorola Cable box transmitter:
#include "/usr/share/lirc/extras/transmitters/motorola/dctxxxx.conf"
include "/usr/share/lirc/extras/transmitters/motorola/dch3200.conf"

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"
#include "/usr/share/lirc/remotes/mceusb/lircd.conf.gpir02bk"
```

```
mythbox@mythbox:~$ cat /usr/share/lirc/extras/transmitters/motorola/dch3200.conf
begin remote
  name            DCH3200
  bits            22
  flags           SPACE_ENC|CONST_LENGTH
  eps             30
  aeps            100
  header          3512  3156
  one             989  2362
  zero            989   680
  ptrail          975
  gap             100094

  begin codes
       power           0x37C107
       rew             0x37291A
       play            0x37990C
       ffwd            0x36293A
       stop            0x365934
       pause           0x374117
       record          0x375914
       circlearrow     0x37C906
       mydvr           0x36C926
       live            0x36B129
       b               0x36193C
       c               0x37191C
       pageup          0x36D924
       pagedown        0x37D904
       up              0x36812F
       left            0x37810F
       ok              0x366133
       right           0x364137
       down            0x37A10B
       guide           0x36C127
       info            0x36213B
       menu            0x373918
       exit            0x366932
       help            0x376912
       last            0x36E123
       vol+            0x36093E
       vol-            0x37091E
       mute            0x36892E
       fav             0x37F101
       ch+             0x377111
       ch-             0x36F121
       0               0x373119
       1               0x36113D
       2               0x37111D
       3               0x36912D
       4               0x37910D
       5               0x365135
       6               0x375115
       7               0x36D125
       8               0x37D105
       9               0x363139
       tv-vcr          0x376113
       zoom            0x36B928
       pip-on-off      0x37B908
       pipswap         0x367930
       pipmove         0x377910
       pip+            0x36E922
       pip-            0x37F900

  end codes

end remote
```

```
mythbox@mythbox:~$ lsusb
Bus 001 Device 003: ID 2040:4902 Hauppauge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 04f3:01a4 Elan Microelectronics Corp.
Bus 002 Device 002: ID 1784:0008 TopSeed Technology Corp.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
mythbox@mythbox:~$ lsmod|grep lirc
lirc_mceusb            15552  1
lirc_dev               10804  3 lirc_mceusb
```

```
mythbox@mythbox:~$ ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2009-12-20 22:47 /dev/lirc0
lrwxrwxrwx 1 root root    19 2009-12-20 23:16 /dev/lircd -> /var/run/lirc/lircd
lrwxrwxrwx 1 root root    20 2009-12-20 23:16 /dev/lircd1 -> /var/run/lirc/lircd1
```

```
mythbox@mythbox:~$ dmesg|grep lirc
[    7.762039] lirc_dev: IR Remote Control driver registered, major 61
[    7.805788] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[    7.805796] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[    7.805802] lirc_mceusb: debug mode enabled
[    7.805837] lirc_mceusb: mceusb_dev_probe called
[    8.174812] lirc_mceusb: acceptable outbound endpoint found
[    8.174821] lirc_mceusb: acceptable inbound endpoint found
[    8.174831] lirc_dev: lirc_register_driver: sample_rate: 0
[    8.180810] lirc_mceusb[2]: Topseed Technology Corp. eHome Infrared Transceiver on usb2:2
[    8.180819] lirc_mceusb[2]: receive request called (size=0x20)
[    8.180828] lirc_mceusb[2]: receive request complete (res=0)
[    8.180833] lirc_mceusb[2]: receive request called (size=0x20)
[    8.180839] lirc_mceusb[2]: receive request complete (res=0)
[    8.180844] lirc_mceusb[2]: receive request called (size=0x5)
[    8.180851] lirc_mceusb[2]: receive request complete (res=0)
[    8.180856] lirc_mceusb[2]: receive request called (size=0x20)
[    8.180862] lirc_mceusb[2]: receive request complete (res=0)
[    8.180867] lirc_mceusb[2]: receive request called (size=0x2)
[    8.180872] lirc_mceusb[2]: receive request complete (res=0)
[    8.180877] lirc_mceusb[2]: receive request called (size=0x20)
[    8.180882] lirc_mceusb[2]: receive request complete (res=0)
[    8.180945] usbcore: registered new interface driver lirc_mceusb
[    8.182796] lirc_mceusb[2]: callback called (status=0 len=5)
[    8.182804] lirc_mceusb[2]: data received 00 ff aa ff 0b  (length=5)
[    8.183795] lirc_mceusb[2]: callback called (status=0 len=2)
[    8.183802] lirc_mceusb[2]: data received ff fe  (length=2)
[    8.183807] lirc_mceusb[2]: callback called (status=0 len=2)
[    8.183813] lirc_mceusb[2]: data received ff 18  (length=2)
[   33.227634] lirc_mceusb[2]: mceusb IR device opened
[   49.946252] lirc_mceusb[2]: callback called (status=0 len=2)
[   49.946261] lirc_mceusb[2]: data received 81 b8  (length=2)
[   49.947239] lirc_mceusb[2]: callback called (status=0 len=2)
[   49.947245] lirc_mceusb[2]: data received 81 0f  (length=2)
[   49.948241] lirc_mceusb[2]: data received 82 8b 07  (length=3)
[   49.948246] lirc_mceusb[2]: setup answer received 3 bytes
[   49.950241] lirc_mceusb[2]: data received 82 8b 07  (length=3)
[   49.952241] lirc_mceusb[2]: data received 83 8a 10 8b  (length=4)
[   49.953239] lirc_mceusb[2]: data received 82 10 9c  (length=3)
[   49.955236] lirc_mceusb[2]: data received 81 11  (length=2)
[   49.957241] lirc_mceusb[2]: data received 84 8a 07 8a 08  (length=5)
[   49.959234] lirc_mceusb[2]: data received 85 8a 08 8a 08 89  (length=6)
[   49.960237] lirc_mceusb[2]: data received 85 08 8a 08 8a 08  (length=6)
[   49.961242] lirc_mceusb[2]: data received 82 8a 08  (length=3)
[   49.963236] lirc_mceusb[2]: data received 82 89 08  (length=3)
[   49.965236] lirc_mceusb[2]: data received 84 8a 08 93 08  (length=5)
[   49.967232] lirc_mceusb[2]: data received 84 89 08 8a 08  (length=5)
[   49.968231] lirc_mceusb[2]: data received 84 8a 11 89 08  (length=5)
[   49.969238] lirc_mceusb[2]: data received 82 8a 08  (length=3)
[   49.971230] lirc_mceusb[2]: data received 82 8a 08  (length=3)
[   49.973232] lirc_mceusb[2]: data received 83 8a 08 92  (length=4)
[   49.975230] lirc_mceusb[2]: data received 84 11 8a 08 8a  (length=5)
[   49.976227] lirc_mceusb[2]: data received 85 08 89 08 8a 08  (length=6)
[   49.977235] lirc_mceusb[2]: data received 81 93  (length=2)
[   49.979227] lirc_mceusb[2]: data received 82 08 8a  (length=3)
[   49.981229] lirc_mceusb[2]: data received 85 08 89 08 8a 08  (length=6)
[   49.983224] lirc_mceusb[2]: data received 81 8a  (length=2)
[   49.986224] lirc_mceusb[2]: data received 81 7f  (length=2)
[   49.993225] lirc_mceusb[2]: data received 81 7f  (length=2)
[   49.999218] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.006219] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.012210] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.018211] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.025204] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.031204] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.037198] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.044200] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.050192] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.052186] lirc_mceusb[2]: data received 81 02  (length=2)
[   50.054189] lirc_mceusb[2]: data received 81 b6  (length=2)
[   50.056184] lirc_mceusb[2]: data received 83 11 89 08  (length=4)
[   50.057188] lirc_mceusb[2]: data received 84 8a 08 8a 11  (length=5)
[   50.059187] lirc_mceusb[2]: data received 81 89  (length=2)
[   50.061187] lirc_mceusb[2]: data received 82 11 9c  (length=3)
[   50.063183] lirc_mceusb[2]: data received 84 11 89 09 89  (length=5)
[   50.064182] lirc_mceusb[2]: data received 84 08 8a 08 8a  (length=5)
[   50.065191] lirc_mceusb[2]: data received 83 08 89 09  (length=4)
[   50.067181] lirc_mceusb[2]: data received 82 89 08  (length=3)
[   50.069183] lirc_mceusb[2]: data received 84 8a 08 8a 08  (length=5)
[   50.071178] lirc_mceusb[2]: data received 84 89 09 89 08  (length=5)
[   50.072180] lirc_mceusb[2]: data received 84 93 08 89 09  (length=5)
[   50.073184] lirc_mceusb[2]: data received 82 89 08  (length=3)
[   50.075178] lirc_mceusb[2]: data received 82 8a 11  (length=3)
[   50.077179] lirc_mceusb[2]: data received 84 89 09 89 09  (length=5)
[   50.079175] lirc_mceusb[2]: data received 84 89 08 8a 08  (length=5)
[   50.080174] lirc_mceusb[2]: data received 83 92 12 89  (length=4)
[   50.081179] lirc_mceusb[2]: data received 83 08 8a 08  (length=4)
[   50.083173] lirc_mceusb[2]: data received 82 89 09  (length=3)
[   50.085177] lirc_mceusb[2]: data received 83 89 09 92  (length=4)
[   50.087174] lirc_mceusb[2]: data received 85 08 89 09 89 09  (length=6)
[   50.088169] lirc_mceusb[2]: data received 83 89 08 8a  (length=4)
[   50.093172] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.100172] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.106170] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.112161] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.119161] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.125152] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.131154] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.138146] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.144150] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.150141] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.157144] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.163135] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.169132] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.176130] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.182124] lirc_mceusb[2]: data received 81 7f  (length=2)
[   50.187125] lirc_mceusb[2]: data received 81 5f 80  (length=3)
[   52.175128] lirc_mceusb[2]: data received 81 b7  (length=2)
[   52.176110] lirc_mceusb[2]: data received 81 10  (length=2)
[   52.178115] lirc_mceusb[2]: data received 82 8b 07  (length=3)
[   52.180110] lirc_mceusb[2]: data received 83 8a 08 8a  (length=4)
[   52.182111] lirc_mceusb[2]: data received 83 10 8a 11  (length=4)
[   52.183108] lirc_mceusb[2]: data received 82 9c 10  (length=3)
[   52.184108] lirc_mceusb[2]: data received 83 8a 08 8a  (length=4)
[   52.186109] lirc_mceusb[2]: data received 82 08 8a  (length=3)
[   52.188106] lirc_mceusb[2]: data received 84 07 8a 08 8a  (length=5)
[   52.190109] lirc_mceusb[2]: data received 85 08 8a 08 8a 07  (length=6)
[   52.191104] lirc_mceusb[2]: data received 84 8a 08 8a 08  (length=5)
[   52.192103] lirc_mceusb[2]: data received 82 8a 08  (length=3)
[   52.194106] lirc_mceusb[2]: data received 82 92 08  (length=3)
[   52.196101] lirc_mceusb[2]: data received 84 8a 08 8a 08  (length=5)
[   52.198104] lirc_mceusb[2]: data received 84 8a 08 89 11  (length=5)
[   52.199102] lirc_mceusb[2]: data received 84 8a 08 8a 08  (length=5)
[   52.200098] lirc_mceusb[2]: data received 82 89 08  (length=3)
[   52.202101] lirc_mceusb[2]: data received 81 93  (length=2)
[   52.204099] lirc_mceusb[2]: data received 85 11 8a 08 89 08  (length=6)
[   52.206099] lirc_mceusb[2]: data received 84 8a 08 8a 08  (length=5)
[   52.207097] lirc_mceusb[2]: data received 84 93 08 89 08  (length=5)
[   52.208095] lirc_mceusb[2]: data received 82 8a 08  (length=3)
[   52.210096] lirc_mceusb[2]: data received 81 8a  (length=2)
[   52.212093] lirc_mceusb[2]: data received 82 11 89  (length=3)
[   52.216094] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.222091] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.228089] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.235085] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.241082] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.247079] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.254075] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.260072] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.267067] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.273064] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.279061] lirc_mceusb[2]: data received 81 78  (length=2)
[   52.282061] lirc_mceusb[2]: data received 81 b7  (length=2)
[   52.284063] lirc_mceusb[2]: data received 81 10  (length=2)
[   52.286063] lirc_mceusb[2]: data received 84 8a 08 8a 08  (length=5)
[   52.287057] lirc_mceusb[2]: data received 83 8a 11 89  (length=4)
[   52.288054] lirc_mceusb[2]: data received 81 11  (length=2)
[   52.290058] lirc_mceusb[2]: data received 81 9c  (length=2)
[   52.292055] lirc_mceusb[2]: data received 84 11 89 08 8a  (length=5)
[   52.294056] lirc_mceusb[2]: data received 84 08 8a 08 89  (length=5)
[   52.295053] lirc_mceusb[2]: data received 85 09 89 08 8a 08  (length=6)
[   52.296051] lirc_mceusb[2]: data received 82 8a 08  (length=3)
[   52.298053] lirc_mceusb[2]: data received 83 89 09 89  (length=4)
[   52.300049] lirc_mceusb[2]: data received 83 08 8a 08  (length=4)
[   52.302053] lirc_mceusb[2]: data received 84 92 09 89 08  (length=5)
[   52.303048] lirc_mceusb[2]: data received 85 8a 08 8a 08 89  (length=6)
[   52.304046] lirc_mceusb[2]: data received 81 12  (length=2)
[   52.306050] lirc_mceusb[2]: data received 83 89 08 8a  (length=4)
[   52.308045] lirc_mceusb[2]: data received 83 08 89 09  (length=4)
[   52.310047] lirc_mceusb[2]: data received 84 92 11 89 09  (length=5)
[   52.311045] lirc_mceusb[2]: data received 84 89 09 89 08  (length=5)
[   52.312041] lirc_mceusb[2]: data received 82 8a 08  (length=3)
[   52.314045] lirc_mceusb[2]: data received 82 92 09  (length=3)
[   52.316042] lirc_mceusb[2]: data received 84 89 09 89 08  (length=5)
[   52.318042] lirc_mceusb[2]: data received 83 8a 11 89  (length=4)
[   52.323039] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.329036] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.335032] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.342030] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.348026] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.354024] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.361021] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.367019] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.373015] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.380015] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.386007] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.392004] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.399001] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.404999] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.411996] lirc_mceusb[2]: data received 81 7f  (length=2)
[   52.415994] lirc_mceusb[2]: data received 81 5f 80  (length=3)
[ 1041.171422] lirc_mceusb[2]: mceusb IR device closed
[ 1041.281789] lirc_mceusb[2]: mceusb IR device opened
[ 1103.702010] lirc_mceusb: SET_TRANSMITTERS mask=1
[ 1764.118287] lirc_mceusb[2]: mceusb IR device closed
[ 1764.237307] lirc_mceusb[2]: mceusb IR device opened
[ 2091.937974] lirc_mceusb[2]: SET_CARRIER requesting 38000 Hz
[ 2091.937984] lirc_mceusb[2]: receive request called (size=0x4)
[ 2091.937998] lirc_mceusb[2]: receive request complete (res=0)
[ 2091.938026] lirc_mceusb[2]: receive request called (size=0x3f)
[ 2091.938033] lirc_mceusb[2]: receive request complete (res=0)
[ 2091.939410] lirc_mceusb[2]: callback called (status=0 len=4)
[ 2091.939418] lirc_mceusb[2]: data received 9f 06 01 41  (length=4)
[ 2091.945408] lirc_mceusb[2]: callback called (status=0 len=63)
[ 2091.945427] lirc_mceusb[2]: data received 9f 08 01 84 c6 3f 93 2f 84 93 2f 93 0d 84 93 2f 93 2f 84 93 2f 93 2f 84 93 2f 93 0d 84 93 0d 93  (length=63)
```


For this one, the remote/receiver works just fine. I get output from irw and it is all set up with a good .lircrc to work in myth, etc. My problem is with the IR Blaster. If I use /dev/lircd, I get no error message, but the IR emitter doesn't blink as it should. That makes sense, because it is setup as the receiver. Note that only /dev/lirc0 is created when the mceusb module is loaded. There should also be a /dev/lirc1... I'm pretty sure that is where my problem lies.

```
irsend -d /dev/lircd1 SEND_ONCE DCH3200 power
irsend: command failed: SEND_ONCE DCH3200 power
irsend: hardware does not support sending
```

---

### Post by oliver.greg@gmail.com on 2010-01-16
Did you find a solution to this?  I have been battling this all day, and after fixing the lirc init script, I cannot get it to blast at all. 

I mknod'ed my own lirc1 to match lirc0 with no success as well.

I did notice that the control-centre created hardware.conf called for lirc_mceusb2 module, but it is not available to be loaded.  That is another big one for me..  It seems a lot of people refer to version 2 of it, but I cannot find the module to load it.  Maybe it has been all folded into the single lirc_mceusb module now??

Thanks for any tips if you have gotten it to work..

could not open /dev/lirc1
Jan 16 14:52:07 htpc lircd-0.8.6[3098]: default_init(): Device or resource busy
Jan 16 14:52:07 htpc lircd-0.8.6[3098]: Failed to initialize hardware
Jan 16 14:52:07 htpc lircd-0.8.6[3098]: error processing command: SEND_ONCE directv info
Jan 16 14:52:07 htpc lircd-0.8.6[3098]: hardware does not support sending
Jan 16 14:52:07 htpc lircd-0.8.6[3098]: removed client

-Greg

---

### Post by LarryJ2 on 2010-01-27
Sorry  ... can't determine how to delete my post.  Turns out my idea was wrong.

---

### Post by scottcrawford on 2010-02-12
I'm in a similar situation. Got a Mediagate IR02BK remote/blaster. The remote works fine using the standard LIRC mceusb config file. I used the Mythbuntu lircrc generator and got Myth responding to the remote. That part was easy. My problem is with the blasting. When I try irsend, the transceiver blinks and my IR LED blinks so I know it's trying to blast but my satellite receiver doesn't respond. I've tried downloading a config file for my satellite remote and I've tried irrecord to create my own. I know the codes are good, because when I run irw and use my satellite remote it shows the correct keypresses. I've also tried opening 2 terminals - in one I ran irw, and in the other I ran irsend while holding my blaster LED up to the transceiver. irw didn't recognize any of the codes I sent from irsend.

In my hardware.conf I'm using lirc_dev and lirc_mceusb (defined only in the transmitter section). I'm not on my Myth box right now so including my hardware.conf is a bit difficult.

I've seen that lirc_mceusb2 has been merged into lirc_mceusb and I've seen that only 1 lirc device needs to be created for the receiver/transmitter combo.

I'm running Ubuntu 9.10 64-bit. The transceiver is identified as a Formosa unit.

Any help is much appreciated!

---

