---
title: "Cannot get online 12.04 Acer Aspire 5534"
date: 2012-07-30
forum: Networking &amp; Wireless
---

### Post by henry cow on 2012-07-30
Here we go again. 2 years ago I wasted dozens of hours trying to get my Acer Aspire 5534 to connect under Lucid. Eventually, I succeeded, after trying way too many experiments suggested here.

So, I upgraded to 12.04 (which worked, although it took all afternoon) but after the reboot into the new OS, I cannot make any connection.

Having the Aetheros internal wireless card dead did not really surprise me, but when I carried it in and actually plugged it into the Ethernet, still nothing.

WTF?

What is the trick to making it connect to a DSL home network? My desktop did not have this problem when I installed 12.04 on it a couple of months ago (although that was a clean install, not an update).

The connections are good because I unplugged a working connection from my wife's desktop to use. And yes, I have rebooted multiple times.

What next?

Thanks

= = = = =
Mörgæs 2013-12-05:
Using Lubuntu 13.10 everything works in first attempt.

---

### Post by mörgæs on 2012-07-30
Do you get internet access (wired) in a live boot of 12.04?

---

### Post by Kirk Schnable on 2012-07-30
Could you please supply the output of:

```
lshw -C network
```

Thanks,
Kirk

---

### Post by wildmanne39 on 2012-07-30
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by henry cow on 2012-07-31
I shut everything down overnight, and reconnected it all this morning. 

Ethernet worked properly right away, so I can get online.

*      *      *      *      *

Wild Man, thanks for your reply. Here is the result.

harry@hubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux hubuntu 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
harry@hubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Foxconn International, Inc. T77H047.31 802.11bgn Wireless Half-size Mini PCIe Card [AR9283] [105b:e01f]
    Kernel modules: ath9k
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:031e]
    Kernel driver in use: r8169
harry@hubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

harry@hubuntu:~$ rfkill list all
harry@hubuntu:~$ lsmod
Module                  Size  Used by
dm_crypt               23125  0 
joydev                 17693  0 
sparse_keymap          13890  0 
snd_hda_codec_realtek   223962  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
xt_hl                  12521  6 
ip6t_rt                12558  3 
snd_seq_midi_event     14899  1 snd_seq_midi
nf_conntrack_ipv6      13906  6 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ipt_REJECT             12576  1 
ipt_LOG                12919  5 harry@hubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux hubuntu 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
harry@hubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Foxconn International, Inc. T77H047.31 802.11bgn Wireless Half-size Mini PCIe Card [AR9283] [105b:e01f]
    Kernel modules: ath9k
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:031e]
    Kernel driver in use: r8169
harry@hubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

harry@hubuntu:~$ rfkill list all
harry@hubuntu:~$ lsmod
Module                  Size  Used by
dm_crypt               23125  0 
joydev                 17693  0 
sparse_keymap          13890  0 
snd_hda_codec_realtek   223962  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
xt_hl                  12521  6 
ip6t_rt                12558  3 
snd_seq_midi_event     14899  1 snd_seq_midi
nf_conntrack_ipv6      13906  6 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87692  0 
serio_raw              13211  0 
xt_limit               12711  7 
fglrx                3263886  54 
xt_tcpudp              12603  18 
edac_core              53746  0 
k8temp                 13057  0 
soundcore              15091  1 snd
sp5100_tco             13791  0 
edac_mce_amd           23709  0 
i2c_piix4              13301  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
xt_addrtype            12713  4 
xt_state               12578  13 
ip6table_filter        12815  1 
ip6_tables             27864  2 ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
nf_nat                 25891  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
ip_tables              27473  1 iptable_filter
x_tables               29846  12 xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
shpchp                 37277  0 
bnep                   18281  2 
rfcomm                 47604  0 
parport_pc             32866  0 
bluetooth             180104  10 bnep,rfcomm
ppdev                  17113  0 
binfmt_misc            17540  1 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13844  1 
pata_atiixp            13204  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0 
video                  19596  0 
wmi                    19256  0 

snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87692  0 
serio_raw              13211  0 
xt_limit               12711  7 
fglrx                3263886  54 
xt_tcpudp              12603  18 
edac_core              53746  0 
k8temp                 13057  0 
soundcore              15091  1 snd
sp5100_tco             13791  0 
edac_mce_amd           23709  0 
i2c_piix4              13301  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
xt_addrtype            12713  4 
xt_state               12578  13 
ip6table_filter        12815  1 
ip6_tables             27864  2 ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
nf_nat                 25891  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
ip_tables              27473  1 iptable_filter
x_tables               29846  12 xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
shpchp                 37277  0 
bnep                   18281  2 
rfcomm                 47604  0 
parport_pc             32866  0 
bluetooth             180104  10 bnep,rfcomm
ppdev                  17113  0 
binfmt_misc            17540  1 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13844  1 
pata_atiixp            13204  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0 
video                  19596  0 
wmi                    19256  0 

*      *      *      *      *

Kirk, I don't know what to make of "unclaimed'

harry@hubuntu:~$ sudo lshw -C network
[sudo] password for harry: 
  *-network UNCLAIMED     
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: memory:f1100000-f110ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:51:d6:00
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=10.0.0.7 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f1010000-f1010fff memory:f1000000-f100ffff memory:f1020000-f102ffff
harry@hubuntu:~$ 

Thanks for your help!

---

### Post by wildmanne39 on 2012-07-31
Hi, please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Does it come alive now?
The driver is not loading that is why you have unclaimed.
Thanks

---

### Post by henry cow on 2012-07-31
Thank you very much!

Something happened, because the little light came on (I have an actual switch for the wireless card, seems stupid), but I am not there yet.

I have also updated and rebooted, but still no wireless.

I checked the connection information, it is correct (held over, this was a 10.04-12.04 upgrade).

I do not get the little window in the upper right that says "X networks are available" or that asks me whether I want to connect.

Do I have to force it to search for the network?

Thanks again.

---

### Post by wildmanne39 on 2012-07-31
Hi, let's dig a little deeper, please post the output of:
```
nm-tool
iwconfig
sudo iwlist scan
lsmod | grep ath
```
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
```
by clicking on new reply and click # then paste the information between the brackets.
Thanks

---

### Post by henry cow on 2012-07-31
Thank you.

harry@hubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:26:22:51:D6:00

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             10.0.0.1


harry@hubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

harry@hubuntu:~$ sudo iwlist scan
[sudo] password for harry: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

harry@hubuntu:~$ lsmod | grep ath
harry@hubuntu:~$ 
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
```

---

### Post by wildmanne39 on 2012-07-31
Hi, for some reason the driver is not loading please do:
```
sudo modprobe ath9k
```
Then post the output of those commands again.
Thanks

---

### Post by henry cow on 2012-07-31
```
harry@hubuntu:~$ sudo modprobe ath9k
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
harry@hubuntu:~$ 

```

```
harry@hubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [mok-Wireless] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           no
  HW Address:        0C:60:76:5F:CD:13

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Apple Network ab5753: Infra, 00:1C:B3:AB:57:53, Freq 2412 MHz, Rate 54 Mb/s, Strength 99 WPA2
    SFSD:            Infra, 00:16:B6:17:1D:D7, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA
    smartys:         Infra, C0:C1:C0:0A:C6:68, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    HOME-9E08:       Infra, 78:CD:8E:31:9E:08, Freq 2432 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    DeBetta:         Infra, 58:6D:8F:D4:DD:68, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    linksys:         Infra, 00:18:F8:E3:4E:30, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WEP
    weber54:         Infra, 00:13:46:BF:BB:0E, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    LakeHouse:       Infra, 00:22:3F:0B:C4:14, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WEP
    gators suck:     Infra, 00:18:E7:F0:6D:74, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WEP
    Motorola:        Infra, 00:14:A5:93:49:A2, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    *mok-Wireless:   Infra, 30:46:9A:07:B7:46, Freq 2417 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    Mary Ann home:   Infra, 00:1C:DF:03:E9:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    Honey Run:       Infra, 20:AA:4B:19:19:79, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    smartys-guest:   Infra, C0:C1:C0:0A:C6:6A, Freq 2462 MHz, Rate 54 Mb/s, Strength 29
    GoldsteinHome-guest: Infra, 58:6D:8F:23:F9:78, Freq 2462 MHz, Rate 54 Mb/s, Strength 20
    UGA2012-guest:   Infra, 58:6D:8F:01:E3:23, Freq 2462 MHz, Rate 54 Mb/s, Strength 17
    FBI Monitoring Network: Infra, B8:C7:5D:04:76:3B, Freq 2457 MHz, Rate 54 Mb/s, Strength 20 WPA2
    GoldsteinHome:   Infra, 58:6D:8F:23:F9:76, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    GoldsteinHome_EXT: Infra, A2:21:B7:98:47:A3, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    UGA2012:         Infra, 58:6D:8F:01:E3:21, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    mark-network:    Infra, 00:1C:10:06:12:4F, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WEP

  IPv4 Settings:
    Address:         10.0.0.75
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             10.0.0.1


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:26:22:51:D6:00

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             10.0.0.1


harry@hubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"mok-Wireless"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 30:46:9A:07:B7:46   
          Bit Rate=150 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:53   Missed beacon:0

eth0      no wireless extensions.

harry@hubuntu:~$ sudo iwlist scan
[sudo] password for harry: 

```


```
harry@hubuntu:~$ sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
[sudo] password for harry: 
Jul 31 17:22:54 hubuntu NetworkManager[894]: <info> wpa_supplicant started
Jul 31 17:22:54 hubuntu NetworkManager[894]: <info> (wlan0): supplicant interface state: starting -> ready
Jul 31 17:22:54 hubuntu NetworkManager[894]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul 31 17:22:54 hubuntu NetworkManager[894]: <info> (wlan0): supplicant interface state: ready -> inactive
Jul 31 17:22:56 hubuntu NetworkManager[894]: <info> Activation (wlan0) starting connection 'mok-Wireless'
Jul 31 17:22:56 hubuntu NetworkManager[894]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 31 17:22:56 hubuntu NetworkManager[894]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 31 17:22:56 hubuntu NetworkManager[894]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 31 17:22:56 hubuntu NetworkManager[894]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 31 17:22:56 hubuntu NetworkManager[894]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 31 17:22:56 hubuntu NetworkManager[894]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 31 17:22:56 hubuntu NetworkManager[894]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 31 17:22:56 hubuntu NetworkManager[894]: <info> Activation (wlan0/wireless): connection 'mok-Wireless' has security, and secrets exist.  No new secrets needed.
Jul 31 17:22:56 hubuntu NetworkManager[894]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 31 17:22:56 hubuntu NetworkManager[894]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jul 31 17:22:57 hubuntu wpa_supplicant[2414]: Trying to authenticate with 30:46:9a:07:b7:46 (SSID='mok-Wireless' freq=2417 MHz)
Jul 31 17:22:57 hubuntu NetworkManager[894]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul 31 17:22:57 hubuntu wpa_supplicant[2414]: Trying to associate with 30:46:9a:07:b7:46 (SSID='mok-Wireless' freq=2417 MHz)
Jul 31 17:22:57 hubuntu kernel: [ 1644.077736] wlan0: authenticate with 30:46:9a:07:b7:46 (try 1)
Jul 31 17:22:57 hubuntu kernel: [ 1644.079671] wlan0: authenticated
Jul 31 17:22:57 hubuntu kernel: [ 1644.080392] wlan0: associate with 30:46:9a:07:b7:46 (try 1)
Jul 31 17:22:57 hubuntu NetworkManager[894]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 31 17:22:57 hubuntu kernel: [ 1644.084680] wlan0: RX AssocResp from 30:46:9a:07:b7:46 (capab=0x431 status=0 aid=5)
Jul 31 17:22:57 hubuntu kernel: [ 1644.084691] wlan0: associated
Jul 31 17:22:57 hubuntu kernel: [ 1644.095712] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 31 17:22:57 hubuntu wpa_supplicant[2414]: Associated with 30:46:9a:07:b7:46
Jul 31 17:22:57 hubuntu NetworkManager[894]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jul 31 17:22:57 hubuntu wpa_supplicant[2414]: WPA: Key negotiation completed with 30:46:9a:07:b7:46 [PTK=CCMP GTK=TKIP]
Jul 31 17:22:57 hubuntu wpa_supplicant[2414]: CTRL-EVENT-CONNECTED - Connection to 30:46:9a:07:b7:46 completed (auth) [id=0 id_str=]
Jul 31 17:22:57 hubuntu NetworkManager[894]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jul 31 17:22:57 hubuntu NetworkManager[894]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'mok-Wireless'.
Jul 31 17:22:57 hubuntu NetworkManager[894]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 31 17:22:57 hubuntu NetworkManager[894]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 31 17:22:57 hubuntu NetworkManager[894]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 31 17:22:57 hubuntu NetworkManager[894]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 31 17:22:57 hubuntu NetworkManager[894]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 31 17:22:57 hubuntu NetworkManager[894]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 31 17:22:57 hubuntu dhclient: Listening on LPF/wlan0/0c:60:76:5f:cd:13
Jul 31 17:22:57 hubuntu dhclient: Sending on   LPF/wlan0/0c:60:76:5f:cd:13
Jul 31 17:22:57 hubuntu dhclient: DHCPREQUEST of 10.0.0.75 on wlan0 to 255.255.255.255 port 67
Jul 31 17:22:57 hubuntu NetworkManager[894]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jul 31 17:22:57 hubuntu NetworkManager[894]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul 31 17:22:57 hubuntu NetworkManager[894]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jul 31 17:22:57 hubuntu avahi-daemon[614]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.75.
Jul 31 17:22:57 hubuntu avahi-daemon[614]: New relevant interface wlan0.IPv4 for mDNS.
Jul 31 17:22:57 hubuntu avahi-daemon[614]: Registering new address record for 10.0.0.75 on wlan0.IPv4.
Jul 31 17:22:58 hubuntu NetworkManager[894]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jul 31 17:22:58 hubuntu NetworkManager[894]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jul 31 17:22:58 hubuntu NetworkManager[894]: <info> Activation (wlan0) successful, device activated.
Jul 31 17:22:58 hubuntu NetworkManager[894]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jul 31 17:22:59 hubuntu avahi-daemon[614]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::e60:76ff:fe5f:cd13.
Jul 31 17:22:59 hubuntu avahi-daemon[614]: New relevant interface wlan0.IPv6 for mDNS.
Jul 31 17:22:59 hubuntu avahi-daemon[614]: Registering new address record for fe80::e60:76ff:fe5f:cd13 on wlan0.*.
Jul 31 17:23:08 hubuntu kernel: [ 1654.672090] wlan0: no IPv6 routers present
Jul 31 17:23:09 hubuntu wpa_supplicant[2414]: WPA: Group rekeying completed with 30:46:9a:07:b7:46 [GTK=TKIP]
harry@hubuntu:~$ 

```

---

### Post by wildmanne39 on 2012-07-31
Hi, it is showing connected, is it working? if not please go into your router and set encryption to just wpa2 only if you have that option, it is best for linux drivers.

Take the dash - out of your network name and then do:
```
sudo su 
echo ath9k >> /etc/modules 
exit
```
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
#!/bin/sh

```
/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit, close and reboot.
Thanks

---

### Post by praseodym on 2012-07-31
Uninstall Ndiswrapper completely:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm /etc/modprobe.d/ndiswrapper
sudo rm -r /etc/ndiswrapper/* 
```
For the wired NIC please have a look here ("r8168 mittels dkms"):

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

---

### Post by henry cow on 2012-08-01
Wild Man - Thank You!

Hallelujah!

That last bit did the trick. I knew it was good when the light on the wireless button came on and stayed on after boot up.

It still refused to connect to the wireless network until I unplugged the ethernet cable, but at least it recognized that the wireless network was there.

Do I still need to uninstall ndiswrapper?

Thank you so much, again.

Why is this so difficult? There must be millions of these laptops out there, and they are not that old.

I went through far more pain and wasted time 2 years ago when the laptop and 10.04 were new, I was assuming that whatever the problem had been back then was rectified long ago.

---

### Post by wildmanne39 on 2012-08-01
Hi, no you do not need to remove ndiswrapper I do not believe it is installed.

We see it all the time where one thing gets fixed and another breaks when a new release comes out.

I am glad it is working.
Enjoy

---

