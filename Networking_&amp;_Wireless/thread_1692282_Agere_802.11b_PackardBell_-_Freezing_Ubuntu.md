---
title: "Agere 802.11b PackardBell - Freezing Ubuntu"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by FranckBM on 2011-02-21
Hello, i'm new on Linux and i have a problem with my wireless connection...



Ubuntu is always freezing when i try to connect my wificard to my box.



Here is, différent tests...can you help me ?

```
franck@franck-EASYNOTE-PB11400002:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
``````
franck@franck-EASYNOTE-PB11400002:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``````
franck@franck-EASYNOTE-PB11400002:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 18)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Device 434c
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:04.0 Network controller: Agere Systems Device ab34
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

``````
franck@franck-EASYNOTE-PB11400002:~$ lspci -nn | grep -i net
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller [1002:4342]
02:04.0 Network controller [0280]: Agere Systems Device [11c1:ab34]
02:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

``````
franck@franck-EASYNOTE-PB11400002:~$ sudo lshw -C network
[sudo] password for franck: 
  *-network:0             
       description: Wireless interface
       product: Agere Systems
       vendor: Agere Systems
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 00
       serial: 00:90:96:cd:f8:98
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wlaskall driverversion=1.56+Agere Systems,01/06/2004, 8 latency=0 link=no multicast=yes wireless=IEEE 802.11b
       resources: irq:10 ioport:a400(size=64)
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth0
       version: 10
       serial: 00:0d:5e:b4:b2:49
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.16 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:10 ioport:a000(size=256) memory:d8200000-d82000ff

``````
franck@franck-EASYNOTE-PB11400002:~$ lsmod
Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
radeon                829447  3 
snd_atiixp             12426  2 
snd_atiixp_modem        9147  5 
snd_ac97_codec         99227  2 snd_atiixp_modem,snd_atiixp
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  5 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
ttm                    56633  1 radeon
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30200  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
joydev                  8767  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168092  5 radeon,ttm,drm_kms_helper
ndiswrapper           184207  0 
ati_agp                 5202  1 
snd                    49038  20 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5168  1 radeon
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
shpchp                 29886  0 
i2c_piix4               8635  0 
snd_page_alloc          7120  3 snd_atiixp_modem,snd_atiixp,snd_pcm
agpgart                32011  3 ttm,drm,ati_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
btrfs                 489451  0 
8139too                19581  0 
8139cp                 16934  0 
zlib_deflate           19266  1 btrfs
pata_atiixp             3288  2 
mii                     4425  2 8139too,8139cp
crc32c                  2531  1 
libcrc32c                887  1 btrfs
``````
franck@franck-EASYNOTE-PB11400002:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````
franck@franck-EASYNOTE-PB11400002:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:5e:b4:b2:49  
          inet adr:192.168.1.16  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::20d:5eff:feb4:b249/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:36 erreurs:0 :0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:4811 (4.8 KB) Octets transmis:17717 (17.7 KB)
          Interruption:10 Adresse de base:0xa000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:12 erreurs:0 :0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:720 (720.0 B) Octets transmis:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:cd:f8:98  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:10

``````
franck@franck-EASYNOTE-PB11400002:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:6A:9F:45:E5
                    ESSID:"Livebox-7E9F"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:00:00:00:00:00
                    ESSID:""
                    Protocol:IEEE 802.11b
                    Mode:Auto
                    Channel:0
                    Quality:100/100  Signal level:-10 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Extra:bcn_int=0
                    Extra:atim=0
          Cell 03 - Address: 00:00:00:00:00:00
                    ESSID:""
                    Protocol:IEEE 802.11b
                    Mode:Auto
                    Channel:0
                    Quality:100/100  Signal level:-10 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Extra:bcn_int=0
                    Extra:atim=0

``````
franck@franck-EASYNOTE-PB11400002:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

``````
franck@franck-EASYNOTE-PB11400002:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:0D:5E:B4:B2:49

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.16
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             disconnected
  Default:           no
  HW Address:        00:90:96:CD:F8:98

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
    Livebox-7E9F:    Infra, 00:1D:6A:9F:45:E5, Freq 2437 MHz, Rate 18 Mb/s, Strength 9 WPA

``````
franck@franck-EASYNOTE-PB11400002:~$ uname -r -m
2.6.35-25-generic i686
```What can i do ??

---

### Post by Hippytaff on 2011-02-21
Hi and welcome to the forums.
 
So you have used a windows driver with Ndiswrapper?
 
you might need to blacklist a conflicting driver, and it's walesy worth giving
```
rfkill unblock all
``` and ```
ifconfig wlan0 up
```

---

### Post by FranckBM on 2011-02-21
Hello, thank you for your welcome and your answer

Yes I have used a windows driver with Ndiswrapper

 
When I use this code, i have this answer (it's french, I'm french in France. it means :  "it's not allowed"):      
   [CODE]   ifconfig wlan0 up
SIOCSIFFLAGS: Permission non accordée[\CODE]

---

### Post by FranckBM on 2011-02-21
Hello, thank you for your welcome and your answer

Yes I have used a windows driver with Ndiswrapper

 
When I use this code, i have this answer (it's french, I'm french in France. it means :  "it's not allowed"):      
 ```
    ifconfig wlan0 up
SIOCSIFFLAGS: Permission non accordée
```

---

### Post by Hippytaff on 2011-02-21
try doing sudo
```
sudo ifconfig wlan0 up
```
you'll have to enter your password (which won't be visible in the terminal) :-)

---

### Post by FranckBM on 2011-02-22
Ok, with sudo it's ok but it doesn't work : Ubuntu is always freezing when it try to connect by wifi...:(
Thanks for your help.

---

### Post by Hippytaff on 2011-02-22
Have you checked for additional drivers?
 
Go to Administration -> Additional Drivers

---

### Post by FranckBM on 2011-02-22
No I haven't checked for additionnal drivers !! But i do it when i'm back home.
Thanks a lot.

---

### Post by Hippytaff on 2011-02-22
If I understand correctly you attach your wifi card after booting?
 
Boot with it attached and then if it doesn't work look for additional drivers

---

### Post by FranckBM on 2011-02-22
Yest I try to attach my wifi card after booting...

How can i do to" boot with my wifi card attached" ? Because when the attachement begin, it freezes all !?

I try to find additionnal drivers with Administration -> Additional Drivers, but it doesn't exist, ubuntu doesn't find anything...

I wonder if we'll find the soluce :(

---

### Post by Hippytaff on 2011-02-22
Did you use ndisgtk an Ndiswrapper GUI to install the xp drivers? if not I recommend doing so. To install do ```
sudo apt-get install ndisgtk
```
then try reinstalling the .inf and .sys files.

---

### Post by FranckBM on 2011-02-23
Yes, the drivers have been installed  with ndisgtk...
but only the file .inf not the .sys ?

---

### Post by Hippytaff on 2011-02-23
You probably need to find and install the .sys file as well

---

### Post by FranckBM on 2011-02-23
Ok, i'll try to find it and I'll tell you
Thanks

---

### Post by FranckBM on 2011-02-23
I found tow files .sys...but i don't know what to do with  !! ndisgtk use only .inf files...

How can i install .sys files ?

Thanks (one more time ! :))

---

### Post by Hippytaff on 2011-02-23
I would do this - copy and paste the .inf and .sys files to the desktop. Start Ndisgtk and select (and intall etc) to the .inf file. I believe it will automatically use the sys file if it's in the same directory.

---

### Post by FranckBM on 2011-02-23
That's the way I used to install the driver (the two files .sys were in the same folder than the .inf file when I launched ndisgtk )...

---

### Post by Hippytaff on 2011-02-24
There are not many more avenues left as far as my (limited) knowledge goes. There is the option to pach the kernel with relevant modules (way out of my league), maybe a driver conflict needs to be resolved? (ralink?) or maybe for some reason the module is not loading. The latter might be down to the fact that the device is not plugged in before booting. During boot udev probes to find what devices are attached and which modules it has to load.
 
I have read that this type of 'soft' modem can be troublesome.
 
Other than the above possibilities (unless I've overlooked something) I am at a loss...sorry!

---

### Post by FranckBM on 2011-02-24
Ok... You don't have to feel sorry. Thank you for your help !
I hope that, one day, we'll find the soluce !

---

### Post by Hippytaff on 2011-02-24
Try booting with the device plugged in ie plug it in then boot

---

### Post by FranckBM on 2011-02-25
I modified few files in etc directory : interfaces and wpa_application.conf

when i tested a ping to google i have had this answer :
```
franck@franck-EASYNOTE-PB11400002:~$ ping -c2 www.google.fr
PING www.l.google.com (74.125.230.82) 56(84) bytes of data.
64 bytes from 74.125.230.82: icmp_req=1 ttl=55 time=47.9 ms
64 bytes from 74.125.230.82: icmp_req=2 ttl=54 time=47.1 ms

--- www.l.google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 5208ms
rtt min/avg/max/mdev = 47.141/47.534/47.928/0.449 ms
```

Does it mean that my wifi card works good ?

In that case, the problem is only about ubuntu and networkmanager ?

(sorry for my english, you can correct me (i'm learning) about the verbs in the second sentence.)

---

