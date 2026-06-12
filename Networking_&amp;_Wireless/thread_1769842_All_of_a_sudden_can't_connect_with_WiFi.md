---
title: "All of a sudden can't connect with WiFi"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by MCBTunes on 2011-05-28
I have Ubuntu 10.04 on my EeePC 1000H. I don't use this computer often but it has always worked before... I suspect an update did this to me. I've recently swapped wireless routers but all my other machines have been able to connect to the new router. 

I can see the SSID and the signal strength is high but when I try to connect to it, it just attempts for a long time then asks me for my password again. 

I see there is another thread similar to this.. because our issues may be different I will avoid hijacking and start this but I will post the output from suggestions there. If anyone has suggestions that would be great.

Edit: I am currently connected to wired network.

```
michael@michaelsEeeUbuntu:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             connected
  Default:           yes
  HW Address:        00:23:54:18:C0:DE

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             disconnected
  Default:           no
  HW Address:        00:22:43:41:C1:8B

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    2WIRE023:        Infra, C0:83:0A:2E:B0:F1, Freq 2462 MHz, Rate 18 Mb/s, Strength 86 WPA WPA2
    2WIRE628:        Infra, 3C:EA:4F:E2:87:31, Freq 2452 MHz, Rate 18 Mb/s, Strength 20 WPA WPA2


michael@michaelsEeeUbuntu:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             connected
  Default:           yes
  HW Address:        00:23:54:18:C0:DE

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             disconnected
  Default:           no
  HW Address:        00:22:43:41:C1:8B

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    2WIRE023:        Infra, C0:83:0A:2E:B0:F1, Freq 2462 MHz, Rate 18 Mb/s, Strength 86 WPA WPA2
    2WIRE628:        Infra, 3C:EA:4F:E2:87:31, Freq 2452 MHz, Rate 18 Mb/s, Strength 20 WPA WPA2

```


```
michael@michaelsEeeUbuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:18:c0:de
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.0.104 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fbfc0000-fbffffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:43:41:c1:8b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:fbef0000-fbefffff
michael@michaelsEeeUbuntu:~$ 


```


```
michael@michaelsEeeUbuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Network controller: RaLink RT2860
03:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
michael@michaelsEeeUbuntu:~$ 

```


```
michael@michaelsEeeUbuntu:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: eeepc-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

```
michael@michaelsEeeUbuntu:~$ lsmod
Module                  Size  Used by
hid_logitech            7388  0 
ff_memless              4093  1 hid_logitech
usbhid                 36110  1 hid_logitech
hid                    67096  2 hid_logitech,usbhid
binfmt_misc             6587  1 
ppdev                   5259  0 
ipt_REJECT              1928  1 
ipt_LOG                 4542  5 
xt_limit                1382  7 
xt_tcpudp               2011  9 
ipt_addrtype            1631  4 
xt_state                1098  7 
rfcomm                 33421  4 
snd_hda_codec_realtek   203408  1 
fbcon                  35102  71 
sco                     7885  2 
tileblit                2031  1 fbcon
snd_hda_intel          22069  2 
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
softcursor              1189  1 bitblit
bridge                 45614  0 
stp                     1655  1 bridge
vga16fb                11385  0 
snd_hwdep               5412  1 snd_hda_codec
ip6table_filter         2343  1 
bnep                    9436  2 
vgastate                8961  1 vga16fb
ip6_tables             11227  1 ip6table_filter
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
nf_nat_irc              1124  0 
snd_seq_oss            26722  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
l2cap                  30624  16 rfcomm,bnep
snd_seq_midi            4557  0 
nf_nat                 15735  2 nf_nat_irc,nf_nat_ftp
i915                  287810  3 
snd_rawmidi            19056  1 snd_seq_midi
nf_conntrack_ipv4      10672  9 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
drm_kms_helper         29329  1 i915
drm                   162345  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nf_conntrack_ftp        5381  1 nf_nat_ftp
snd_timer              19098  2 snd_pcm,snd_seq
video                  17375  1 i915
nf_conntrack           61615  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          2271  1 
joydev                  8740  0 
btusb                  10957  2 
eeepc_laptop           14331  0 
output                  1871  1 video
rt2860sta             481561  1 
ip_tables               9991  1 iptable_filter
uvcvideo               57310  0 
lp                      7028  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54180  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x_tables               14299  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
parport                32635  2 ppdev,lp
soundcore               6620  1 snd
intel_agp              24375  2 i915
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
agpgart                31724  2 drm,intel_agp
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
psmouse                63245  0 
serio_raw               3978  0 
atl1e                  28018  0 

```


```
michael@michaelsEeeUbuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: C0:83:0A:2E:B0:F1   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:-60 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

```
michael@michaelsEeeUbuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 3C:EA:4F:E2:87:31
                    Protocol:802.11b/g
                    ESSID:"2WIRE628"
                    Mode:Managed
                    Channel:9
                    Quality:10/100  Signal level:-86 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: C0:83:0A:2E:B0:F1
                    Protocol:802.11b/g
                    ESSID:"2WIRE023"
                    Mode:Managed
                    Channel:11
                    Quality:76/100  Signal level:-60 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

pan0      Interface doesn't support scanning.


```

---

### Post by MCBTunes on 2011-05-29
bump. Can anyone help? I really have no idea.

---

### Post by maphew on 2011-05-30
i managed to get the wireless to work, sometimes, by using "edit connections" followed by "connect to hidden network". It is very unreliable though, the next time i turn on the computer it very likely is broken again. Once or twice all I needed to do is to switch from dhcp to manual ip and back again, but that is rare.

The most reliable unreliable method, if i may chain those two together, seems to be to set ipv4 to "dhcp, addresses only" and use the dns server ip's written down from one of the successful connections. What follows is the output from one of the rare occasions when the wireless is working. (before upgrading from 10.10 to 11.04 wireless always worked, without fuss. my display doesn't work as well as before either, but that's another thread.)

My laptop is an Acer 3500.
```

matt@laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

matt@laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:93:65:93
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:2000(size=256) memory:e2003000-e2003fff memory:48000000-4801ffff
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 01
       serial: 00:0e:9b:a4:9f:cf
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A ip=123.123.123.123 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:e2010000-e201ffff

matt@laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"myplace"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:29:12:B3:05:BE   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:183   Missed beacon:0

vboxnet0  no wireless extensions.


```

---

### Post by Plumtreed on 2011-05-30
I don't have any answers but I have a similar problem and my solution follows Maphew's 'line-of-attack'.

I often, but not always, have to search in 'Connect to hidden networks' and manually trigger my wireless network choice manually. This doesn't usually connect but if I 'Restart' it will often connect automatically on restart. 

I don't know what the problem is & the work around is awkward and time consuming.

I am running 10.10 which has worked properly until recent upgrades. I have another PC running 10.10 that hasn't been upgraded so dutifully and it continues to work the way it should.

I have been watching and reading these forums in the hope that someone has an answer:(

---

### Post by MCBTunes on 2011-05-31
I think I am going to backup all my data tomorrow (to give this thrad a little longer to potentially save me) and try to reinstall with 11.04 and see what happens. Will report back if I have good news.

---

### Post by RickPJ on 2011-05-31
This sounds like the same problem I'm having with 10.04 on an Eee 901. Yesterday I accepted a kernel upgrade to 2.6.32-32, after which Wifi has been erratic at best. It was connecting to start with, but behaved as if the connection was intermittent - web pages timing out etc. Then it just would not connect at all, always falling back to asking for the Wifi password.

I tried interrupting boot and selecting the previous kernel (2.6.32-31) and that works fine, as it always has in prior versions. So it seems there is a driver update in the -32 kernel that's broken something.

Assuming you keep the previous kernel on your system then this is a solution, at least in the short term.

Rick

---

### Post by Plumtreed on 2011-05-31
Initially, I thought this problem had to do with the Broadcom cards but It appears to happen to other cards too.

I haven't tried selecting an earlier kernel version because my problem is very inconsistent and often works the way it should. Then, for no apparent reason, I will be 'locked-out'. 

Wireless seems to be a general problem in 11.04 and the associated upgrades.

---

### Post by grahammechanical on 2011-05-31
Hi MCBTunes

This is for you. Did you notice that the state of wlan0 is disconnected? Ok, so you already knew that but the question is why? Network Manager tries to connect but fails. Why?

1) It is using the connection information for the previous router to access the new router.

2) You have created an new connection in Network manager but have given it the wrong password. It is not your login password but the wireless key or pass phrase (WPA-PSK) for the new router. which is different from the one the old router used.

3) The new router is set to a different encryption method than is network manager.

These could be reasons for the failure to connect. On the plus side. The driver is installed and it matches the wireless adapter in the machine. The wireless adapter is not soft blocked or hard blocked. In other words it is not switched off by either a software switch or a hardware switch. The two wireless networks that are being detected are set to WPA2 encryption. This also means that the wireless adapter is working. It is detecting wireless networks.

All that is needed now is to get Network Manager to connect to one of them.

Regards.

---

### Post by maphew on 2011-06-18
There are threads all over the place about messed up wifi with 11.04. Some of them are solved but the routes they took don't appply to my machine. The sometimes-works method I posted previously now doesn't work at all. The only way I can use the laptop + internet is to boot from a sysrescue cd, where the wireless "just works".

---

