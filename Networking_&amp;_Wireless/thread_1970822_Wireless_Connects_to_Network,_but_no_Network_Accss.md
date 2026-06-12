---
title: "Wireless Connects to Network, but no Network Accss"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by kaivanes on 2012-05-01
I have an old Pentium 4 box running 12.04.  Yesterday I bought a PCI wireless adapter for it (D-Link DWA-552, see below for more details).  I installed it, and the computer recognized it perfectly, it connected, and everything was beautiful.  Then I was an idiot, and tried to share the wireless connection from the card over the computer's Ethernet port (the manual interface file way; before I understood Network Manager) and everything broke.

lspci | grep Network:
```
01:00.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:02.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)
```Currently, the wireless card will successfully connect to my wireless network, and obtain an ip.  It even obtains the correct ip, reserved for it by the router.  I can change the reservation in the router, and the card will pick up the new address, meaning that password/essid/network configuration should be correct. For reference, the network is 2.4GHz 802.11n with a WPA2 Personal password.

The issue is that after connecting, there is absolutely no network connectivity.  Ping to the router fails, ping to local computers fails, and ping to google fails--and by fails I mean 100% packet loss.  Internet browsing also fails, and the computer does not respond to pings from other machines. Yet the router shows the computer as having an active lease, and ifconfig shows transmitted data...

The computer can connect to the network fine over Ethernet, when put next to the router. I tried removing the Ethernet card from the computer, and the problem persists.  I then tried reinstalling Network Manager, as well as removing the wireless card, purging Network Manager, and then reinstalling both Network Manager and the wireless card (while the Ethernet card was removed).

This is incredibly frustrating, as the card worked out of the box, and as far as I can tell, I reverted all the changes I made (interfaces file is back to being empty except for lo).  Any help would be greatly appreciated, as I am stumped...

Included below is information that is usually asked for, regarding drivers and configurations; let me know if anything else is needed. Note: all commands run with Ethernet cable unplugged.

**iwconfig:**
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Moonbase"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: C8:CD:72:2F:95:BA   
          Bit Rate=270 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:30   Missed beacon:0

eth0      no wireless extensions.
```**ifconfig:**
```
eth0      Link encap:Ethernet  HWaddr 00:0f:9f:d7:ba:2b  
          inet6 addr: fe80::20f:9fff:fed7:ba2b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:631558 (631.5 KB)  TX bytes:101670 (101.6 KB)
          Interrupt:21 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:670 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99094 (99.0 KB)  TX bytes:99094 (99.0 KB)

wlan0     Link encap:Ethernet  HWaddr 84:c9:b2:42:fd:92  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::86c9:b2ff:fe42:fd92/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45059 (45.0 KB)  TX bytes:32532 (32.5 KB)
```[B]
nm-tool:
[/B]```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [Moonbase] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        84:C9:B2:42:FD:92

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    METR0NT:         Infra, 00:A0:F8:92:0C:85, Freq 2412 MHz, Rate 11 Mb/s, Strength 42 WEP
    *Moonbase:       Infra, C8:CD:72:2F:95:BA, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA2

  IPv4 Settings:
    Address:         192.168.2.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tulip
  State:             unavailable
  Default:           no
  HW Address:        00:0F:9F:D7:BA:2B

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
```[B]
lsch -C network[/B]
```
  *-network:0             
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 11
       serial: 00:0f:9f:d7:ba:2b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 maxlatency=128 mingnt=64 multicast=yes
       resources: irq:21 ioport:d400(size=256) memory:ff8efc00-ff8effff memory:ff8a0000-ff8bffff
  *-network:1
       description: Wireless interface
       product: AR922X Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: wlan0
       version: 01
       serial: 84:c9:b2:42:fd:92
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-24-generic firmware=N/A ip=192.168.2.3 latency=168 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:ff890000-ff89ffff

```[B]lsmod:
[/B]```
Module                  Size  Used by
ipt_MASQUERADE         12663  1 
iptable_nat            13016  1 
nf_nat                 24959  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19084  3 iptable_nat,nf_nat
nf_conntrack           73847  4 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18106  1 iptable_nat
x_tables               21974  3 ipt_MASQUERADE,iptable_nat,ip_tables
rmd160                 16664  0 
crypto_null            12782  0 
camellia               29212  0 
lzo                    12525  0 
cast6                  16773  0 
cast5                  24976  0 
deflate                12545  0 
zlib_deflate           26622  1 deflate
cts                    12816  0 
ctr                    13033  0 
gcm                    18768  0 
ccm                    17596  0 
serpent                29029  0 
blowfish_generic       12474  0 
blowfish_common        16635  1 blowfish_generic
twofish_generic        16579  0 
twofish_i586           12755  0 
twofish_common         20823  2 twofish_generic,twofish_i586
xcbc                   12711  0 
sha512_generic         16780  0 
des_generic            21191  0 
geode_aes              13228  0 
cryptd                 19821  0 
aes_i586               16956  2 
xfrm_user              31159  0 
ah6                    12793  0 
ah4                    12707  0 
esp6                   12811  0 
esp4                   12806  0 
xfrm4_mode_beet        12497  0 
xfrm4_tunnel           12675  0 
tunnel4                13045  1 xfrm4_tunnel
xfrm4_mode_tunnel      12546  0 
xfrm4_mode_transport    12517  0 
xfrm6_mode_transport    12517  0 
xfrm6_mode_ro          12458  0 
xfrm6_mode_beet        12536  0 
xfrm6_mode_tunnel      12546  0 
ipcomp                 12593  0 
ipcomp6                12596  0 
xfrm_ipcomp            13282  2 ipcomp,ipcomp6
xfrm6_tunnel           13522  1 ipcomp6
tunnel6                13016  1 xfrm6_tunnel
af_key                 31531  0 
dm_crypt               22528  0 
snd_intel8x0           33455  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
arc4                   12473  2 
rfcomm                 38139  4 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
ath9k                 117425  0 
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              436455  1 ath9k
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13781  1 ath9k
snd_timer              28931  2 snd_pcm,snd_seq
ath9k_hw              391523  2 ath9k,ath9k_common
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
psmouse                87213  0 
cfg80211              178679  3 ath9k,mac80211,ath
snd                    62064  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32325  0 
binfmt_misc            17292  1 
parport_pc             32114  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
radeon                729591  2 
i915                  414568  0 
ttm                    65344  1 radeon
tulip                  52487  0 
drm_kms_helper         45466  2 radeon,i915
drm                   197692  5 radeon,ttm,i915,drm_kms_helper
floppy                 60310  0 
i2c_algo_bit           13199  2 radeon,i915
video                  19068  1 i915

```**cat /etc/network/interfaces**
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo

iface lo inet loopback
```

Edit: massive face-palm for misspelling the thread title... Sorry.

---

