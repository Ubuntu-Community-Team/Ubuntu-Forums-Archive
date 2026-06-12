---
title: "eth0 not working help !!"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by kevinorourke2008 on 2011-08-01
Hi all, I'm using ubuntu 10.04 on my acer aspire one.
I can connect to the internet using my wireless but not my eth0 wired connection.
Could someone run me through how to delete the settings (and where to find the settings) and reinstall the needed software to get my wired connection up and running.
It was working up to a couple of weeks ago when it just stopped working.

any other information I can get to help would be most appreciated.

Cheers kev

---

### Post by chili555 on 2011-08-02
I'm not sure you need to delete any settings yet. Let's see what you have and see why it isn't working. Let's see what kind of ethernet card you have. Please run and post:```
lspci -nn | grep 0200
```Let's see if the module is loading:```
lsmod
```Is an interface present?```
ifconfig
```Last, are there any interesting messages?```
dmesg | grep eth0
```Thanks.

---

### Post by kevinorourke2008 on 2011-08-03
hello, i typed what you had written and here are the results, 

```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
```

lsmod brings up,

```
Module                  Size  Used by
isofs                  29250  0 
udf                    78785  0 
crc_itu_t               1371  1 udf
ums_cypress             2058  0 
joydev                  8740  0 
nls_iso8859_1           3249  4 
nls_cp437               4919  4 
vfat                    8933  4 
fat                    47767  1 vfat
xt_limit                1382  8 
xt_tcpudp               2011  7 
ipt_LOG                 4542  8 
ipt_MASQUERADE          1407  0 
xt_DSCP                 1677  0 
ipt_REJECT              1928  1 
nf_conntrack_irc        3332  0 
nf_conntrack_ftp        5381  0 
xt_state                1098  6 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
iptable_nat             3543  0 
nf_nat                 15560  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10346  9 iptable_nat,nf_nat
nf_conntrack           60975  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
iptable_mangle          1549  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
iptable_filter          1369  1 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
ip_tables               9899  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               14175  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mmc_block               8258  2 
i915                  288611  3 
uvcvideo               57374  0 
drm_kms_helper         29329  1 i915
snd                    54244  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath5k                 121632  0 
acerhdf                 6691  0 
usbhid                 36110  0 
videodev               34361  1 uvcvideo
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
sdhci_pci               5470  0 
jmb38x_ms               7311  0 
mac80211              205402  1 ath5k
ath                     7611  1 ath5k
usb_storage            39841  4 ums_cypress
v4l1_compat            13251  2 uvcvideo,videodev
hid                    67288  1 usbhid
intel_agp              24375  2 i915
sdhci                  15494  1 sdhci_pci
video                  17375  1 i915
soundcore               6620  1 snd
memstick                8237  1 jmb38x_ms
psmouse                63677  0 
serio_raw               3978  0 
cfg80211              126144  3 ath5k,mac80211,ath
led_class               2864  2 ath5k,sdhci
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  34140  0 
mii                     4381  1 r8169
```

ipconfig brings up,

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:f1:a0:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50320 (50.3 KB)  TX bytes:50320 (50.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:4b:1a:5c  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe4b:1a5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:140843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:177894328 (177.8 MB)  TX bytes:12923920 (12.9 MB)
```

dmesg | grep eth0 brings,

```
[    1.156251] eth0: RTL8102e at 0xf804e000, 00:1e:68:f1:a0:18, XID 04a00000 IRQ 28
[   20.622010] r8169: eth0: link down
[   20.623127] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  267.665704] r8169: eth0: link down
[  267.666213] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5907.307454] r8169: eth0: link down
[ 5907.308732] ADDRCONF(NETDEV_UP): eth0: link is not ready
[11797.181495] r8169: eth0: link down
[11797.181987] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

to be honest with you I haven't a clue what most of this means but i sure would like my wired connection going again.

Cheers Kev

---

### Post by chili555 on 2011-08-03
Your ethernet card has a driver associated with it, r8169. It is loading on boot as expected. Let's do some diagnostics. With the cable firmly attached and checked at both ends, please run and post:```
sudo nm-tool
```We are looking to see if the card and cable appear healthy. Also post:```
sudo cat /var/log/syslog | grep -e r8169 -e etwork | tail -n25
```We want to see what the system logs say about the driver and Network Manager. Thanks.

---

### Post by kevinorourke2008 on 2011-08-04
Hi chili555,
some more info for you, it was working just fine but suddenly stopped. I am still dual booting with xp and it works fine, so i don't think it is a physical problem.

sudo nm-tool brings


NetworkManager Tool

State: connected

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1E:68:F1:A0:18

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: wlan0  [Auto NETGEAR32] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           no
  HW Address:        00:23:4D:4B:1A:5C

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *NETGEAR32:      Infra, 00:18:4D:0A:B8:F4, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA

  IPv4 Settings:
    Address:         192.168.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1



sudo cat /var/log/syslog | grep -e r8169 -e etwork | tail -n25
 
Aug  4 09:48:43 kevino-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Aug  4 09:48:43 kevino-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Aug  4 09:48:43 kevino-laptop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Aug  4 09:48:43 kevino-laptop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Aug  4 09:48:43 kevino-laptop NetworkManager: <info>  dhclient started with pid 3143
Aug  4 09:48:43 kevino-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug  4 09:48:43 kevino-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Aug  4 09:48:43 kevino-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Aug  4 09:48:43 kevino-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug  4 09:48:44 kevino-laptop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Aug  4 09:48:44 kevino-laptop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Aug  4 09:48:44 kevino-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug  4 09:48:44 kevino-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Aug  4 09:48:44 kevino-laptop NetworkManager: <info>    address 192.168.0.3
Aug  4 09:48:44 kevino-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Aug  4 09:48:44 kevino-laptop NetworkManager: <info>    gateway 192.168.0.1
Aug  4 09:48:44 kevino-laptop NetworkManager: <info>    nameserver '192.168.0.1'
Aug  4 09:48:44 kevino-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug  4 09:48:44 kevino-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug  4 09:48:44 kevino-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Aug  4 09:48:45 kevino-laptop NetworkManager: <info>  Policy set 'Auto NETGEAR32' (wlan0) as default for routing and DNS.
Aug  4 09:48:45 kevino-laptop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Aug  4 09:48:45 kevino-laptop NetworkManager: <info>  Policy set 'Auto Ethernet' (eth0) as default for routing and DNS.
Aug  4 09:48:45 kevino-laptop NetworkManager: <info>  Activation (eth0) successful, device activated.
Aug  4 09:48:45 kevino-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.


I hope this helps ?

cheers kev

---

### Post by chili555 on 2011-08-04
Well, there is good news and bad news. First, the good news:> - Device: eth0 [Auto Ethernet] ------------------------------------------------
Type: Wired
Driver: r8169
[COLOR="Red"]State: connected[/COLOR]
Default: yes
HW Address: 00:1E:68:F1:A0:18

Capabilities:
Carrier Detect: yes
Speed: 100 Mb/s

Wired Properties
Carrier: on

IPv4 Settings:
[COLOR="Red"]Address: 192.168.0.3[/COLOR]
Prefix: 24 (255.255.255.0)
Gateway: 192.168.0.1

DNS: 192.168.0.1Your ethernet is connected and working as expected. The bad news is that Network Manager is designed to disallow a wireless connection if you have wired ethernet connected. It's not doing its job correctly, because:> Type: 802.11 WiFi
Driver: ath5k
State: connected
Default: no
HW Address: 00:23:4D:4B:1A:5C

Capabilities:
Speed: 54 Mb/s

Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points (* = current AP)
*NETGEAR32: Infra, 00:18:4D:0A:B8:F4, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA

IPv4 Settings:
[COLOR="Red"]Address: 192.168.0.2[/COLOR]
Prefix: 24 (255.255.255.0)
Gateway: 192.168.0.1

DNS: 192.168.0.1
Can you please click the Network Manager icon, uncheck Enable Wireless and reboot? Please run:```
ifconfig
```Does your ethernet interface eth0 have an IP address? Can you surf the web?

---

### Post by peatbog on 2011-08-04
Hi. I'm having a similar problem after an upgrade to 11.04. I've tried and failed to fix it numerous times in the past few days (by attempting to follow advice from various forums and techy sites). I'm completely new to Linux based OS's and this problem seems beyond my current skill level!

based on what I've been reading apparently this stuff will be useful:

`lspci -nm | grep 0200' yeilds:
```
03:00.0 "0200" "10ec" "8168" -r03 "103c" "144a"
````lsmod' :
```
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
pppoe                  17476  0 
pppox                  13158  1 pppoe
nls_utf8               12493  1 
isofs                  39571  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  1 
binfmt_misc            13213  1 
arc4                   12473  2 
snd_hda_codec_idt      60537  1 
ath9k                 103633  0 
i915                  450944  7 
radeon                896428  1 
snd_seq_midi           13132  0 
snd_hda_intel          24140  2 
usbhid                 41704  0 
joydev                 17322  0 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
mac80211              257001  1 ath9k
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ttm                    65184  1 radeon
uvcvideo               66851  0 
hid                    77084  1 usbhid
snd_rawmidi            25269  1 snd_seq_midi
ath9k_common           13611  1 ath9k
hp_wmi                 13418  0 
drm_kms_helper         40745  2 radeon,i915
sparse_keymap          13666  1 hp_wmi
videodev               75143  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
ath9k_hw              300328  2 ath9k,ath9k_common
drm                   180037  6 radeon,i915,ttm,drm_kms_helper
psmouse                73312  0 
ath                    19141  2 ath9k,ath9k_hw
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
cfg80211              156212  3 ath9k,mac80211,ath
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_ips              17769  0 
serio_raw              12990  0 
i2c_algo_bit           13184  2 radeon,i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
hp_accel               21632  0 
lis3lv02d              19285  1 hp_accel
input_polldev          13735  1 lis3lv02d
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  3 
r8169                  42534  0 
libahci                25548  1 ahci
```
`ifconfig'
```

eth0      Link encap:Ethernet  HWaddr 98:4b:e1:a8:74:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0xe000 

eth0:avahi Link encap:Ethernet  HWaddr 98:4b:e1:a8:74:63  
          inet addr:169.254.8.197  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:41 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57888 (57.8 KB)  TX bytes:57888 (57.8 KB)
```
`dmesg | grep eth0'
```
[    2.395904] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xf807e000, 98:4b:e1:a8:74:63, XID 083000c0 IRQ 41
[    9.653316] r8169 0000:03:00.0: eth0: link down
[    9.653546] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  117.334628] r8169 0000:03:00.0: eth0: link down
[  117.335065] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  138.783139] r8169 0000:03:00.0: eth0: link down
[  138.783581] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  231.007651] r8169 0000:03:00.0: eth0: link down
[  231.008089] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3005.484246] r8169 0000:03:00.0: eth0: link down
[ 3005.484838] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3205.780229] r8169 0000:03:00.0: eth0: link down
[ 3205.780663] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4907.200130] r8169 0000:03:00.0: eth0: link down
[ 4907.200423] ADDRCONF(NETDEV_UP): eth0: link is not ready
```
`sudo nm-tool'
```
 NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        90:00:4E:22:A9:E9

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        98:4B:E1:A8:74:63

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off
```
`cat /var/log/syslog | grep -e ath9k | tail -n25'
```
Aug  4 13:24:27 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.305446] ath9k 0000:02:00.0: setting latency timer to 64
Aug  4 13:24:27 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.368793] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Aug  4 13:24:27 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.369717] Registered led device: ath9k-phy0::radio
Aug  4 13:24:27 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.369749] Registered led device: ath9k-phy0::assoc
Aug  4 13:24:27 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.369776] Registered led device: ath9k-phy0::tx
Aug  4 13:24:27 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.369829] Registered led device: ath9k-phy0::rx
Aug  4 13:24:27 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[817]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Aug  4 13:24:28 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [   10.673891] Modules linked in: snd_hda_codec_idt arc4 snd_hda_intel(+) snd_hda_codec snd_hwdep snd_pcm snd_seq_midi ath9k snd_rawmidi snd_seq_midi_event snd_seq mac80211 radeon(+) uvcvideo hp_wmi joydev sparse_keymap i915 snd_timer videodev usbhid snd_seq_device ath9k_common ath9k_hw ath ttm intel_ips hid psmouse cfg80211 drm_kms_helper serio_raw drm snd soundcore snd_page_alloc i2c_algo_bit hp_accel lis3lv02d input_polldev video lp parport ahci libahci r8169
Aug  4 19:34:40 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [   25.418446] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  4 19:34:40 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [   25.418460] ath9k 0000:02:00.0: setting latency timer to 64
Aug  4 19:34:40 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [   25.503820] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Aug  4 19:34:40 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [   25.504598] Registered led device: ath9k-phy0::radio
Aug  4 19:34:40 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [   25.504623] Registered led device: ath9k-phy0::assoc
Aug  4 19:34:40 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [   25.504647] Registered led device: ath9k-phy0::tx
Aug  4 19:34:40 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [   25.504671] Registered led device: ath9k-phy0::rx
Aug  4 19:34:41 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[729]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Aug  4 19:34:42 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [   27.293248] Modules linked in: snd_hda_codec_idt radeon(+) snd_hda_intel(+) arc4 i915 snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi ath9k snd_seq_midi_event uvcvideo hp_wmi snd_seq joydev videodev sparse_keymap snd_timer snd_seq_device mac80211 usbhid ttm psmouse drm_kms_helper hid snd ath9k_common ath9k_hw ath intel_ips drm cfg80211 serio_raw soundcore snd_page_alloc i2c_algo_bit hp_accel video lis3lv02d input_polldev lp parport ahci libahci r8169
Aug  4 20:52:33 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.235373] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  4 20:52:33 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.235385] ath9k 0000:02:00.0: setting latency timer to 64
Aug  4 20:52:33 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.294444] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Aug  4 20:52:33 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.295707] Registered led device: ath9k-phy0::radio
Aug  4 20:52:33 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.295733] Registered led device: ath9k-phy0::assoc
Aug  4 20:52:33 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.295763] Registered led device: ath9k-phy0::tx
Aug  4 20:52:33 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.295796] Registered led device: ath9k-phy0::rx
Aug  4 20:52:33 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[708]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
```
Any help will be much appreciated

---

### Post by chili555 on 2011-08-04
> cat /var/log/syslog | grep -e [COLOR="Red"]ath9k[/COLOR] | tail -n25That's your wireless driver. Instead, let's see:```
cat /var/log/syslog | grep r8169 | tail -n25
```

---

### Post by kevinorourke2008 on 2011-08-04
I've done what you said to do I.E. switch off the wireless in the notification area at the top of the screen and rebooted and it now works.
What I have done though is opened a terminal and typed ifconfig and the results are;

eth0      Link encap:Ethernet  HWaddr 00:1e:68:f1:a0:18  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fef1:a018/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1538 (1.5 KB)  TX bytes:3984 (3.9 KB)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:496 errors:0 dropped:0 overruns:0 frame:0
          TX packets:496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39360 (39.3 KB)  TX bytes:39360 (39.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:4b:1a:5c  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe4b:1a5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:837 (837.0 B)  TX bytes:3400 (3.4 KB)

cheers kevin

---

### Post by chili555 on 2011-08-04
> eth0 Link encap:Ethernet HWaddr 00:1e:68:f1:a0:18
inet addr:192.168.0.3 Bcast:192.168.0.255 Mask:255.255.255.0

wlan0 Link encap:Ethernet HWaddr 00:23:4d:4b:1a:5c
inet addr:192.168.0.2 Bcast:192.168.0.255 Same problem. Please disable wireless and don't reboot. Does the wired work?

---

### Post by peatbog on 2011-08-04
> Quote:
                                                 cat /var/log/syslog | grep -e [COLOR=Red]ath9k[/COLOR] | tail -n25                                 
That's your wireless driver. Instead, let's see:     Code:
     cat /var/log/syslog | grep r8169 | tail -n25
of course! apologies

```

Aug  5 08:27:46 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[710]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Aug  5 08:27:46 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.531095] r8169 0000:03:00.0: eth0: link down
Aug  5 08:27:47 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [   10.643847] Modules linked in: snd_hda_codec_idt radeon(+) arc4 snd_hda_intel(+) snd_hda_codec snd_hwdep i915 snd_seq_midi ath9k snd_rawmidi snd_pcm ttm snd_seq_midi_event mac80211 snd_seq usbhid hid snd_timer drm_kms_helper joydev hp_wmi sparse_keymap snd_seq_device uvcvideo ath9k_common drm videodev ath9k_hw psmouse ath snd cfg80211 intel_ips serio_raw i2c_algo_bit soundcore snd_page_alloc video hp_accel lis3lv02d input_polldev lp parport ahci r8169 libahci
Aug  5 08:37:48 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.396611] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Aug  5 08:37:48 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.396636] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug  5 08:37:48 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.396683] r8169 0000:03:00.0: setting latency timer to 64
Aug  5 08:37:48 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.396751] r8169 0000:03:00.0: irq 41 for MSI/MSI-X
Aug  5 08:37:48 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.397305] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xf807e000, 98:4b:e1:a8:74:63, XID 083000c0 IRQ 41
Aug  5 08:37:48 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[810]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Aug  5 08:37:49 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.762076] r8169 0000:03:00.0: eth0: link down
Aug  5 08:37:50 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [   10.856208] Modules linked in: snd_hda_codec_idt arc4 ath9k radeon(+) snd_hda_intel(+) snd_hda_codec snd_hwdep snd_pcm mac80211 snd_seq_midi i915 ttm snd_rawmidi usbhid ath9k_common ath9k_hw hid ath hp_wmi snd_seq_midi_event snd_seq uvcvideo joydev sparse_keymap cfg80211 psmouse snd_timer snd_seq_device drm_kms_helper drm videodev serio_raw i2c_algo_bit snd intel_ips soundcore snd_page_alloc hp_accel video lis3lv02d input_polldev lp parport ahci r8169 libahci
Aug  5 08:39:08 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.409115] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Aug  5 08:39:08 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.409214] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug  5 08:39:08 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.409332] r8169 0000:03:00.0: setting latency timer to 64
Aug  5 08:39:08 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.409400] r8169 0000:03:00.0: irq 41 for MSI/MSI-X
Aug  5 08:39:08 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.409962] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xf806c000, 98:4b:e1:a8:74:63, XID 083000c0 IRQ 41
Aug  5 08:39:08 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[826]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Aug  5 08:39:08 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [   18.927881] r8169 0000:03:00.0: eth0: link down
Aug  5 09:03:33 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.407090] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Aug  5 09:03:33 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.407116] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug  5 09:03:33 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.407162] r8169 0000:03:00.0: setting latency timer to 64
Aug  5 09:03:33 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.407231] r8169 0000:03:00.0: irq 41 for MSI/MSI-X
Aug  5 09:03:33 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    2.407792] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xf807c000, 98:4b:e1:a8:74:63, XID 083000c0 IRQ 41
Aug  5 09:03:33 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[718]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Aug  5 09:03:33 aaron-HP-Pavilion-dv6-Notebook-PC kernel: [    9.531802] r8169 0000:03:00.0: eth0: link down
```
Chilli, thanks for taking the time to look at this - much appreciated

---

### Post by chili555 on 2011-08-06
This bothers me:> Wired Properties
    Carrier:         offThat sort of suggests that, even though the cable is firmly attached at both ends, the network card doesn't see any signal from the router, modem or other access point at the other end. Is this computer dual-booted with Windows? This may be an issue: [http://www.linuxquestions.org/questions/linux-networking-3/realtek-8139-8168-8169-on-2-6-21-3-or-newer-593495/](http://www.linuxquestions.org/questions/linux-networking-3/realtek-8139-8168-8169-on-2-6-21-3-or-newer-593495/)> you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this options through Windows' device manager. Finally, I see nothing amiss in the driver readings. Let's see what Network Manager is doing all this time. Click the Network Manager icon and try to connect with wired ethernet. Then run and post:```
sudo cat /var/log/syslog | grep etwork | tail -n25
```

---

### Post by peatbog on 2011-08-06
```
sudo cat var/log/syslog | grep etwork | tail -n25

Aug  6 23:46:59 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Aug  6 23:46:59 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> Trying to start the supplicant...
Aug  6 23:46:59 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (wlan0): supplicant manager state:  down -> idle
Aug  6 23:47:51 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> disable requested (sleeping: no  enabled: yes)
Aug  6 23:47:51 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> sleeping or disabling...
Aug  6 23:47:51 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (wlan0): now unmanaged
Aug  6 23:47:51 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (wlan0): device state change: 2 -> 1 (reason 37)
Aug  6 23:47:51 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (eth0): now unmanaged
Aug  6 23:47:51 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (eth0): device state change: 2 -> 1 (reason 37)
Aug  6 23:47:51 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (eth0): cleaning up...
Aug  6 23:47:51 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (eth0): taking down device.
Aug  6 23:47:55 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> enable requested (sleeping: no  enabled: no)
Aug  6 23:47:55 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> waking up and re-enabling...
Aug  6 23:47:55 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> WWAN now enabled by management service
Aug  6 23:47:55 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (wlan0): now managed
Aug  6 23:47:55 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Aug  6 23:47:55 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (wlan0): bringing up device.
Aug  6 23:47:55 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (wlan0): deactivating device (reason: 2).
Aug  6 23:47:55 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Aug  6 23:47:55 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Aug  6 23:47:55 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (eth0): now managed
Aug  6 23:47:55 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Aug  6 23:47:55 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (eth0): bringing up device.
Aug  6 23:47:55 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (eth0): preparing device.
Aug  6 23:47:55 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[739]: <info> (eth0): deactivating device (reason: 2).

```

No it's not a dual boot machine - It came new with win7 on it but that was erased when I installed Ubuntu 10.10. It's a HP notebook. It might be noteworthy that the wired connection was working fine until 11.04. I have a desktop also with 11.04 on which the wired connection works beautifully - I'm using it now - same ethernet cable I try in the notebook. No wireless in the desktop though. 

What your saying fits with my experience at this end. My modem has little led's for, amongst other things, ethernet and usb connection - when plugged into the desktop the modem ethernet led lights up but not when in the notebook.

I tried connecting with NM but the best I can do is `enable networking' - the wired network options all remain greyed out - anyway that's all I could do before getting the log above - I presume `deactivating device (reason 2)' is our culprit, or at least part thereof?

Thanks again for taking the time. Failing this I can always try another distribution - Ubuntu doesn't seem to get along with this notebook - there has been graphics driver issues previously also.

---

### Post by chili555 on 2011-08-06
> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))That's a bit mysterious to me. Is there any listing except loopback here?```
cat /etc/network/interfaces
```If so, remove it with *sudo gedit*.>  <info> (eth0): deactivating device (reason: 2).I'm pretty sure that means, roughly, 'we don't see a carrier signal here; there's no reason to continue.' You might check here: [http://ubuntuforums.org/showthread.php?t=1811819&highlight=r8168](http://ubuntuforums.org/showthread.php?t=1811819&highlight=r8168)

If you'd like to try it, I'll be happy to assist.

---

### Post by peatbog on 2011-08-07
> That's a bit mysterious to me. Is there any listing except loopback here? 	Code:
 	cat /etc/network/interfaces


there was some eth0 stuff that I put there but it was hashed out after a failed attempt to fix it following some thread. it's gone now.

> 
 You might check here: [http://ubuntuforums.org/showthread.p...ighlight=r8168]("http://ubuntuforums.org/showthread.php?t=1811819&highlight=r8168")
Thanks for pointing this out - I read the thread and their problem sounded pretty similar to mine so I installed the r8168 driver. It looked promising for a second too! the Network Manager app whirred into life and it was trying to connect eth0 but it just keeps trying and never manages to connect - I don't think I changed anything when I was originally trying to find a solution - I did in *etc/network/interfaces* but changed it back again - I also messed around with */etc/NetworkManager/NetworkManager.conf* but I don't think there was any net change there either

looked at the logs again after installing the new driver:
```
root@aaron-HP-Pavilion-dv6-Notebook-PC:/home/aaron# cat /var/log/syslog | grep etwork | tail -n25
Aug  7 17:00:43 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): carrier now ON (device state 7)
Aug  7 17:00:44 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Aug  7 17:00:45 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): carrier now ON (device state 7)
Aug  7 17:00:46 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Aug  7 17:00:48 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): carrier now ON (device state 7)
Aug  7 17:00:49 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Aug  7 17:00:53 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): carrier now ON (device state 7)
Aug  7 17:00:54 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Aug  7 17:00:58 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): carrier now ON (device state 7)
Aug  7 17:00:58 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): device state change: 7 -> 3 (reason 39)
Aug  7 17:00:58 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): deactivating device (reason: 39).
Aug  7 17:00:58 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2360
Aug  7 17:00:59 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): carrier now OFF (device state 3)
Aug  7 17:00:59 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): device state change: 3 -> 2 (reason 40)
Aug  7 17:00:59 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): deactivating device (reason: 40).
Aug  7 17:01:03 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): carrier now ON (device state 2)
Aug  7 17:01:03 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Aug  7 17:01:04 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): carrier now OFF (device state 3)
Aug  7 17:01:04 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): device state change: 3 -> 2 (reason 40)
Aug  7 17:01:04 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): deactivating device (reason: 40).
Aug  7 17:01:06 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): carrier now ON (device state 2)
Aug  7 17:01:06 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Aug  7 17:01:07 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): carrier now OFF (device state 3)
Aug  7 17:01:07 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): device state change: 3 -> 2 (reason 40)
Aug  7 17:01:07 aaron-HP-Pavilion-dv6-Notebook-PC NetworkManager[714]: <info> (eth0): deactivating device (reason: 40).
```

ifconfig has changed:```

root@aaron-HP-Pavilion-dv6-Notebook-PC:/home/aaron# ifconfig
eth0      Link encap:Ethernet  HWaddr 98:4b:e1:a8:74:63  
          inet6 addr: fe80::9a4b:e1ff:fea8:7463/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:16760 (16.7 KB)
          Interrupt:41 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24208 (24.2 KB)  TX bytes:24208 (24.2 KB)

wlan0     Link encap:Ethernet  HWaddr 90:00:4e:22:a9:e9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

showing new driver:
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 144a
    Flags: bus master, fast devsel, latency 0, IRQ 41
    I/O ports at 2000 [size=256]
    Memory at c1404000 (64-bit, prefetchable) [size=4K]
    Memory at c1400000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at c1410000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Count=4 Masked-
    Capabilities: [cc] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: r8168
    Kernel modules: r8168
```


On the plus side I'm learning lots

---

### Post by chili555 on 2011-08-08
Let's see:```
dmesg | grep r816
```Thanks.

---

### Post by peatbog on 2011-08-08
```
aaron@aaron-HP-Pavilion-dv6-Notebook-PC:~$ dmesg | grep r816
[    2.397320] r8168 Gigabit Ethernet driver 8.024.00-NAPI loaded
[    2.397350] r8168 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.397377] r8168 0000:03:00.0: setting latency timer to 64
[    2.397453] r8168 0000:03:00.0: irq 41 for MSI/MSI-X
[    2.465060] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[    2.465065] r8168  Copyright (C) 2011  Realtek NIC software team <nicfae@realtek.com> 
[   19.541889] r8168: eth0: link down
```Thanks

---

### Post by lkjoel on 2011-08-09
> 
...
[   19.541889] r8168: eth0: link down

That doesn't look good to me.

---

### Post by fdrake on 2011-08-09
```
sudo ifconfig eth0 up
```?

edit:  oh , wait..nevermind, i just saw now your ifconfig output,... ehhhmmmm........

---

### Post by peatbog on 2011-08-09
ha ha oh man these things cook my noodle! 

I read this thread [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

briefly it says shut down > power down > connect ethernet cable > power on > boot ubuntu > wired connection magically works ta da!

quick digression ~ I've also have been having what i believe is a graphics issue where upon booting I get a black screen - I can Ctrl Alf F1,F2 etc into terminal screens but graphics is pooped - I was initially concerned with getting wired connection fixed first because all fixes for the graphics thing seem to need it. 

Anyway turns out I keep getting blank screen when ethernet physically connected - but take it out > boot > plug in ethernet > and the promised ta da materializes before my very eyes!

I didn't think those two things could be related but anecdotal evidence suggests otherwise

any more of this kind of luck and i'll have to change my user id to [I]winning

[/I]thanks for your help

---

### Post by chili555 on 2011-08-09
> and the promised ta da materializes before my very eyes!
??Meaning that the ethernet works and connects? I don't know whether to be glad or stunned!

---

### Post by peatbog on 2011-08-10
Yep. Ethernet works.

 > I don't know whether to be glad or stunned! 	

may I suggest bewildered? Especially as we learn that the old driver r8169 running it. Many power off's > > reboots and attempted starts through grub must have somehow changed it back. 

Perhaps the first thing that people with the wired connection problem could try is shut down> power off>  wait about 15 seconds > power on and boot ubuntu. there's and explanation of why (and more ideas) here => [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

anyway graphics problem is sorted courtesy of information on another thread

cheers for your help Chilli

i'm off to change my user id to something less defeatist

---

