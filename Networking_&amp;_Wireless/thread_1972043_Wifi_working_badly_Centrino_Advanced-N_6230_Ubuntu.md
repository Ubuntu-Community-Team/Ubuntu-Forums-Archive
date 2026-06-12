---
title: "Wifi working badly Centrino Advanced-N 6230 Ubuntu 12.04"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by ghuo on 2012-05-03
I've just installed the last version of XUbuntu on my new laptop, a Samsung Serie 5 ultrabook 530U3B.

After a few minutes, the Wifi doesn't work anymore.

I checked the configuration: everything looks ok.

Any ideas?

```
milou@milou-laptop:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

 

milou@milou-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
 Bus 001 Device 003: ID 2232:1018  
Bus 002 Device 003: ID 8086:0189 Intel Corp. 
Bus 003 Device 002: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse



 milou@milou-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0  VGA compatible controller: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller (rev 09)
 00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
 00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
 00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
 00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
 00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
 01:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 (rev 34)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
 03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller



milou@milou-laptop:~$ lspci -nn | grep -i net
01:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [8086:0091] (rev 34)
 02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  06)



milou@milou-laptop:~$ sudo lshw -C network
 [sudo] password for milou: 
  *-network               
       description: Interface réseau sans fil
       produit: Centrino Advanced-N 6230
       fabriquant: Intel Corporation
        identifiant matériel: 0
       information bus: pci@0000:01:00.0
       nom logique: wlan0
       version: 34
       numéro de série: 88:53:2e:92:81:87
       bits: 64 bits
        horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=iwlwifi  driverversion=3.2.0-24-generic firmware=18.168.6.1 ip=192.168.0.6  latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
        ressources: irq:48 mémoire:f0600000-f0601fff
  *-network
       description: Ethernet interface
       produit: RTL8111/8168B PCI Express Gigabit Ethernet controller
       fabriquant: Realtek Semiconductor Co., Ltd.
        identifiant matériel: 0
       information bus: pci@0000:02:00.0
       nom logique: eth0
       version: 06
       numéro de série: e8:03:9a:33:96:eb
       taille: 10Mbit/s
        capacité: 1Gbit/s
       bits: 64 bits
       horloge: 33MHz
        fonctionnalités: pm msi pciexpress msix vpd bus_master cap_list  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12  latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       ressources: irq:46 portE/S:2000(taille=256) mémoire:f0404000-f0404fff mémoire:f0400000-f0403fff
 


milou@milou-laptop:~$ lsmod
Module                  Size  Used by
usbhid                 41906  0 
hid                    77367  1 usbhid
snd_hda_codec_hdmi     31775  1 
 snd_hda_codec_realtek   174055  1 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  16 
bnep                   17830  2 
 joydev                 17393  0 
arc4                   12473  2 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
 snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
 snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
 mac_hid                13077  0 
i915                  414568  2 
iwlwifi               287751  0 
psmouse                87213  0 
mac80211              436455  1 iwlwifi
 btusb                  17912  2 
drm_kms_helper         45466  1 i915
serio_raw              13027  0 
drm                   197692  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
 video                  19068  1 i915
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
mei                    36570  0 
bluetooth             158438  23 rfcomm,bnep,btusb
 snd                    62064  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178679  2 iwlwifi,mac80211
 soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
 


milou@milou-laptop:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"TchouTchou"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: E6:65:B2:D8:F5:B4   
           Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=47/70  Signal level=-63 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:32  Invalid misc:154   Missed beacon:0


eth0      no wireless extensions.

 

milou@milou-laptop:~$ ifconfigeth0      Link encap:Ethernet  HWaddr e8:03:9a:33:96:eb  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
           Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:46 Adresse de base:0xa000 


lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
           adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:81 erreurs:0 :0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 lg file transmission:0 
          Octets reçus:8783 (8.7 KB) Octets transmis:8783 (8.7 KB)


wlan0     Link encap:Ethernet  HWaddr 88:53:2e:92:81:87  
           inet adr:192.168.0.6  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::8a53:2eff:fe92:8187/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           Packets reçus:5102 erreurs:0 :0 overruns:0 frame:0
          TX packets:3768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:6368271 (6.3 MB) Octets transmis:448866 (448.8 KB)
 



milou@milou-laptop:~$ sudo iwlist scan
 lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: E6:65:B2:D8:F5:B4
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                     Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"TchouTchou"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                               18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000126de621140
                     Extra: Last beacon: 68732ms ago
                    IE: Unknown: 000A5463686F755463686F75
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                     IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1607050700000000000000000000000000000000000000
                     IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                     IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3407050700000000000000000000000000000000000000


 eth0      Interface doesn't support scanning.



milou@milou-laptop:~$ uname -r -m
3.2.0-24-generic i686



milou@milou-laptop:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback



milou@milou-laptop:~$ nm-tool


NetworkManager Tool
 

State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
   State:             unavailable
  Default:           no
  HW Address:        E8:03:9A:33:96:EB


  Capabilities:
    Carrier Detect:  yes


   Wired Properties
    Carrier:         off




- Device: wlan0  [TchouTchou] --------------------------------------------------
  Type:              802.11 WiFi
   Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        88:53:2E:92:81:87


  Capabilities:
    Speed:           60 Mb/s
 

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
     Livebox-4110:    Infra, 00:16:CE:7F:48:21, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA
    FreeWifi:        Infra, F4:CA:E5:E9:7E:55, Freq 2442 MHz, Rate 54 Mb/s, Strength 67
    FreeWifi:        Infra, F4:CA:E5:CB:0A:55, Freq 2417 MHz, Rate 54 Mb/s, Strength 69
     *TchouTchou:     Infra, E6:65:B2:D8:F5:B4, Freq 2442 MHz, Rate 54 Mb/s, Strength 58 WEP
    BobikS:          Infra, 00:1F:9F:C2:76:53, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2


   IPv4 Settings:
    Address:         192.168.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254


    DNS:             [212.27.40.241]("tel:212.27.40.241")
     DNS:             [212.27.40.240]("tel:212.27.40.240")



milou@milou-laptop:~$ sudo rfkill list
0: hci0: Bluetooth
    Soft blocked: no
     Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

### Post by chili555 on 2012-05-03
Please try this:```
sudo iwconfig wlan0 power off
```Is it more stable now? If so, we can make it persistent.

---

### Post by ghuo on 2012-05-03
Hi,

It is much better, thank you very much!

Could you please tell me how I can make it persistent?

---

### Post by ghuo on 2012-05-03
Well, I reboot the computer and try again. The wifi is still unstable...

```

fred@globglob-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"TchouTchou"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: E6:65:B2:D8:F5:B4   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:31   Missed beacon:0

```

---

### Post by chili555 on 2012-05-03
You would make it persistent with:```
sudo gedit /etc/rc.local
```Add a line above exit 0```
iw dev wlan0 set power_save off
```Your signal strength is a significant factor, I suspect:> wlan0     IEEE 802.11abg  ESSID:"TchouTchou"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: E6:65:B2:D8:F5:B4   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          [COLOR="Red"]Link Quality=39/70[/COLOR]  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:31   Missed beacon:0Is the signal strength adjustable on the router? Is it better on another channel? I get better signal strength with the router standing on its nose.

---

