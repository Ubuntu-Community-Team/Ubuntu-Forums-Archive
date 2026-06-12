---
title: "Connected to wifi, but only ssh access?"
date: 2012-07-28
forum: Networking &amp; Wireless
---

### Post by Aetasdk on 2012-07-28
Im running Ubuntu 12.04 which is connected to a wifi network with wpa2 encryption. I cannot access the system in any other way than by ssh. Before the update from 11.10 I could access the system using both windows and mac. Im running Samba shares and unix shares on the system and they show in Finder, but I no longer have access to them. I get this messeage when trying "*The server may not exist or it is unavailable at this time. Check the server name or IP address, check your network connection, and then try again.*" 
It think there might be a problem with the ip address, so I have tried to force a static IP on the system. I have search google and several forums...
I hope you can help me. 
Thank you in advance.
/Phil

Here are some details:

iwconfig
> lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Tomato"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 20:4E:7F:10:18:54   
          Bit Rate=108 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:100   Missed beacon:0

eth0      no wireless extensions.

rfkill list all
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

dmesg | grep wlan0
```
[   84.725769] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   84.729250] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   87.924759] wlan0: authenticate with 20:4e:7f:10:18:54 (try 1)
[   87.926734] wlan0: authenticated
[   87.927411] wlan0: associate with 20:4e:7f:10:18:54 (try 1)
[   87.930782] wlan0: RX AssocResp from 20:4e:7f:10:18:54 (capab=0x411 status=0 aid=3)
[   87.930789] wlan0: associated
[   87.940813] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   98.368037] wlan0: no IPv6 routers present
[ 8796.006343] wlan0: deauthenticated from 20:4e:7f:10:18:54 (Reason: 7)
[ 8797.132419] wlan0: authenticate with 20:4e:7f:10:18:54 (try 1)
[ 8797.135379] wlan0: authenticated
[ 8797.136422] wlan0: associate with 20:4e:7f:10:18:54 (try 1)
[ 8797.140288] wlan0: RX ReassocResp from 20:4e:7f:10:18:54 (capab=0x411 status=0 aid=1)
[ 8797.140298] wlan0: associated
```

/etc/modprobe.d$ lsmod
```
Module                  Size  Used by
iptable_filter         12706  0 
ip_tables              18106  1 iptable_filter
x_tables               21974  2 iptable_filter,ip_tables
appletalk              29192  0 
rfcomm                 38139  6 
bnep                   17830  2 
btusb                  17912  2 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13516  1 
arc4                   12473  2 
ath9k                 117326  0 
eeepc_wmi              12949  0 
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
mac80211              436455  1 ath9k
ath3k                  12825  0 
bluetooth             158438  24 rfcomm,bnep,btusb,ath3k
k10temp                12990  0 
psmouse                72919  0 
serio_raw              13027  0 
ath9k_common           13781  1 ath9k
ath9k_hw              391523  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178679  3 ath9k,mac80211,ath
sp5100_tco             13495  0 
snd_hda_codec_realtek   174055  1 
snd_hda_codec_hdmi     31775  1 
joydev                 17393  0 
i2c_piix4              13093  0 
snd_hda_intel          32765  7 
snd_hda_codec         109562  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
fglrx                2909855  112 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 asus_wmi
snd                    62064  23 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_logitech           22024  0 
ff_memless             12945  1 hid_logitech
usbhid                 41906  1 hid_logitech
hid                    77367  2 hid_logitech,usbhid
r8169                  56321  0 
pata_atiixp            12999  0 
```

lshw -C network
  ```
*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: e0:b9:a5:ad:17:0f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-24-generic-pae firmware=N/A ip=192.168.1.200 latency=0 multicast=yes wireless=IEEE 802.11bgn resources: irq:16 memory:fea00000-fea0ffff
```

lsmod | grep "ath9k"
```
ath9k                 117326  0 
mac80211              436455  1 ath9k
ath9k_common           13781  1 ath9k
ath9k_hw              391523  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178679  3 ath9k,mac80211,ath
blackbox@Blackbox:~$ lspci -nn | grep 'Atheros' 
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
blackbox@Blackbox:~$ dmesg | egrep 'ath|firm'
[    9.834682] ath9k 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.834701] ath9k 0000:03:00.0: setting latency timer to 64
[    9.884483] ath: EEPROM regdomain: 0x60
[    9.884487] ath: EEPROM indicates we should expect a direct regpair map
[    9.884493] ath: Country alpha2 being used: 00
[    9.884497] ath: Regpair used: 0x60
[    9.994556] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    9.995591] Registered led device: ath9k-phy0
```

lsmod | grep ath
```
ath9k                 117326  0 
mac80211              436455  1 ath9k
ath9k_common           13781  1 ath9k
ath9k_hw              391523  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178679  3 ath9k,mac80211,ath
blackbox@Blackbox:~$ dmesg | grep wlan0
[   45.689429] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.693155] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.743038] wlan0: authenticate with 20:4e:7f:10:18:54 (try 1)
[   48.745261] wlan0: authenticated
[   48.776724] wlan0: associate with 20:4e:7f:10:18:54 (try 1)
[   48.780280] wlan0: RX AssocResp from 20:4e:7f:10:18:54 (capab=0x411 status=0 aid=2)
[   48.780290] wlan0: associated
[   48.787054] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

nm-tool

```
NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unmanaged
  Default:           no
  HW Address:        14:DA:E9:6B:B1:74

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Tomato] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        E0:B9:A5:AD:17:0F

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Thomsen:         Infra, F0:7D:68:59:B4:7E, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
    Enghaven:        Infra, 00:1D:4F:A8:1B:3D, Freq 2472 MHz, Rate 54 Mb/s, Strength 64 WPA2
    Pretty Fly For A Wi-fi: Infra, 84:C9:B2:5B:45:52, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Schande:         Infra, 00:11:50:D6:AC:28, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA
    ispind:          Infra, 00:1E:58:0A:FC:EC, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    *Tomato:         Infra, 20:4E:7F:10:18:54, Freq 2452 MHz, Rate 54 Mb/s, Strength 68 WPA2
    MaxHegn:         Infra, C0:C1:C0:DB:09:1F, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    KP:              Infra, 28:37:37:4B:52:9F, Freq 2442 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Sundevedsgade:   Infra, 00:25:68:F5:77:E5, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WEP
    rnUn6DfN:        Infra, 00:24:8C:32:69:F9, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA
    Praeriehund:     Infra, 00:0D:93:EB:90:85, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    Didde:           Infra, 20:4E:7F:7E:2B:68, Freq 2452 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    AnnaogMikkel:    Infra, 1C:AF:F7:25:BE:BC, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WEP
    Bertrams:        Infra, D8:30:62:2E:F3:5F, Freq 2462 MHz, Rate 54 Mb/s, Strength 40

  IPv4 Settings:
    Address:         192.168.1.200
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
```

---

### Post by steeldriver on 2012-07-28
since you can ssh in OK I would think it's more likely a firewall issue - or the smb / nfs services simply not starting on the remote box

---

### Post by Aetasdk on 2012-07-28
The firewall is disabled, and as far as I can tell the smb / nfs services are running. I checked it using Webmin on the remote box.

---

### Post by steeldriver on 2012-07-28
does running smbtree (samba) / showmount -e (nfs) on the local machine show any remote shares?

---

### Post by Aetasdk on 2012-07-28
> **steeldriver said:**
> does running smbtree on the local machine show any remote shares?

No, it doesn't - What does that mean?

---

### Post by steeldriver on 2012-07-28
I don't really know - either the server really isn't reachable or the client conf is incorrect I would guess? 

You could try running smbtree with debugging level turned up - that should give you some information about the local conf and list any remote hosts it's polling e.g.

```
smbtree -d3
```(the levels go up to 10 I think)

---

### Post by bakegoodz on 2012-07-28
Maybe DNS isn't working. Run this ```
cat /etc/resolv.conf
```
and ping the nameservers listed in there.

---

### Post by Aetasdk on 2012-07-28
I think we are getting close. This is what your suggestions print:

smbtree -d3
```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The "only user" option is deprecated
added interface wlan0 ip=fe80::e2b9:a5ff:fead:170f%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.200 bcast=192.168.1.255 netmask=255.255.255.0
Enter blackbox's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.200 ( 192.168.1.200 )
Connecting to host=192.168.1.200
Connecting to 192.168.1.200 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
anonymous failed session setup with NT_STATUS_PIPE_BROKEN
Connecting to host=BLACKBOX
Connecting to 192.168.1.200 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
anonymous failed session setup with NT_STATUS_PIPE_BROKEN
```

cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 8.8.4.4
nameserver 8.8.8.8
nameserver 127.0.0.1
```

ping -c 5 8.8.4.4
```
PING 8.8.4.4 (8.8.4.4) 56(84) bytes of data.

--- 8.8.4.4 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4032ms
```
This also happens for 8.8.8.8

ping -c 5 127.0.0.1
```
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_req=1 ttl=64 time=0.069 ms
64 bytes from 127.0.0.1: icmp_req=2 ttl=64 time=0.070 ms
64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.064 ms
64 bytes from 127.0.0.1: icmp_req=4 ttl=64 time=0.072 ms
64 bytes from 127.0.0.1: icmp_req=5 ttl=64 time=0.066 ms
```

---

### Post by bakegoodz on 2012-07-28
Dude you don't have internet connection on that computer. 8.8.8.8 and 8.8.4.4 are Google's DNS servers and they are up and 127.0.0.1 just loops back to your own computer. Can you ping other computers on your network? If so you have local access, but you can't reach your gateway/router or somthing is wrong with your gateway/router.

---

### Post by Aetasdk on 2012-07-28
I have been digging a little more and found what I have posted below. Now I dont think that Im connected to the gateway, or even get a ip although I have specified a static ip for wlan0 interface. Could this have anything to do with my problem?

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```

ping -c 5 192.168.1.1
```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.200 icmp_seq=1 Destination Host Unreachable
From 192.168.1.200 icmp_seq=2 Destination Host Unreachable
From 192.168.1.200 icmp_seq=3 Destination Host Unreachable
From 192.168.1.200 icmp_seq=4 Destination Host Unreachable
From 192.168.1.200 icmp_seq=5 Destination Host Unreachable
```

arp -a
```
? (192.168.1.1) at <incomplete> on eth0
? (192.168.1.1) at 20:4e:7f:10:18:52 [ether] on wlan0
```


Thank you for your time and help!

---

### Post by Aetasdk on 2012-07-28
> **bakegoodz said:**
> Dude you don't have internet connection on that computer. 8.8.8.8 and 8.8.4.4 are Google's DNS servers and they are up and 127.0.0.1 just loops back to your own computer. Can you ping other computers on your network? If so you have local access, but you can't reach your gateway/router or somthing is wrong with your gateway/router.

I can't ping any devices on the LAN. However Im able to:
```
sudo apt-get update && apt-get upgrade
```
and even install from the commandline...

---

### Post by bakegoodz on 2012-07-28
Give me the output of ```
ifconfig
```

---

### Post by Aetasdk on 2012-07-29
Sure
ifconfig
```
eth0      Link encap:Ethernet  HWaddr f8:3c:45:6f:67:b0
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2409 (2.4 KB)  TX bytes:2409 (2.4 KB)

wlan0     Link encap:Ethernet  HWaddr 83:5f:6a:92:1d:66
          inet addr:192.168.1.125  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e2b9:a5ff:fead:170f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:344 errors:0 dropped:0 overruns:0 frame:0
          TX packets:331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45535 (45.5 KB)  TX bytes:52080 (52.0 KB)
```

---

### Post by Aetasdk on 2012-07-29
I've been digging a bit more and maybe this might be the problem:

ip route
```
default via 192.168.1.1 dev wlan0  proto static 
default via 192.168.1.1 dev eth0  metric 100 
169.254.0.0/16 dev eth0  scope link  metric 1000 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.200 
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.125  metric 2 
```

sudo ip route
```

blackbox@Blackbox:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

Could this be it?

---

### Post by Aetasdk on 2012-07-29
For some reason I think that all my network requests from the system was directed to 192.168.1.200, which is the static ip of my eth0. I disabled the static ip in /etc/network/interfaces and set it to dhcp. And now it works. Is it not possible to have a static ip for both eth0 and wlan0?

Thank you for all your efforts, its been very helpful :)

---

### Post by bakegoodz on 2012-07-29
I think I see what is going on. You have 2 adapters on the same subnet and the dhcp client has the ability to set one adapter to dominate and network has a pathway to the network outside your computer, but when you set it staticly you it trys to force the same subnet and gateway on two adapters then they conflict with each other and is practicly disabled, except maybe some networks services know how to navigate your conflicted configuration. 

So my question is what in the world are you trying to accomplish with both a wired and wireless adapter on the same network/subnet?

---

