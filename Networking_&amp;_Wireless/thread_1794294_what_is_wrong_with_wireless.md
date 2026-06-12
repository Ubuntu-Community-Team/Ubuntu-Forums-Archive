---
title: "what is wrong with wireless?"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by enuckon on 2011-06-30
Connected freshly installed 10.04.2 to a wireless network through a router.  Everything looks correct -- IP is assigned, connection is on, the system shows up on the router -- except that there is no internet connection and I can't ping the router or anywhere else.  According to the router, the wireless signal at the ubuntu system is stronger than at the sitting-right-next-to-it windows system with *working* internet.  what is this?  Should I replace current driver?  

> 
__________________________________________________
user@lynx:~$ sudo lshw -C network
...
*-network

     description: Wireless interface
     physical id: 1
     logical name: wlan0
     serial: 00:15:af:xx:xx:xx
     capabilities: ethernet physical wireless
     configuration: broadcast=yes ip=192.168.1.112 multicast=yes    wireless=IEEE 802.11bg
__________________________________________________

Would appreciate any suggestion.

---

### Post by chili555 on 2011-06-30
> Should I replace current driver? Which is what? Please let us see:```
lspci -nn
lsmod
```Thanks.

---

### Post by enuckon on 2011-06-30
Below is the output of the two commands:

"""

```
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801IR (ICH9R) LPC Interface Controller [8086:2916] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller [8086:2920] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller [8086:2926] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G84 [GeForce 8600 GTS] [10de:0400] (rev a1)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
03:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
03:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
05:03.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 70)


Module                  Size  Used by
aes_i586                7268  2 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_analog    58598  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22005  2 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nouveau               467048  2 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ttm                    49943  1 nouveau
drm_kms_helper         29329  1 nouveau
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rtl8187                50680  0 
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
cfg80211              126528  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
asus_atk0110            9017  0 
usbhid                 36110  0 
snd                    54180  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162409  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            5028  1 nouveau
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
intel_agp              24375  0 
agpgart                31724  3 ttm,drm,intel_agp
parport                32635  2 ppdev,lp
hid                    67064  1 usbhid
ohci1394               26950  0 
floppy                 53016  0 
ieee1394               81181  1 ohci1394
pata_jmicron            1843  0 
sky2                   40807  0 
ahci                   32200  0 
```

"""

---

### Post by chili555 on 2011-06-30
The driver looks OK; no conflicts that I can see. Now, let's see:```
ifconfig
route -n
cat /etc/resolv.conf
sudo iwlist wlan0 scan
```Thanks.

---

### Post by enuckon on 2011-07-01
"iwlist wlan0 scan" shows visible wireless networks including the one I am connected to.  "/etc/resolv.conf", generated by NM, has "domain" line, "search" line and "nameserver" with router's IP.  

It looks like that the incoming traffic is existent.  However, it is extremely slow - 200 bytes/s, and it is periodic, like 3 seconds between peaks.  It is not stable and strong enough for pinging.   Thanks for taking your time to respond.

---

### Post by chili555 on 2011-07-01
I have researched this twitchy driver a few times in the past. There are many complaints that it's slow and has poor signal strength. Here is one thread that ends in SOLVED: [http://ubuntuforums.org/showthread.php?t=1444096&page=3](http://ubuntuforums.org/showthread.php?t=1444096&page=3)

If you need any further guidance, please post back.

---

### Post by enuckon on 2011-07-01
Thanks! Will try the link. Here is output of the commands:

```
user@lynx:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:38:52:6c   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:292 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:292 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:28027 (28.0 KB)  TX bytes:28027 (28.0 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:15:af:64:f3:09   
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::215:afff:fe64:f309/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1508 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:734 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:381726 (381.7 KB)  TX bytes:58062 (58.0 KB) 
 

user@lynx:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0 
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0 


user@lynx:~$ cat /etc/resolv.conf 
# Generated by NetworkManager 
domain fsd1.bestinternet.net 
search fsd1.bestinternet.net 
nameserver 192.168.1.1 


user@lynx:~$ sudo iwlist wlan0 scan 
[sudo] password for user:  
wlan0     Scan completed : 
          Cell 01 - Address: C0:3F:0E:BA:73:FA 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=36/70  Signal level=-74 dBm   
                    Encryption key:on 
                    ESSID:"tyro1" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=0000000024973194 
                    Extra: Last beacon: 304ms ago 
                    IE: Unknown: 0005646F6D696B 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030106 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000 
                    IE: Unknown: DD090010180204F0050000 
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: DD1A00904C3406001700000000000000000000000000000000000000 
          Cell 02 - Address: 00:22:3F:39:DE:0E 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=44/70  Signal level=-66 dBm   
                    Encryption key:on 
                    ESSID:"Tuko-g" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000239160f7b6f 
                    Extra: Last beacon: 1644ms ago 
                    IE: Unknown: 000654756B6F2D67 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 03010B 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B00010310470010A8940D9DC50BBB463097B91BBD68871F1021000D4E4554474541522C20496E632E10230008574E44523333303010240008574E4452333330301042000230311054000800060050F204000110110008574E445233333030100800020084103C000103 
                    IE: Unknown: DD090010180200F0040000 
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
 

```

As I said, the signal seeps through periodically, ~3 secs between peaks of 200 bytes/s, with the strength sufficient only for detection.

---

### Post by enuckon on 2011-07-02
An Intrepid laptop, next to the Lynx desktop I am trying to straighten up, has a similar weak and dropping wireless connection.  However, (a) it is not as weak as for the Lynx desktop above -- sometimes the internet works; and (b) it can always be carried closer to the router -- which always make the connection strong and stable.  For the Intrepid laptop, "sudo lshw -C network" gives: 

```
[sudo] password for chkn: 
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:34:69:f5
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.117 latency=64 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

``` 

Different driver -- similar problem: relatively strong connection with no internet.

---

### Post by chili555 on 2011-07-02
> Different driver -- similar problem: relatively strong connection with no internet.Does it work better with the router on a different channel? Is there a signal strength setting in the router? Please see attached. Is the router set to WPA and WPA2 mixed mode? I have better luck with WPA2 only.

---

