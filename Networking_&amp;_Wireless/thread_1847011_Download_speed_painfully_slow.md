---
title: "Download speed painfully slow"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by jbrya029 on 2011-09-20
Hi, I'm relatively new to Ubuntu and just installed 10.4. I tried 11 first but noticed that the internet was impossibly slow. 

I went to speedtest.net and it said that my ping was 316ms with download of .46Mbps and upload of .78Mbps. I looked through my wireless driver CD and it said that it only supported Ubuntu 10.4 (so I went back and installed this one).

 However, I have the exact same problem here. I've disable Ipv6 and installed the driver (./configure, make, make install). My download is still around .4Mbps and if I'm trying to load a video on youtube it's more like .09Mbps. I've searched forums everywhere and I can't find anything that works.

 My wireless card is an Asus PCE-N10. Please help!

---

### Post by praseodym on 2011-09-20
Hi,

please show the terminal outputs of:

```
lspci -nnk | grep -iA2 net
ifconfig -a
iwconfig
lsmod
route -n
cat /etc/resolv.conf
```

---

### Post by jbrya029 on 2011-09-20
desktop:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
	Kernel driver in use: rtl8192CE
	Kernel modules: r8192ce_pci
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Kernel driver in use: r8169
	Kernel modules: r8169
__________________________________________________


desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 40:61:86:95:45:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

wlan0     Link encap:Ethernet  HWaddr f4:6d:04:a1:31:6f  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3374079 (3.3 MB)  TX bytes:347493 (347.4 KB)
          Interrupt:16 Memory:f8088000-f8088100 
______________________________


desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  ESSID:"snell"  Nickname:"rtl8192CE"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:23:97:20:E4:B9   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=79/100  Signal level=-60 dBm  Noise level=-109 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

________________________


desktop:~$ lsmod
Module                  Size  Used by
michael_mic             1732  8 
arc4                    1153  4 
binfmt_misc             6587  1 
snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
joydev                  8740  0 
softcursor              1189  1 bitblit
i2c_piix4               8335  0 
parport_pc             25962  1 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
serio_raw               3978  0 
r8192ce_pci           461495  0 
fglrx                2092908  31 
agpgart                31724  1 fglrx
vga16fb                11385  1 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  0 
pata_atiixp             3148  2 
r8169                  34140  0 
mii                     4381  1 r8169

_______________________________________


desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

___________________________________________


desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain westell.com
search westell.com
nameserver 192.168.1.1

---

### Post by praseodym on 2011-09-21
You cann add the nameservers of your ISP or the google public NS directly in the network-manager applet (IPv4-settings->Pull-down-menu, choose "Automatic (DHCP), addresses only" and add them in "DNS-Servers", separated by comma

---

### Post by jbrya029 on 2011-09-21
Did all, still the same speed. 0.52 Mbps download 0.71 Mbps upload. On my Windows netbook I got about a 4.8 and a 0.7 immediately after I ran the test on ubuntu.

---

### Post by praseodym on 2011-09-21
Try to add the mtu-value of your ISP as number (normally 1500 or 1492) instead of "Automatic" in the network-manager applet, seems like a download thing.

---

### Post by jbrya029 on 2011-09-21
1492 did it! Thank you!

---

### Post by theller on 2012-10-29
This solution worked for me too. This was on a dell machine (Ubuntu 12.04) at a school connected to a switch. Guess the switch doesn't like 1500 MTU.

I just tested. Speeds went from KiB/s to MiB/s
Ubuntu 12.04 finished downloading 12.10 (32bit) and 12.10 (64bit).
Windows - still downloading 32bit, it just went from 3 to 4 min.

---

### Post by wildmanne39 on 2012-10-29
Old thread closed.

---

