---
title: "wireless is not working on clean install of 11.10"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by skn332 on 2011-12-16
Any help would be greatly appreciated.  I've had kubuntu on the computer since 9.x and wireless has always worked.  It was working just fine with 11.04. I did a clean install of the 11.10 and now i have no wireless.  Here is the info

sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:b8:8e:e4:ac
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.10.106 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 memory:d0200000-d0203fff ioport:a000(size=256)
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:22 memory:d0304000-d0305fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:85:18:44
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-13-generic firmware=508.1084 link=no multicast=yes wireless=IEEE 802.11bg


lspci -nnk | grep -iA2 net

03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 10)
        Subsystem: Gateway 2000 Device [107b:0300]
        Kernel driver in use: sky2
--
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
        Subsystem: Gemtek Technology Co., Ltd Device [17f9:0006]
        Kernel driver in use: b43-pci-bridge



iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          



rfkill list all

0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes



lsmod

Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
joydev                 17393  0 
snd_atiixp_modem       18604  5 
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25241  1 snd_seq_midi
pcmcia                 39822  0 
snd_seq_midi_event     14475  1 snd_seq_midi
b43                   318816  0 
snd_atiixp             19337  2 
snd_ac97_codec        106082  2 snd_atiixp_modem,snd_atiixp
ac97_bus               12642  1 snd_ac97_codec
mac80211              393459  1 b43
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80468  5 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1              12937  0 
snd_timer              28932  2 snd_seq,snd_pcm
cfg80211              172392  2 b43,mac80211
tifm_core              15040  1 tifm_7xx1
snd                    55902  20 snd_atiixp_modem,snd_rawmidi,snd_atiixp,snd_ac97_codec,snd_d_pcm,snd_seq_device,snd_timer
psmouse                73673  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              12990  0 
k8temp                 12905  0 
soundcore              12600  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  3 snd_atiixp_modem,snd_atiixp,snd_pcm
i2c_piix4              13093  0 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
radeon                925094  3 
firewire_ohci          35854  0 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192226  5 radeon,ttm,drm_kms_helper
ssb                    50682  1 b43
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
video                  18908  0 
pata_atiixp            12967  6 
sky2                   49317  0 
i2c_algo_bit           13199  1 radeon
ati_agp                13242  0 





sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35

Dec 16 21:53:11 tittyfuck kernel: [ 2997.390837] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 16 21:53:11 tittyfuck NetworkManager[827]: <info> (wlan0): preparing device.
Dec 16 21:53:11 tittyfuck NetworkManager[827]: <info> (wlan0): deactivating device (reason 'none') [0]
Dec 16 21:53:11 tittyfuck kernel: [ 2997.417836] b43-phy0: Radio hardware status changed to DISABLED
Dec 16 21:53:12 tittyfuck wpa_supplicant[8886]: Could not set interface wlan0 flags: Operation not possible due to RF-kill
Dec 16 21:53:12 tittyfuck wpa_supplicant[8886]: Could not set interface 'wlan0' UP
Dec 16 21:53:12 tittyfuck wpa_supplicant[8886]: Could not set interface wlan0 flags: Operation not possible due to RF-kill
Dec 16 21:53:12 tittyfuck NetworkManager[827]: <error> [1324093992.464035] [nm-supplicant-interface.c:570] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
Dec 16 21:53:12 tittyfuck NetworkManager[827]: <info> (wlan0): supplicant interface state: starting -> down
Dec 16 21:53:42 tittyfuck dhclient: Listening on LPF/wlan0/00:14:a5:85:18:44
Dec 16 21:53:42 tittyfuck dhclient: Sending on   LPF/wlan0/00:14:a5:85:18:44
Dec 16 21:55:38 tittyfuck kernel: [    1.990807] b43-pci-bridge 0000:05:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec 16 21:55:38 tittyfuck kernel: [   22.491080] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
Dec 16 21:55:38 tittyfuck kernel: [   22.583490] Registered led device: b43-phy0::tx
Dec 16 21:55:38 tittyfuck kernel: [   22.583536] Registered led device: b43-phy0::rx
Dec 16 21:55:38 tittyfuck kernel: [   22.583585] Registered led device: b43-phy0::radio
Dec 16 21:55:38 tittyfuck NetworkManager[830]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:05:02.0/ssb0:0/net/wlan0, iface: wlan0)
Dec 16 21:55:38 tittyfuck NetworkManager[830]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:05:02.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 16 21:55:38 tittyfuck NetworkManager[830]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 16 21:55:38 tittyfuck NetworkManager[830]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec 16 21:55:38 tittyfuck NetworkManager[830]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Dec 16 21:55:38 tittyfuck NetworkManager[830]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 16 21:55:38 tittyfuck NetworkManager[830]: <info> (wlan0): now managed
Dec 16 21:55:38 tittyfuck NetworkManager[830]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 16 21:55:38 tittyfuck NetworkManager[830]: <info> (wlan0): bringing up device.
Dec 16 21:55:39 tittyfuck kernel: [   26.456087] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
Dec 16 21:55:39 tittyfuck NetworkManager[830]: <info> (wlan0): preparing device.
Dec 16 21:55:39 tittyfuck NetworkManager[830]: <info> (wlan0): deactivating device (reason 'managed') [2]
Dec 16 21:55:39 tittyfuck kernel: [   26.511905] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 16 21:55:39 tittyfuck kernel: [   26.536181] b43-phy0: Radio hardware status changed to DISABLED
Dec 16 21:55:39 tittyfuck wpa_supplicant[989]: Could not set interface wlan0 flags: Operation not possible due to RF-kill
Dec 16 21:55:39 tittyfuck wpa_supplicant[989]: Could not set interface 'wlan0' UP
Dec 16 21:55:39 tittyfuck wpa_supplicant[989]: Could not set interface wlan0 flags: Operation not possible due to RF-kill
Dec 16 21:55:39 tittyfuck NetworkManager[830]: <error> [1324094139.555663] [nm-supplicant-interface.c:570] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
Dec 16 21:55:39 tittyfuck NetworkManager[830]: <info> (wlan0): supplicant interface state: starting -> down



If you need more information please let me know.  I was in a hurry and tried the fix suggested here: [http://ubuntuforums.org/showthread.php?t=1861669](http://ubuntuforums.org/showthread.php?t=1861669) but it didn't work.  Like I said, I was in a hurry and didn't read any of it.  I was hoping for a quick fix :(

Anyway thanks again for your help.

---

### Post by wildmanne39 on 2011-12-17
Hi, your computer is hard blocked which usually means you need to turn your wireless on with the switch or what ever key turns your on like fn f2 for example.
Thank you

---

### Post by digital_k on 2011-12-17
With this version of Kubuntu, if your wireless SSID is not being broadcast it seems to not want to connect. If you haven't enabled SSID broadcast on the router, try doing so and see if that helps.

---

