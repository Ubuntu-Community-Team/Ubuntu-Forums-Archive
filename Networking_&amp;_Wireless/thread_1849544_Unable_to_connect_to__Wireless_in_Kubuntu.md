---
title: "Unable to connect to  Wireless in Kubuntu"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by mac4rfree on 2011-09-24
Hi Guys,

I just installed Kubuntu.

I went to Network connections and Wireless Tab. I tried to add a new entry there.

I was able to see my SSID when i clicked on scan. In Wireless Security tab, i selected WEP and Gave the wifi password.

But am not able to connect to Internet.

Can somebody help me as what i am doing wrong..

Cheers!!!!

---

### Post by wildmanne39 on 2011-09-24
Hi, please run these commands in a terminal and post the results here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
```
sudo iwlist scan
```
```
nm-tool
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by mac4rfree on 2011-09-24
Hi please find my details below..
```
cat /etc/lsb-release; uname -a
```
```
 vijay@vijay-RV409-RV509-RV709:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux vijay-RV409-RV509-RV709 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
vijay@vijay-RV409-RV509-RV709:~$ 

```
```
sudo lshw -C network
```
```
   *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: e0:ca:94:3e:e3:cd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:fc500000-fc503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.                                                                                                                                                  
       physical id: 0                                                                                                                                                                           
       bus info: pci@0000:04:00.0                                                                                                                                                               
       logical name: eth0                                                                                                                                                                       
       version: 06
       serial: e8:11:32:73:a2:a1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:3000(size=256) memory:fc900000-fc900fff memory:fca04000-fca07fff

```
```
lspci -nnk | grep -iA2 net
```
```
 02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
        Subsystem: Askey Computer Corp. Device [144f:7179]
        Kernel driver in use: wl
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
        Subsystem: Samsung Electronics Co Ltd Device [144d:c581]
        Kernel driver in use: r8169

```
```
iwconfig
```
```
vijay@vijay-RV409-RV509-RV709:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:159
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```
```
rfkill list all
```
```
vijay@vijay-RV409-RV509-RV709:~$ rfkill list all
0: brcmwl-0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

```
```
lsmod
```
```
Module                  Size  Used by
usbhid                 41704  0 
hid                    77084  1 usbhid
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
rfcomm                 38125  12 
sco                    17779  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
btusb                  18160  1 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211_crypt_tkip    17203  0 
videodev               75143  1 uvcvideo
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
wl                   2642531  0 
psmouse                73312  0 
serio_raw              12990  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
intel_ips              17769  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  450944  8 
ahci                   21591  2 
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
libahci                25548  1 ahci
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
r8169                  42534  0 

```
```
sudo iwlist scan
```
```
vijay@vijay-RV409-RV509-RV709:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: D8:5D:4C:C5:D0:C0
                    ESSID:"ywake"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-15 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:21:91:2B:B4:27
                    ESSID:"Vikram"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-61 dBm  Noise level:-95 dBm
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B00010310470010270EB629B7D336B872200021912BB42710210006442D4C696E6B102300074449522D333030102400074449522D3330301042000830303030303030301054000800060050F2040001101100074449522D33303010080002008E
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:1B:57:BB:80:45
                    ESSID:"naidu"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:2/5  Signal level:-72 dBm  Noise level:-93 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 04 - Address: 00:1E:40:14:D8:8F
                    ESSID:"padhu22"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:2/5  Signal level:-78 dBm  Noise level:-93 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

```
```
nm-tool
```
```
vijay@vijay-RV409-RV509-RV709:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        E0:CA:94:3E:E3:CD

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ywake:           Infra, D8:5D:4C:C5:D0:C0, Freq 2412 MHz, Rate 0 Mb/s, Strength 100 WEP
    naidu:           Infra, 00:1B:57:BB:80:45, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WEP
    padhu22:         Infra, 00:1E:40:14:D8:8F, Freq 2462 MHz, Rate 0 Mb/s, Strength 20 WPA
    Vikram:          Infra, 00:21:91:2B:B4:27, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        E8:11:32:73:A2:A1

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


```

---

### Post by wildmanne39 on 2011-09-24
Hi, set your encryption to wpa2 and note mixed or wep that usually works better, then make sure your speed is set to b,g,n and not just n.
Thank you

---

### Post by mac4rfree on 2011-09-25
Hi, i set it as WPA/WPA2 Personal and gave the password. I even gave the manual ip.

But it is not working. 

> **wildmanne39 said:**
> Hi, set your encryption to wpa2 and note mixed or wep that usually works better, then make sure your speed is set to b,g,n and not just n.
Thank you

---

### Post by mac4rfree on 2011-09-25
Finally got connected.. i gave the manual ip and bingo am able to connect..
 
But now the issue is i am not able to browse even though it is showing as Conneccted...

---

### Post by wildmanne39 on 2011-09-25
Hi, usually wireless works best if you set your encryption to wpa2 only and note mixed no wpa/wpa2 if you have that option and not wep, then make sure your speed is set to b,g,n and not just n.

Please post the results of these commands:
```
dmesg | egrep 'wl|wlan0'
```
Thank you

---

### Post by mac4rfree on 2011-09-25
I have only wep, wpa/wpa2 personal, wpa/wpa2 enterprise option...
But now it says that it is connected.. but i am not able to browse..
below is what you requested.

```
vijay@vijay-RV409-RV509-RV709:~$ dmesg | egrep 'wl|wlan0'
[   12.271677] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.286904] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.286914] wl 0000:02:00.0: setting latency timer to 64
[ 1472.128202] wl 0000:02:00.0: PCI INT A disabled
[ 1474.023457] wl 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1474.023484] wl 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfc500004)
[ 1474.023490] wl 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1474.023499] wl 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[ 1474.024050] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1474.024057] wl 0000:02:00.0: setting latency timer to 64

```

---

### Post by wildmanne39 on 2011-09-25
Hi, when you set up the static ip did you use an address out side the range of what DHCP assigns?

Also try this please.
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
Thank you

---

### Post by mac4rfree on 2011-09-25
Hi Yes, i gave a static ip, given to me by provid er......

I have already tried the command you gave me.. 
I will give a try...

Btw,, i really appreciate your help.. :)

> **wildmanne39 said:**
> Hi, when you set up the static ip did you use an address out side the range of what DHCP assigns?

Also try this please.
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
Thank you

---

### Post by wildmanne39 on 2011-09-25
Hi, your welcome! you might change the channel th your router is using and see if that helps.

Please post the results of these commands:
```
sudo tail -n100 /var/log/syslog
```
```
cat /var/lib/NetworkManager/NetworkManager.state
```
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
```
cat /etc/network/interfaces
```
Thank you

---

### Post by mac4rfree on 2011-09-25
I have posted the results you wanted..

Please post the results of these commands:
```
sudo tail -n100 /var/log/syslog
```
```
vijay@vijay-RV409-RV509-RV709:~$ sudo tail -n100 /var/log/syslog
[sudo] password for vijay: 
Sep 26 00:47:51 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth1): device state change: 3 -> 1 (reason 37)
Sep 26 00:47:51 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth1): cleaning up...
Sep 26 00:47:51 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth1): taking down device.
Sep 26 00:47:51 vijay-RV409-RV509-RV709 avahi-daemon[786]: Interface eth1.IPv6 no longer relevant for mDNS.
Sep 26 00:47:51 vijay-RV409-RV509-RV709 avahi-daemon[786]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::e2ca:94ff:fe3e:e3cd.
Sep 26 00:47:51 vijay-RV409-RV509-RV709 avahi-daemon[786]: Withdrawing address record for fe80::e2ca:94ff:fe3e:e3cd on eth1.
Sep 26 00:47:51 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): now unmanaged
Sep 26 00:47:51 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): device state change: 8 -> 1 (reason 37)
Sep 26 00:47:51 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): deactivating device (reason: 37).
Sep 26 00:47:51 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): canceled DHCP transaction, DHCP client pid 919
Sep 26 00:47:51 vijay-RV409-RV509-RV709 avahi-daemon[786]: Withdrawing address record for 192.168.1.3 on eth0.
Sep 26 00:47:51 vijay-RV409-RV509-RV709 avahi-daemon[786]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.3.
Sep 26 00:47:51 vijay-RV409-RV509-RV709 avahi-daemon[786]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep 26 00:47:51 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): cleaning up...
Sep 26 00:47:51 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): taking down device.
Sep 26 00:47:52 vijay-RV409-RV509-RV709 avahi-daemon[786]: Interface eth0.IPv6 no longer relevant for mDNS.
Sep 26 00:47:52 vijay-RV409-RV509-RV709 avahi-daemon[786]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::ea11:32ff:fe73:a2a1.
Sep 26 00:47:52 vijay-RV409-RV509-RV709 avahi-daemon[786]: Withdrawing address record for fe80::ea11:32ff:fe73:a2a1 on eth0.
Sep 26 00:47:52 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): carrier now OFF (device state 1)
Sep 26 00:47:55 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> enable requested (sleeping: no  enabled: no)
Sep 26 00:47:55 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> waking up and re-enabling...
Sep 26 00:47:55 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> WWAN now enabled by management service
Sep 26 00:47:55 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth1): now managed
Sep 26 00:47:55 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Sep 26 00:47:55 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth1): bringing up device.
Sep 26 00:47:55 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth1): deactivating device (reason: 2).
Sep 26 00:47:55 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Sep 26 00:47:55 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Sep 26 00:47:55 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): now managed
Sep 26 00:47:55 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Sep 26 00:47:55 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): bringing up device.
Sep 26 00:47:55 vijay-RV409-RV509-RV709 kernel: [  344.234411] r8169 0000:04:00.0: eth0: link down
Sep 26 00:47:55 vijay-RV409-RV509-RV709 kernel: [  344.234419] r8169 0000:04:00.0: eth0: link down
Sep 26 00:47:55 vijay-RV409-RV509-RV709 kernel: [  344.234598] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 26 00:47:55 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): preparing device.
Sep 26 00:47:55 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): deactivating device (reason: 2).
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth1): bringing up device.
Sep 26 00:47:57 vijay-RV409-RV509-RV709 kernel: [  345.833901] r8169 0000:04:00.0: eth0: link up
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): carrier now ON (device state 2)                                                                                     
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): device state change: 2 -> 3 (reason 40)                                                                             
Sep 26 00:47:57 vijay-RV409-RV509-RV709 kernel: [  345.854642] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready                                                                                
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) starting connection 'Auto eth0'                                                                           
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> dhclient started with pid 2036
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep 26 00:47:57 vijay-RV409-RV509-RV709 dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Sep 26 00:47:57 vijay-RV409-RV509-RV709 dhclient: Copyright 2004-2010 Internet Systems Consortium.
Sep 26 00:47:57 vijay-RV409-RV509-RV709 dhclient: All rights reserved.
Sep 26 00:47:57 vijay-RV409-RV509-RV709 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep 26 00:47:57 vijay-RV409-RV509-RV709 dhclient: 
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth1): supplicant interface state:  starting -> ready
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth1): device state change: 2 -> 3 (reason 42)
Sep 26 00:47:57 vijay-RV409-RV509-RV709 dhclient: Listening on LPF/eth0/e8:11:32:73:a2:a1
Sep 26 00:47:57 vijay-RV409-RV509-RV709 dhclient: Sending on   LPF/eth0/e8:11:32:73:a2:a1
Sep 26 00:47:57 vijay-RV409-RV509-RV709 dhclient: Sending on   Socket/fallback
Sep 26 00:47:57 vijay-RV409-RV509-RV709 dhclient: DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
Sep 26 00:47:57 vijay-RV409-RV509-RV709 dhclient: DHCPACK of 192.168.1.3 from 192.168.1.1
Sep 26 00:47:57 vijay-RV409-RV509-RV709 dhclient: bound to 192.168.1.3 -- renewal in 97606 seconds.
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info>   address 192.168.1.3
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info>   prefix 24 (255.255.255.0)
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info>   gateway 192.168.1.1
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info>   hostname 'dhcppc1'
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info>   nameserver '192.168.1.1'
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Scheduling stage 5
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Done scheduling stage 5
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep 26 00:47:57 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Sep 26 00:47:57 vijay-RV409-RV509-RV709 avahi-daemon[786]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.3.
Sep 26 00:47:57 vijay-RV409-RV509-RV709 avahi-daemon[786]: New relevant interface eth0.IPv4 for mDNS.
Sep 26 00:47:57 vijay-RV409-RV509-RV709 avahi-daemon[786]: Registering new address record for 192.168.1.3 on eth0.IPv4.
Sep 26 00:47:58 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Sep 26 00:47:58 vijay-RV409-RV509-RV709 avahi-daemon[786]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::ea11:32ff:fe73:a2a1.
Sep 26 00:47:58 vijay-RV409-RV509-RV709 avahi-daemon[786]: New relevant interface eth0.IPv6 for mDNS.
Sep 26 00:47:58 vijay-RV409-RV509-RV709 avahi-daemon[786]: Registering new address record for fe80::ea11:32ff:fe73:a2a1 on eth0.*.
Sep 26 00:47:58 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep 26 00:47:58 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) successful, device activated.
Sep 26 00:47:58 vijay-RV409-RV509-RV709 NetworkManager[833]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Sep 26 00:47:59 vijay-RV409-RV509-RV709 avahi-daemon[786]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::e2ca:94ff:fe3e:e3cd.
Sep 26 00:47:59 vijay-RV409-RV509-RV709 avahi-daemon[786]: New relevant interface eth1.IPv6 for mDNS.
Sep 26 00:47:59 vijay-RV409-RV509-RV709 avahi-daemon[786]: Registering new address record for fe80::e2ca:94ff:fe3e:e3cd on eth1.*.
Sep 26 00:48:07 vijay-RV409-RV509-RV709 kernel: [  355.973418] eth0: no IPv6 routers present
Sep 26 00:48:07 vijay-RV409-RV509-RV709 ntpdate[2076]: adjust time server 91.189.94.4 offset 0.148691 sec
Sep 26 00:48:08 vijay-RV409-RV509-RV709 kernel: [  356.748558] eth1: no IPv6 routers present

```
```
cat /var/lib/NetworkManager/NetworkManager.state
```
```
vijay@vijay-RV409-RV509-RV709:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
```
vijay@vijay-RV409-RV509-RV709:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e8:11:32:73:a2:a1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcm80211)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e0:ca:94:3e:e3:cd", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4727 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e0:ca:94:3e:e3:cd", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```
```
cat /etc/network/interfaces
```
```
vijay@vijay-RV409-RV509-RV709:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

vijay@vijay-RV409-RV509-RV709:~$
```

---

### Post by wildmanne39 on 2011-09-25
Hi, try this please:
```
sudo su
echo "blacklist brcm80211" >> /etc/modprobe.d/blacklist.conf
exit
```
disconnect your wired connection and restart.
Thank you

---

### Post by mac4rfree on 2011-09-25
Still it shows as connected but unable to browse .... but able to do it when i am connected with wired connection

---

### Post by wildmanne39 on 2011-09-25
Hi, You might change your channel to auto or change it manually in your router to like 6 or 11 instead of 1.
Thank you

---

### Post by wildmanne39 on 2011-09-25
Hi, if changing the channel does not help post the results of this command it is a little different then the one I gave you before, but unplug your wired connection first, in the other log it mainly showed the wired connection I am hoping this will show what we need.
```
sudo cat /var/log/syslog | grep etwork | tail -n100
```
Thank you

---

### Post by mac4rfree on 2011-09-26
The issue is resolved....
 
I have changed the manual ip to Automatic,, viola.. it worked.
 
I guess the provider has given a wrong ip... lol
 
Thanks a lot wildmanne39,, for your help.. i have picked up somethings from ur tips.. :)

---

### Post by mac4rfree on 2011-09-26
i installed the fcwcutter to get the drivers for bcm43xx drivers.. 
 
and then the normal configuration fixed the problem...

---

### Post by wildmanne39 on 2011-09-26
Hi, your welcome! I am glad it is working,would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

