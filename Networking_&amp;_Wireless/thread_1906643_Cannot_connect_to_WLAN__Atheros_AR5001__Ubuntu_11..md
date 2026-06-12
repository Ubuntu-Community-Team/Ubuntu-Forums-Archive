---
title: "Cannot connect to WLAN / Atheros AR5001 / Ubuntu 11.04"
date: 2012-01-09
forum: Networking &amp; Wireless
---

### Post by laurac1022 on 2012-01-09
Basically my wireless adapter sees the network but fails when obtaining ip address from dhcp.  I am running ubuntu 11.04 64bit on a Toshiba Satellite laptop with an Atheros AR5001 wireless adapter using the ath5k driver.  Currently connected via wired connection.  The wireless will work if I boot from live usb.

Background on the issue:
I installed 11.04 to dual boot with win 7 and immediately after installation i had a wireless connection.  However occasionally when waking from suspend it would fail to connect.  This would happen maybe once every couple days or so.  It would not connect even if I immediately rebooted.  Usually I would just go to a wired connection or just walk away and in a few hours wake it again and it would have no problem connecting.  I searched the internet for a solution and found that some had success switching to WiCD.  I installed wicd and removed network manager.  After that I went from an occasionally broken wireless connection to a wlan catastrophe.  Could never establish a wireless connection with wicd although it could see wlan.  It would always stall trying to obtain ip address regardless if I used static ip or not.  I figured I was better off with network manager so I reinstalled it and removed wicd.  Now I still have no wireless and there is no tray icon as there was previously with network manager.  Searching for network manager in applications yields nothing but it shows it as being installed in the ubuntu software center.  I decided it would be best to seek assistance before I try to "fix" it anymore.

sudo lshw -C network
```
laura@laura-Satellite-A215:~$ sudo lshw -C network
[sudo] password for laura: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:11:8a:2f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.69 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:a000(size=256) memory:f8300000-f8300fff memory:f8a00000-f8a1ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:28:90:eb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-13-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f8200000-f820ffff

```iwconfig
```
laura@laura-Satellite-A215:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.


```sudo iwlist scan
```
laura@laura-Satellite-A215:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: B0:E7:54:57:5F:B1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:off
                    ESSID:"ryan&laura"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c55808ea4f
                    Extra: Last beacon: 330ms ago
                    IE: Unknown: 000A7279616E266C61757261
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C

vboxnet0  Interface doesn't support scanning.


```rfkill list all
```
laura@laura-Satellite-A215:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```lspci -nnk | grep -iA2 net
```
laura@laura-Satellite-A215:~$ lspci -nnk | grep -iA2 net
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Toshiba America Info Systems Device [1179:ff00]
    Kernel driver in use: r8169
--
14:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7128]
    Kernel driver in use: ath5k

```lsmod
```
laura@laura-Satellite-A215:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
uvcvideo               72195  0 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
radeon                982182  3 
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
videodev               82052  1 uvcvideo
arc4                   12529  2 
snd_seq_midi           13324  0 
joydev                 17606  0 
ath5k                 153264  0 
snd_rawmidi            30486  1 snd_seq_midi
v4l2_compat_ioctl32    17078  1 videodev
ath                    23779  1 ath5k
ttm                    76664  1 radeon
drm_kms_helper         42394  1 radeon
drm                   227534  5 radeon,ttm,drm_kms_helper
snd_seq_midi_event     14899  1 snd_seq_midi
i2c_algo_bit           13400  1 radeon
mac80211              296672  1 ath5k
pcmcia                 49166  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
tifm_7xx1              13042  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_core              15654  1 tifm_7xx1
psmouse                73535  0 
edac_core              53845  0 
yenta_socket           27846  0 
pcmcia_rsrc            18372  1 yenta_socket
sparse_keymap          13898  0 
video                  19438  0 
serio_raw              13166  0 
sp5100_tco             13744  0 
edac_mce_amd           23464  0 
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
cfg80211              181865  3 ath5k,ath,mac80211
shpchp                 37297  0 
k8temp                 13016  0 
lp                     17825  0 
i2c_piix4              13303  0 
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                46458  3 parport_pc,ppdev,lp
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
sdhci_pci              13989  0 
ahci                   25951  5 
crc_itu_t              12707  1 firewire_core
sdhci                  27387  1 sdhci_pci
r8169                  48022  0 
libahci                26642  1 ahci
pata_atiixp            13165  0 

```nm-tool
```
laura@laura-Satellite-A215:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1B:38:11:8A:2F

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.69
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:1B:9E:28:90:EB

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ryan&laura:      Infra, B0:E7:54:57:5F:B1, Freq 2437 MHz, Rate 54 Mb/s, Strength 94



```

---

### Post by laurac1022 on 2012-01-11
help....it would be appreciated

---

### Post by laurac1022 on 2012-01-12
anyone?

---

### Post by laurac1022 on 2012-01-12
bump

If there is any additional info I need to provide to get help, please someone let me know.

---

### Post by laurac1022 on 2012-01-13
bump

---

### Post by howefield on 2012-01-14
Thread closed.

Duplicate here :  [http://ubuntuforums.org/showthread.php?t=1908691](http://ubuntuforums.org/showthread.php?t=1908691)

---

