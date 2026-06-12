---
title: "I can't connect my wifi since 11.04"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by einvonley on 2011-06-05
Hi, my wifi was working find on 10.10 but since 11.04 it doesn't work.


```
supo@supo-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

supo@supo-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
06:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

supo@supo-laptop:~$ lspci -nn | grep -i net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 16)
06:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

supo@supo-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:13:a9:c6:b0:33
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:d6000000-d6003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 00:1c:26:47:27:8d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:da000000-da00ffff
supo@supo-laptop:~$ lsmod
Module                  Size  Used by
snd_hrtimer            12680  1 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
arc4                   12473  2 
snd_hda_intel          24140  4 
pcmcia                 39671  0 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ath5k                 144412  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  450944  3 
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
snd_seq                51291  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17322  0 
drm_kms_helper         40745  1 i915
snd                    55295  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27230  0 
tifm_7xx1              12898  0 
drm                   180037  4 i915,drm_kms_helper
pcmcia_rsrc            18292  1 yenta_socket
i2c_algo_bit           13184  1 i915
cfg80211              156212  3 ath5k,ath,mac80211
tifm_core              15040  1 tifm_7xx1
sony_laptop            34432  0 
psmouse                73312  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sky2                   49172  0 
btrfs                 527341  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
supo@supo-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
supo@supo-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:a9:c6:b0:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:16 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:404 erreurs:0 :0 overruns:0 frame:0
          TX packets:404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:32944 (32.9 KB) Octets transmis:32944 (32.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:26:47:27:8d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

supo@supo-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

supo@supo-laptop:~$ uname -r -m
2.6.38-8-generic i686
supo@supo-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

supo@supo-laptop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:13:A9:C6:B0:33

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:1C:26:47:27:8D

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


supo@supo-laptop:~$ sudo rfkill list
[sudo] password for supo: 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```Any helps ?
Thanks

---

### Post by TBABill on 2011-06-05
Have you tried using wicd instead of network manager?

---

### Post by einvonley on 2011-06-08
Hi, 
I tried it doesn't help. I remember a few years ago replacing network manager by wicd make my connection work find. But not this time unfortunatly.

Any other idea ?

Ps: sorry for the very late response, i reseted 5 times my password and it couldn't log in... and I realize today it's because at the registration I spelled wrong my pseudo !!!!!!!!!!!

---

### Post by R0ssp on 2011-06-08
I am having the exact same difficulties, I know that the issue is that there were missing internet drivers on my install of 11.04. I know this because the person who gave me the install disk told me so and he also told me which drivers to get but I forgot what they were. Does anyone know which drivers you need and where to get them (I assume off the Ubuntu webpage)? Oh, and this is my first experience with ubuntu/linux so I need simple instructions if possible. Thanks and I hope this helps someone out there.

---

### Post by einvonley on 2011-06-08
Does "madwifi" remind you something ?
I'm not sure but i saw it in some forums, I'm gonna take a look.

---

### Post by einvonley on 2011-06-08
I don't know on the official website it seems that there no modification since mars 2010.

And it look likes I have those drivers.

Any help ?
I thinks I am gonna downgrade to 10.10, it's too annoying.

---

