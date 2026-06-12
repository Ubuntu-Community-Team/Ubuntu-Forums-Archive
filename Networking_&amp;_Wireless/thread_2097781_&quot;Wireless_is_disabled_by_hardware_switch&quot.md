---
title: "&quot;Wireless is disabled by hardware switch&quot;"
date: 2012-12-24
forum: Networking &amp; Wireless
---

### Post by RaineShadow on 2012-12-24
I've been struggling with this and as I fix one thing another thing pops up. I'm not sure what to do and would really love some help. Thanks in advance.

I've heard to type in these codes and this is what it gives with each.

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
```

```
uname -a
Linux giselle-HP-Pavilion-ze2000-EC196UA-ABA 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 athlon i386 GNU/Linux
```

```
dmesg | grep -ie firm
[    0.076004] [Firmware Warn]: MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
[   26.138604] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   26.138611] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   26.138616] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  978.973278] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  978.973285] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  978.973290] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

```
lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:3091]
	Kernel driver in use: 8139too
--
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1355]
	Kernel driver in use: b43-pci-bridge

```

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
lsmod
Module                  Size  Used by
snd_atiixp_modem       18604  5
snd_via82xx_modem      18377  0
snd_intel8x0m          18498  0
joydev                 17393  0
hp_wmi                 13652  0
sparse_keymap          13658  1 hp_wmi
arc4                   12473  2
b43                   342643  0
snd_atiixp             19337  2
snd_seq_midi           13132  0
pcmcia                 39791  0
snd_rawmidi            25424  1 snd_seq_midi
mac80211              436455  1 b43
bnep                   17830  2
rfcomm                 38139  0
snd_ac97_codec        106082  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_atiixp
ac97_bus               12642  1 snd_ac97_codec
bluetooth             158438  8 bnep,rfcomm
parport_pc             32114  0
radeon                737789  3
ppdev                  12849  0
snd_seq_midi_event     14475  1 snd_seq_midi
snd_pcm                80845  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_atiixp,snd_ac97_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_seq,snd_pcm
cfg80211              178679  2 b43,mac80211
yenta_socket           27465  0
psmouse                72919  0
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
k8temp                 12905  0
bcma                   25651  1 b43
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
snd                    62064  22 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_atiixp,snd_rawmidi,snd_ac97_codec,snd_seq,snd_pcm,snd_timer,snd_seq_device
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              13027  0
video                  19068  0
soundcore              14635  1 snd
snd_page_alloc         14108  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_atiixp,snd_pcm
i2c_algo_bit           13199  1 radeon
wmi                    18744  1 hp_wmi
i2c_piix4              13093  0
ati_agp                13242  0
shpchp                 32325  0
mac_hid                13077  0
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
ssb                    50691  1 b43
8139too                23283  0
8139cp                 26759  0
pata_atiixp            12999  2

```

---

### Post by RaineShadow on 2012-12-24
Here is this information also. 

```
giselle@giselle-HP-Pavilion-ze2000-EC196UA-ABA:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:a8:4d:57
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
  *-network:1
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
       resources: irq:20 memory:c0204000-c0205fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:f1:4e:80
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-35-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

giselle@giselle-HP-Pavilion-ze2000-EC196UA-ABA:~$ lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:3091]
	Kernel driver in use: 8139too
--
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1355]
	Kernel driver in use: b43-pci-bridge

giselle@giselle-HP-Pavilion-ze2000-EC196UA-ABA:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

giselle@giselle-HP-Pavilion-ze2000-EC196UA-ABA:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

giselle@giselle-HP-Pavilion-ze2000-EC196UA-ABA:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1
nls_cp437              12751  1
vfat                   17308  1
fat                    55605  1 vfat
uas                    17828  0
usb_storage            39646  1
joydev                 17393  0
hp_wmi                 13652  0
sparse_keymap          13658  1 hp_wmi
arc4                   12473  2
b43                   342669  0
snd_atiixp             19337  2
snd_seq_midi           13132  0
snd_atiixp_modem       18604  5
snd_ac97_codec        110213  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
pcmcia                 39826  0
mac80211              436493  1 b43
snd_rawmidi            25424  1 snd_seq_midi
snd_pcm                80916  5 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
radeon                737926  3
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65344  1 radeon
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         45466  1 radeon
drm                   197641  5 radeon,ttm,drm_kms_helper
psmouse                86520  0
cfg80211              178877  2 b43,mac80211
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13027  0
bcma                   25651  1 b43
yenta_socket           27465  0
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
k8temp                 12905  0
snd                    62218  20 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
rfcomm                 38139  0
i2c_algo_bit           13199  1 radeon
bnep                   17830  2
parport_pc             32114  0
soundcore              14635  1 snd
bluetooth             158479  10 rfcomm,bnep
ppdev                  12849  0
snd_page_alloc         14108  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4              13093  0
video                  19068  0
shpchp                 32325  0
ati_agp                13242  0
mac_hid                13077  0
wmi                    18744  1 hp_wmi
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
8139too                23283  0
pata_atiixp            12999  2
8139cp                 26759  0
ssb                    50691  1 b43

giselle@giselle-HP-Pavilion-ze2000-EC196UA-ABA:~$ sudo cat /var/log/syslog |grep -e b43 -e wl -e firmware -e wlan0 | tail -n35
Dec 24 09:37:49 giselle-HP-Pavilion-ze2000-EC196UA-ABA kernel: [   27.129377] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
Dec 24 09:37:49 giselle-HP-Pavilion-ze2000-EC196UA-ABA kernel: [   27.129685] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 24 09:37:49 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): device state change: unavailable -> unavailable (reason 'none') [20 20 0]
Dec 24 09:37:49 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): bringing up device.
Dec 24 09:37:49 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): deactivating device (reason 'none') [0]
Dec 24 09:37:49 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:05:02.0/ssb0:0/net/wlan0, iface: wlan0)
Dec 24 09:37:49 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:05:02.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 24 09:38:22 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): bringing up device.
Dec 24 09:38:22 giselle-HP-Pavilion-ze2000-EC196UA-ABA kernel: [   59.985288] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
Dec 24 09:38:22 giselle-HP-Pavilion-ze2000-EC196UA-ABA kernel: [   59.985295] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
Dec 24 09:38:22 giselle-HP-Pavilion-ze2000-EC196UA-ABA kernel: [   59.985300] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
Dec 24 09:38:58 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): device state change: unavailable -> unavailable (reason 'none') [20 20 0]
Dec 24 09:38:58 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): bringing up device.
Dec 24 09:38:58 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): deactivating device (reason 'none') [0]
Dec 24 09:39:09 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): bringing up device.
Dec 24 09:39:10 giselle-HP-Pavilion-ze2000-EC196UA-ABA kernel: [  107.454565] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
Dec 24 09:39:10 giselle-HP-Pavilion-ze2000-EC196UA-ABA kernel: [  107.454572] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
Dec 24 09:39:10 giselle-HP-Pavilion-ze2000-EC196UA-ABA kernel: [  107.454578] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
Dec 24 09:39:13 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): device state change: unavailable -> unavailable (reason 'none') [20 20 0]
Dec 24 09:39:13 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): bringing up device.
Dec 24 09:39:13 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): deactivating device (reason 'none') [0]
Dec 24 09:39:14 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): bringing up device.
Dec 24 09:39:15 giselle-HP-Pavilion-ze2000-EC196UA-ABA kernel: [  112.788531] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
Dec 24 09:39:15 giselle-HP-Pavilion-ze2000-EC196UA-ABA kernel: [  112.788542] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
Dec 24 09:39:15 giselle-HP-Pavilion-ze2000-EC196UA-ABA kernel: [  112.788551] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
Dec 24 09:39:22 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): device state change: unavailable -> unavailable (reason 'none') [20 20 0]
Dec 24 09:39:22 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): bringing up device.
Dec 24 09:39:22 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): deactivating device (reason 'none') [0]
Dec 24 09:51:53 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): bringing up device.
Dec 24 09:51:53 giselle-HP-Pavilion-ze2000-EC196UA-ABA kernel: [  871.200491] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
Dec 24 09:51:53 giselle-HP-Pavilion-ze2000-EC196UA-ABA kernel: [  871.200502] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
Dec 24 09:51:53 giselle-HP-Pavilion-ze2000-EC196UA-ABA kernel: [  871.200511] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
Dec 24 09:51:55 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): device state change: unavailable -> unavailable (reason 'none') [20 20 0]
Dec 24 09:51:55 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): bringing up device.
Dec 24 09:51:55 giselle-HP-Pavilion-ze2000-EC196UA-ABA NetworkManager[720]: <info> (wlan0): deactivating device (reason 'none') [0]

```

---

### Post by bkratz on 2012-12-24
Do the responses {missing  firmware} look familiar in post 13 of this thread?  Post 14 gives you the answer.

[http://ubuntuforums.org/showthread.php?t=2094257&page=2&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=2094257&page=2&highlight=BCM4318)

---

### Post by RaineShadow on 2012-12-24
Oh my gosh thank you so much! I've been working on it for like four days now looking up stuff and trying to figure it out. Thanks for pointing me in the right direction :)

---

### Post by bkratz on 2012-12-24
> **RaineShadow said:**
> Oh my gosh thank you so much! I've been working on it for like four days now looking up stuff and trying to figure it out. Thanks for pointing me in the right direction :)



Sure glad you got it going, good work!

---

### Post by RaineShadow on 2012-12-24
Thanks :)

---

