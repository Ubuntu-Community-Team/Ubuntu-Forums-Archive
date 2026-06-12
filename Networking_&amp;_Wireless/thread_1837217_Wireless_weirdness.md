---
title: "Wireless weirdness"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by ebasa on 2011-09-01
My ISP recently upgraded my speed to 25 MBS. When connected to the router with the wired connection download speetest shows 26 MBS, when connected with wireless on the same computer it shows 15 MPS.  Any ideas on how to get the wireless (AR5007) to increase its speed?

---

### Post by praseodym on 2011-09-01
Hi,

please show:

```
uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
sudo iwlist scan [COLOR="Red"]#which ESSID is yours?[/COLOR]
dmesg | grep ath
route -n
cat /etc/resolv.conf
```

---

### Post by ebasa on 2011-09-01
tom@tom-laptop:~$ uname -a
Linux tom-laptop 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64 GNU/Linux
tom@tom-laptop:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Kernel driver in use: ath5k
    Kernel modules: ath5k
--
08:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
tom@tom-laptop:~$ lsmod
Module                  Size  Used by
iptable_filter          2791  1 
ipt_MASQUERADE          1863  1 
iptable_nat             5219  1 
nf_nat                 19501  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      12980  3 iptable_nat,nf_nat
nf_conntrack           73966  4 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
ip_tables              18390  2 iptable_filter,iptable_nat
x_tables               22461  3 ipt_MASQUERADE,iptable_nat,ip_tables
hidp                   14218  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
sco                     9649  2 
bridge                 53216  0 
stp                     2171  1 bridge
bnep                   11884  2 
rfcomm                 40393  11 
l2cap                  34807  17 hidp,bnep,rfcomm
dm_crypt               13043  0 
arc4                    1473  2 
joydev                 11072  0 
snd_hda_codec_realtek   279008  1 
snd_hda_intel          25741  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
pcmcia                 35580  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 134437  0 
snd                    71251  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           22901  1 
rsrc_nonstatic          9830  1 yenta_socket
mac80211              238896  1 ath5k
ath                     9723  1 ath5k
btusb                  13001  2 
bluetooth              58685  10 hidp,sco,bnep,rfcomm,l2cap,btusb
edac_core              45423  0 
soundcore               8052  1 snd
acer_wmi               15829  0 
pcmcia_core            38176  3 pcmcia,yenta_socket,rsrc_nonstatic
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
i2c_piix4               9639  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
edac_mce_amd            9278  0 
k8temp                  4040  0 
psmouse                64576  0 
serio_raw               4918  0 
cfg80211              148725  3 ath5k,mac80211,ath
led_class               3764  3 ath5k,acer_wmi,sdhci
shpchp                 33711  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
dm_raid45              75532  0 
xor                     4685  1 dm_raid45
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
radeon                742816  2 
8139too                22245  0 
ttm                    60847  1 radeon
usbhid                 41116  0 
drm_kms_helper         30742  1 radeon
8139cp                 19541  0 
hid                    83472  2 hidp,usbhid
mii                     5237  2 8139too,8139cp
pata_atiixp             4209  0 
drm                   198948  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            6024  1 radeon
sata_sil                8895  2 
ramzswap                7857  1 
xvmalloc                5054  1 ramzswap
lzo_decompress          2533  1 ramzswap
lzo_compress            2325  1 ramzswap
tom@tom-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"RogersDE87"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:21:29:64:DE:87   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

pan1      no wireless extensions.

tom@tom-laptop:~$ sudo iwlist scan #which ESSID is yours?
[sudo] password for tom: 
- Address: 00:21:29:64:DE:87
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"RogersDE87"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001d737ac0a
                    Extra: Last beacon: 50ms ago
                    IE: Unknown: 000A526F6765727344453837
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD06001018020011
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

---

### Post by praseodym on 2011-09-01
Try:

```
sudo iwconfig wlan0 rate auto
iconfig #control
```
You are using no encryption? Are you sure about that? I would prefer WPA2-AES if possible.

---

### Post by ebasa on 2011-09-01
eth0      Link encap:Ethernet  HWaddr 00:1b:24:22:6a:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:42711 errors:2 dropped:50 overruns:2 frame:0
          TX packets:24203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61587135 (61.5 MB)  TX bytes:4857239 (4.8 MB)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:628 (628.0 B)  TX bytes:628 (628.0 B)

pan0      Link encap:Ethernet  HWaddr ba:68:de:56:bc:b0  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:2373 (2.3 KB)

pan1      Link encap:Ethernet  HWaddr 22:ad:6b:d9:45:f8  
          inet addr:10.241.89.1  Bcast:10.241.89.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:2145 (2.1 KB)

pan0:avahi Link encap:Ethernet  HWaddr ba:68:de:56:bc:b0  
          inet addr:169.254.10.135  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:41:65:46  
          inet addr:192.168.24.101  Bcast:192.168.24.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33959 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63096035 (63.0 MB)  TX bytes:5267224 (5.2 MB)

---

### Post by praseodym on 2011-09-01
Sorry, typo:

```
i[COLOR="Red"]w[/COLOR]config
```

Try to update your system (kernel 2.6.32-33 is the newest one, dont forget to reboot) and update the driver with the backport-modules afterwards:

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

and reboot again.

---

