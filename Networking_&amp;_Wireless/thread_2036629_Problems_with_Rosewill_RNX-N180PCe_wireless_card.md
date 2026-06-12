---
title: "Problems with Rosewill RNX-N180PCe wireless card"
date: 2012-08-02
forum: Networking &amp; Wireless
---

### Post by Subcomfreak on 2012-08-02
I'm currently running ubuntu 12.04 and am having an interesting issue with my wireless card. 

I know for a fact that my card is a **Rosewill RNX-N180PCe. **It finds and connects to my wireless network fine. I can browse the web fine (in fact I am posting from linux right now!) and download files. However, after a while it stops receiving information as if it were disconnected from the network.  It says that it is still connected (83% signal strength.), however via system monitor and the downloading program itself (firefox, update manager, ubuntu software center, even the terminal) I can tell that it IS NOT downloading.

This is my cards official website: [http://www.rosewill.com/products/1698/ProductDetail_Download.htm](http://www.rosewill.com/products/1698/ProductDetail_Download.htm)

Also, the security on my network is "WPA2" personal. I heard that the split mode (which I used previously) could cause problems. However, after I changed my security to only WPA2, everything seemed okay, however, the problem still persists. 

I DO know that it is not a hardware issue because when I boot to windows on the same computer (windows 2000) everything works perfectly.

I'm still very new to linux and I'm procrastinating on learning how to use the terminal effectively, so I will need step-by-step instructions. However, support for ubuntu has never failed me yet, and I know there is a solution! 

Thank you in advance!!!


additional information:
lspci gives:
02:0b.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R

ifconfig gives:
```
eth0      Link encap:Ethernet  HWaddr 00:b0:d0:22:60:79  
          inet6 addr: fe80::2b0:d0ff:fe22:6079/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4210 (4.2 KB)  TX bytes:5011 (5.0 KB)
          Interrupt:16 Base address:0xc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:144485 (144.4 KB)  TX bytes:144485 (144.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:02:6f:a3:19:67  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:6fff:fea3:1967/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:143670505 (143.6 MB)  TX bytes:7020045 (7.0 MB)

```

iwconfig gives:
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"RosoRouter"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:6D:8F:9B:A2:B3   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1504  Invalid misc:106   Missed beacon:0

eth0      no wireless extensions.


```

lsmod gives:

```
Module                  Size  Used by
deflate                12545  0 
zlib_deflate           26622  1 deflate
ctr                    13033  0 
twofish_generic        16579  0 
twofish_i586           12755  0 
twofish_common         20823  2 twofish_generic,twofish_i586
camellia               29212  0 
serpent                29029  0 
blowfish_generic       12474  0 
blowfish_common        16635  1 blowfish_generic
cast5                  24976  0 
des_generic            21191  0 
xcbc                   12711  0 
rmd160                 16664  0 
sha512_generic         16780  0 
crypto_null            12782  0 
af_key                 31531  2 
rfcomm                 37291  0 
bnep                   17711  2 
bluetooth             164346  10 rfcomm,bnep
binfmt_misc            17292  1 
ppdev                  12849  0 
dcdbas                 14098  0 
snd_cs46xx             83775  3 
gameport               15060  2 snd_cs46xx
snd_ac97_codec        106082  1 snd_cs46xx
ac97_bus               12642  1 snd_ac97_codec
arc4                   12473  2 
snd_pcm                80845  3 snd_cs46xx,snd_ac97_codec
rt2800pci              18108  0 
snd_seq_midi           13132  0 
psmouse                72919  0 
rt2800lib              52596  1 rt2800pci
snd_rawmidi            25424  2 snd_cs46xx,snd_seq_midi
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14116  1 rt2800pci
rt2x00lib              48261  3 rt2800pci,rt2800lib,rt2x00pci
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                737789  2 
mac80211              440734  3 rt2800lib,rt2x00pci,rt2x00lib
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd                    62064  12 snd_cs46xx,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   197692  4 radeon,ttm,drm_kms_helper
parport_pc             32114  1 
cfg80211              178818  2 rt2x00lib,mac80211
i2c_algo_bit           13199  1 radeon
eeprom_93cx6           13134  1 rt2800pci
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_cs46xx,snd_pcm
mac_hid                13077  0 
intel_rng              12700  0 
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
aic7xxx               126038  0 
3c59x                  37445  0 
floppy                 60310  0 

```

sudo lshw -C network gives:
```
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth0
       version: 78
       serial: 00:b0:d0:22:60:79
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:cc80(size=128) memory:f8fffc00-f8fffc7f memory:f9000000-f901ffff
  *-network:1
       description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R
       vendor: Ralink corp.
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: wlan0
       version: 00
       serial: 00:02:6f:a3:19:67
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-27-generic-pae firmware=0.34 ip=192.168.1.135 latency=64 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f8fe0000-f8feffff

```

iwlist scan gives:
```
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 58:6D:8F:9B:A2:B3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"RosoRouter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 36612ms ago
                    IE: Unknown: 000A526F736F526F75746572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B00010310470010D8E17EC120B3C9FBB0584A516170A335102100074C696E6B7379731023000D4C696E6B7379732045343230301024000776312E302E30341042000234321054000800060050F20400011011000D4C696E6B737973204534323030100800020084103C000103
                    IE: Unknown: DD090010180203F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.


```

---

### Post by praseodym on 2012-08-02
Hi,

please show:
> 
cat /etc/resolv.conf
route -n
dmesg | grep rt2

---

### Post by Subcomfreak on 2012-08-02
cat /etc/resolv.conf
```
 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```

dmesg | grep rt2 			 		
```
[   45.871232] [COLOR=Red]rt2[/COLOR]800pci 0000:02:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   45.922686] Registered led device:[COLOR=Red] rt2[/COLOR]800pci-phy0::radio
[   45.922769] Registered led device: [COLOR=Red]rt2[/COLOR]800pci-phy0::assoc
[   45.922840] Registered led device: [COLOR=Red]rt2[/COLOR]800pci-phy0::quality
[   48.556600] phy0 -> [COLOR=Red]rt2[/COLOR]800pci_mcu_status: Error - MCU request failed, no response from hardware

```

---

### Post by jawilljr on 2012-08-02
Subcomfreak, take a look at [this thread](http://ubuntuforums.org/showthread.php?t=1973881&highlight=mcu)...especially [this fix from Chili](http://ubuntuforums.org/showpost.php?p=11908967&postcount=6)

It seems you both have the same error as below:

```
phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
```

The fix was to install "linux-backports-modules-cw-3.3-precise-generic" to update the drivers...

Jerry

---

### Post by Subcomfreak on 2012-08-02
Installing now. Results to come!

I'm currently downloading a public domain movie that is 700MB at 330-350 kbs (a pretty good speed for my Internet). Around 50MB done so far, so we shall see. But so far, so good.

---

### Post by Subcomfreak on 2012-08-02
Unfortunatly the problem still seems to be there.** It stopped downloading** my file at around 80Mb.

---

### Post by praseodym on 2012-08-03
Remove the package "resolvconf" and reboot.

---

### Post by Subcomfreak on 2012-08-03
Testing now!

Same problem. Stopped around 7MB.

---

### Post by praseodym on 2012-08-03
Go to the NM Wireless->IPv4-Settings and choose "Automatic DHCP (addresses only)" and add

> 8.8.8.8,8.8.4.4

in "DNS-Servers". These are the Google-Public-DNS

---

### Post by Subcomfreak on 2012-08-03
Testing now.

Stopped downloading at 60MB

---

### Post by praseodym on 2012-08-03
Maybe the router is cancelling the connection?! Check, if the firmware of it is up-to-date.

---

### Post by Subcomfreak on 2012-08-03
I know for a fact that it is.

Could it possibly still be a driver issue?

---

### Post by praseodym on 2012-08-03
Lets check:
```

cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by Subcomfreak on 2012-08-03
cat /etc/network/interfaces

```
auto lo
iface lo inet loopback

```

cat /etc/NetworkManager/NetworkManager.conf

```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

```

cat /var/lib/NetworkManager/NetworkManager.state
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

---

### Post by Subcomfreak on 2012-08-04
> **jawilljr said:**
> Subcomfreak, take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1973881&highlight=mcu")...especially [this fix from Chili]("http://ubuntuforums.org/showpost.php?p=11908967&postcount=6")

It seems you both have the same error as below:

```
phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
```The fix was to install "linux-backports-modules-cw-3.3-precise-generic" to update the drivers...

Jerry
I believe I have a "Pae" system. Not 100% but I will go check and see and install the other package for this and try.

---

### Post by Subcomfreak on 2012-08-05
Didn't work. I still need help though!

---

### Post by praseodym on 2012-08-05
Try this driver:

[http://forum.ubuntuusers.de/topic/lenovo-s205-wlan-langsam/?highlight=rt2860sta#post-4483632](http://forum.ubuntuusers.de/topic/lenovo-s205-wlan-langsam/?highlight=rt2860sta#post-4483632)

Reboot after that.

---

### Post by Subcomfreak on 2012-08-05
Trying now.

---

### Post by Subcomfreak on 2012-08-05
Now it doesn't detect my wireless network/router:?

---

### Post by praseodym on 2012-08-05
Check:

```
lsmod
dmesg | grep rt2
iwconfig
rfkill list
sudo iwlist scan
route -n
cat /etc/resolv.conf
```

---

### Post by Subcomfreak on 2012-08-06
```
john@11ukkhunbuntu:~$ lsmod
Module                  Size  Used by
deflate                12545  0 
zlib_deflate           26622  1 deflate
ctr                    13033  0 
twofish_generic        16579  0 
twofish_i586           12755  0 
twofish_common         20823  2 twofish_generic,twofish_i586
camellia               29212  0 
serpent                29029  0 
blowfish_generic       12474  0 
blowfish_common        16635  1 blowfish_generic
cast5                  24976  0 
des_generic            21191  0 
xcbc                   12711  0 
rmd160                 16664  0 
sha512_generic         16780  0 
crypto_null            12782  0 
af_key                 31531  2 
bnep                   17711  2 
rfcomm                 37291  0 
bluetooth             164346  10 bnep,rfcomm
binfmt_misc            17292  1 
ppdev                  12849  0 
dcdbas                 14098  0 
snd_cs46xx             83775  2 
gameport               15060  2 snd_cs46xx
snd_ac97_codec        106082  1 snd_cs46xx
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_cs46xx,snd_ac97_codec
snd_seq_midi           13132  0 
psmouse                72919  0 
snd_rawmidi            25424  2 snd_cs46xx,snd_seq_midi
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
radeon                737789  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  11 snd_cs46xx,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65344  1 radeon
parport_pc             32114  1 
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_cs46xx,snd_pcm
mac_hid                13077  0 
i2c_algo_bit           13199  1 radeon
intel_rng              12700  0 
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
aic7xxx               126038  0 
floppy                 60310  0 
3c59x                  37445  0 


john@11ukkhunbuntu:~$ dmesg | grep rt2
john@11ukkhunbuntu:~$ 


john@11ukkhunbuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



john@11ukkhunbuntu:~$ rfkill list
john@11ukkhunbuntu:~$ 





john@11ukkhunbuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


john@11ukkhunbuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


john@11ukkhunbuntu:~$ cat/etc/resolv.conf
bash: cat/etc/resolv.conf: No such file or directory
```

I tried to preserve exactly what the terminal showed. Sometimes it didn't return anything. Sorry for late response.

---

### Post by praseodym on 2012-08-06
Load the driver:

```
sudo modprobe -v rt2860sta
```
or
```
sudo modprobe -v rt3090sta
```

---

### Post by Subcomfreak on 2012-08-06
```
john@11ukkhunbuntu:~$ sudo modprobe -v rt2860sta
[sudo] password for john: 
FATAL: Module rt2860sta not found.
john@11ukkhunbuntu:~$ sudo modprobe -v rt3090sta
insmod /lib/modules/3.2.0-27-generic-pae/updates/dkms/rt3090sta.ko 


```
Still can't find the wireless network in linux (I can with windows). I tried rebooting and still couldn't find the network. I also tried logging in and out and still couldn't see the network.

---

### Post by praseodym on 2012-08-06
Ok, after (re-)loading the module rt3090sta, please show:

> iwconfig
lsmod
dmesg | egrep 'rt2|rt3'
sudo iwlist scan
rfkill list

---

### Post by Subcomfreak on 2012-08-07
```
john@11ukkhunbuntu:~$ sudo modprobe -v rt3090sta
[sudo] password for john: 
insmod /lib/modules/3.2.0-27-generic-pae/updates/dkms/rt3090sta.ko 
john@11ukkhunbuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

john@11ukkhunbuntu:~$ lsmodModule                  Size  Used by
rt3090sta             794418  0 
deflate                12545  0 
zlib_deflate           26622  1 deflate
ctr                    13033  0 
twofish_generic        16579  0 
twofish_i586           12755  0 
twofish_common         20823  2 twofish_generic,twofish_i586
camellia               29212  0 
serpent                29029  0 
blowfish_generic       12474  0 
blowfish_common        16635  1 blowfish_generic
cast5                  24976  0 
des_generic            21191  0 
xcbc                   12711  0 
rmd160                 16664  0 
sha512_generic         16780  0 
crypto_null            12782  0 
af_key                 31531  2 
rfcomm                 37291  0 
bnep                   17711  2 
bluetooth             164346  10 rfcomm,bnep
binfmt_misc            17292  1 
ppdev                  12849  0 
dcdbas                 14098  0 
snd_cs46xx             83775  2 
gameport               15060  2 snd_cs46xx
snd_ac97_codec        106082  1 snd_cs46xx
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_cs46xx,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_cs46xx,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                72919  0 
serio_raw              13027  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
radeon                737789  2 
intel_rng              12700  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
snd                    62064  11 snd_cs46xx,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32114  1 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_cs46xx,snd_pcm
i2c_algo_bit           13199  1 radeon
mac_hid                13077  0 
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
aic7xxx               126038  0 
floppy                 60310  0 
3c59x                  37445  0 
john@11ukkhunbuntu:~$ dmesg | egrep 'rt2|rt3'
[  163.824962] rt3090sta: module license 'unspecified' taints kernel.
john@11ukkhunbuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

john@11ukkhunbuntu:~$ rfkill list 
john@11ukkhunbuntu:~$ 
```

---

### Post by praseodym on 2012-08-07
Did you install linux-backports-modules-cw-3.3-precise-generic**-pae**? You may uninstall the rt2860sta-package first, then reboot.

---

### Post by Subcomfreak on 2012-08-07
I completely uninstalled the generic and installed the Pea backports. And I did reboot. So the answer is yes. I could try reinstalling them.

---

### Post by Subcomfreak on 2012-08-08
Could we possibly try to "wrap" the windows XP driver?

---

### Post by praseodym on 2012-08-08
Thats possible. But first: How much RAM do you have? Do you really need the -PAE-kernel? If no, try the "regular" generic-kernel and reinstall the driver, etc.

---

### Post by Subcomfreak on 2012-08-09
I have only 1gb of ram.

---

### Post by praseodym on 2012-08-09
So, then you can install the regular generic-kernel:
```

sudo apt-get install linux-image-generic linux-headers-generic build-essential dkms
```
Reboot. "uname -a" should show this kernel now. Install the driver again.

---

### Post by Subcomfreak on 2012-08-09
I can do this even without an internet connection? Or do I have to download some package in windows (where I have internet connectivity) and then copy it over to ubuntu and then run the command?

After that I simply need to install the generic back ports.

---

### Post by praseodym on 2012-08-09
You need these packages:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.2.0-27-generic_3.2.0-27.43_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.2.0-27-generic_3.2.0-27.43_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.2.0.27.29_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.2.0.27.29_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-27-generic_3.2.0-27.43_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-27-generic_3.2.0-27.43_i386.deb)

Save them in "Downlopads" and install via:

> sudo dpkg -i ~/Downloads/*.deb
Reboot, check the kernel with "uname -a" and try the driver again

---

### Post by Subcomfreak on 2012-08-10
Tried installing the generic back ports. It didn't work. Going to try and re-mount the other drivers.

---

### Post by Subcomfreak on 2012-08-10
trying the 2860 shoots out a "fatal rt2860 could not be found"
trying the 3090 shows
```
insmod/lib/modules/3.2.0-27-generic/updates/dkms/rt3090sta.ko
fatal: error inserting (insmod/lib/modules/3.2.0-27-generic/updates/dkms/rt3090sta.ko)invalid module format
```

---

### Post by praseodym on 2012-08-10
Is the driver shown in "additional drivers"?

---

### Post by Subcomfreak on 2012-08-10
there is nothing shown in additional drivers. Just two white boxes and a message at the top saying "no proprietary drivers are in use on this system"

---

### Post by praseodym on 2012-08-10
Uninstall the driver and install the backport-modules:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.2.0/linux-backports-modules-cw-3.3-3.2.0-27-generic_3.2.0-27.12_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.2.0/linux-backports-modules-cw-3.3-3.2.0-27-generic_3.2.0-27.12_i386.deb)

Reboot.

---

### Post by Subcomfreak on 2012-08-10
Excuse my ignorance, but what is the exact procedure for uninstalling the driver? I assume the instillation of the back ports is exactly the same a the kernel instillation, except for the “*” I will use the specific name of the back-ports module to avoid installing all of the .deb packages.

---

### Post by praseodym on 2012-08-10
It should be:

```
sudo apt-get remove --purge rt2860sta
```
Install the other .deb-Package with "dpkg"

---

### Post by Subcomfreak on 2012-08-10
Will do as soon as I can.

---

### Post by Subcomfreak on 2012-08-11
When I tried to uninstall the driver it said that it couldn't find that module installed.So I installed the back ports and rebooted. No luck there. Maybe te driver wasn't installed in the generic kernel?

---

### Post by praseodym on 2012-08-11
I compiled the "original" driver rt2860sta in a virtualbox with kernel 3.2.0.27-generic. Please find the tarball of the module attached, you need to unpack it and may need to rename it to "rt2860sta.ko". Save it in "Downloads" and copy it to the right plase:
```

sudo cp ~/Downloads/rt2860sta.ko /lib/modules/3.2.0-27-generic/kernel/drivers/net/wireless/
```
You also need the other package attached:

```
sudo mkdir /etc/Wireless/RT2860STA
sudo tar xvf 2591002-RT2860STA.dat.tar.gz /etc/Wireless/RT2860STA
sudo depmod -a
sudo update-initramfs -u
```
Reboot or load the driver:

```
sudo modprobe -v rt2860sta
```
Check:
```
iwconfig
lsmod
rfkill list
dmesg | grep rt2
```

---

### Post by Subcomfreak on 2012-08-12
I will try that first thing tomorrow! Thanks for putting so much work into my problem, even over the weekend!

---

### Post by Subcomfreak on 2012-08-13
Okay, the first procedure of moving the .ko file worked perfectly. However the second operation had a few problems, however I think I got it to work.

when I typed "sudo mkdir /etc/Wireless/RT2860STA" it said it couldn't ake the directory because it already existed. Okay, no problem. So I got to the next step:

sudo tar xvf 2591002-RT2860STA.dat.tar.gz /etc/Wireless/RT2860STA

It says that the directory "/etc/wireless/RT2860STA" does not exist in the archive. So I just extracted the tar and copyed over the file that was in it to the /etc directory using a modified version of the previous command. (Something like sudo cp /download/RT2860STA.dat /etc/wireless/rt2860STA) everything seemed okay. The next commaned appeared to work okay, it didn't have any output, so I assumed that it worked.

However, the next command (sudo update-initramfs -u) seemed to be doing some configuring in generic-pae even though I booted into generic. anyway, I loaded the driver with out re-booting and here is the other information that you requested:

```
   
  john@11ukkhunbuntu:~$ iwconfig
  
  lo        no wireless extensions.
  
   
   
  ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
  
            Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
  
            Bit Rate:1 Mb/s   
  
            RTS thr:off   Fragment thr:off
  
            Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
  
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
  
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
  
   
   
  eth0      no wireless extensions.
  
   
   
   
  john@11ukkhunbuntu:~$ lsmod
  
  Module                  Size  Used by
  
  rt2860sta             769176  1 
  
  nls_iso8859_1          12617  1 
  
  nls_cp437              12751  1 
  
  vfat                   17308  1 
  
  fat                    55605  1 vfat
  
  usb_storage            39646  1 
  
  deflate                12545  0 
  
  zlib_deflate           26622  1 deflate
  
  ctr                    13033  0 
  
  twofish_generic        16579  0 
  
  twofish_i586           12755  0 
  
  twofish_common         20823  2 twofish_generic,twofish_i586
  
  camellia               29212  0 
  
  serpent                29029  0 
  
  blowfish_generic       12474  0 
  
  blowfish_common        16635  1 blowfish_generic
  
  cast5                  24976  0 
  
  des_generic            21191  0 
  
  xcbc                   12711  0 
  
  rmd160                 16664  0 
  
  sha512_generic         16780  0 
  
  crypto_null            12782  0 
  
  af_key                 31531  2 
  
  rfcomm                 37291  0 
  
  bnep                   17711  2 
  
  bluetooth             164346  10 rfcomm,bnep
  
  binfmt_misc            17292  1 
  
  ppdev                  12849  0 
  
  snd_cs46xx             83775  2 
  
  gameport               15060  2 snd_cs46xx
  
  snd_ac97_codec        106082  1 snd_cs46xx
  
  ac97_bus               12642  1 snd_ac97_codec
  
  snd_pcm                80845  2 snd_cs46xx,snd_ac97_codec
  
  dcdbas                 14098  0 
  
  snd_seq_midi           13132  0 
  
  snd_rawmidi            25424  2 snd_cs46xx,snd_seq_midi
  
  snd_seq_midi_event     14475  1 snd_seq_midi
  
  snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
  
  snd_timer              28931  2 snd_pcm,snd_seq
  
  snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
  
  radeon                733687  2 
  
  psmouse                87213  0 
  
  serio_raw              13027  0 
  
  snd                    62064  11 snd_cs46xx,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
  
  ttm                    65344  1 radeon
  
  drm_kms_helper         45466  1 radeon
  
  drm                   197692  4 radeon,ttm,drm_kms_helper
  
  soundcore              14635  1 snd
  
  snd_page_alloc         14115  2 snd_cs46xx,snd_pcm
  
  intel_rng              12700  0 
  
  i2c_algo_bit           13199  1 radeon
  
  parport_pc             32114  1 
  
  mac_hid                13077  0 
  
  shpchp                 32325  0 
  
  lp                     17455  0 
  
  parport                40930  3 ppdev,parport_pc,lp
  
  aic7xxx               126038  0 
  
  scsi_transport_spi     25672  1 aic7xxx
  
  3c59x                  37445  0 
  
  floppy                 60310  0 
  
  john@11ukkhunbuntu:~$ 
  
   
   
  john@11ukkhunbuntu:~$ rfkill list
  
  john@11ukkhunbuntu:~$ 
  
   
   
  john@11ukkhunbuntu:~$ dmesg | grep rt2
  
  [ 1261.536644] rt2860 0000:02:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
  
  [ 1261.633668] <==== [COLOR=Red]rt2[/COLOR]8xx_init, Status=0
  
  [ 1261.684163] <====[COLOR=Red] rt2[/COLOR]8xx_init, Status=0
  
  [ 1455.158792] <====[COLOR=Red] rt2[/COLOR]8xx_init, Status=0
  
   
   
  
```

---

### Post by praseodym on 2012-08-13
Now remove (not edit) your wireless profile and setup a new one in "Infrastructure" mode. Check after that:

> lspci -nnk | grep -iA2 net
lsmod
iwconfig
sudo iwlist scan
iwlist chan
cat /etc/resolv.conf
cat /etc/network/interfaces

---

### Post by Subcomfreak on 2012-08-14
I'm not sure what a wireless profile is. Is it the options that I get when I select edit connections?

---

### Post by praseodym on 2012-08-14
Yes, it is.

---

### Post by Subcomfreak on 2012-08-14
Will do first thing tomorrow.

---

### Post by Subcomfreak on 2012-08-15
I booted up today and it seems to be able to connect to the internet. Still did exactly as you asked:

```
john@11ukkhunbuntu:~$  lspci -nnk | grep -iA2 net
02:04.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
    Subsystem: Dell Device [1028:0096]
    Kernel driver in use: 3c59x
--
02:0b.0 Network controller [0280]: Ralink corp. RT2760 Wireless 802.11n 1T/2R [1814:0701]
    Subsystem: Ralink corp. RT2760 Wireless 802.11n 1T/2R [1814:0701]
    Kernel driver in use: rt2860

john@11ukkhunbuntu:~$ lsmod
Module                  Size  Used by
deflate                12545  0 
zlib_deflate           26622  1 deflate
ctr                    13033  0 
twofish_generic        16579  0 
twofish_i586           12755  0 
twofish_common         20823  2 twofish_generic,twofish_i586
camellia               29212  0 
serpent                29029  0 
blowfish_generic       12474  0 
blowfish_common        16635  1 blowfish_generic
cast5                  24976  0 
des_generic            21191  0 
xcbc                   12711  0 
rmd160                 16664  0 
sha512_generic         16780  0 
crypto_null            12782  0 
af_key                 31531  2 
rfcomm                 37291  0 
bnep                   17711  2 
bluetooth             164346  10 rfcomm,bnep
snd_cs46xx             83775  2 
gameport               15060  2 snd_cs46xx
binfmt_misc            17292  1 
snd_ac97_codec        106082  1 snd_cs46xx
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_cs46xx,snd_ac97_codec
ppdev                  12849  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_cs46xx,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
dcdbas                 14098  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
radeon                733687  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87213  0 
serio_raw              13027  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
snd                    62064  11 snd_cs46xx,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt2860sta             769176  1 
i2c_algo_bit           13199  1 radeon
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_cs46xx,snd_pcm
parport_pc             32114  1 
mac_hid                13077  0 
intel_rng              12700  0 
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
aic7xxx               126038  0 
scsi_transport_spi     25672  1 aic7xxx
floppy                 60310  0 
3c59x                  37445  0 

lo        no wireless extensions.

ra0       Ralink STA  ESSID:"RosoRouter-guest"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 58:6D:8F:9B:A2:B5   
          Bit Rate=65 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-38 dBm  Noise level:-58 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

john@11ukkhunbuntu:~$ sudo iwlist scan
[sudo] password for john: 
lo        Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 58:6D:8F:9B:A2:B5
                    Protocol:802.11b/g/n
                    ESSID:"RosoRouter-guest"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-38 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:144 Mb/s
          Cell 02 - Address: 58:6D:8F:9B:A2:B3
                    Protocol:802.11b/g/n
                    ESSID:"RosoRouter"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-36 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000110104400010210470010D8E17EC120B3C9FBB0584A516170A335103C000103

eth0      Interface doesn't support scanning.

[john@11ukkhunbuntu:~$ iwlist chan
lo        no frequency information.

ra0       11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

eth0      no frequency information.
john@11ukkhunbuntu:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 127.0.0.1

john@11ukkhunbuntu:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 127.0.0.1
john@11ukkhunbuntu:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback



```

---

### Post by Subcomfreak on 2012-08-15
To test if everything is working, as it appears to be, I'm going to download a big file.

I downloaded 700mb in one shot and it seemed to work. Still need to do further testing to be sure though.

Also, this is probably not the right place to ask this, but how do I "un-nest" the generic version of ubuntu in the grub menu. Right now I have to go to previous linux distributions in order to boot. Also, if I run updates will it change my wireless situation?

---

