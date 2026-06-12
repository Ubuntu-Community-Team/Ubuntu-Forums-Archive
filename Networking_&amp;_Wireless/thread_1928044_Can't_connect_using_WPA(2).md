---
title: "Can't connect using WPA(2)"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by PatrikN78 on 2012-02-19
I have an old HP laptop with built-in Intel 2200BG Wireless. I connect without any problem using no security ("open"). When i switch to WPA it just won't connect and I can't seem to find out why.

I'm using the server-version of Ubuntu 11.10, so only command line is availiable.

Info, when connected to the open network..

lsb_release -d
```

Description:    Ubuntu 11.10

```uname -mr
```

3.0.0-16-generic-pae i686

```sudo /etc/init.d/networking restart
```

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                  RTNETLINK answers: File exists
ssh stop/waiting
ssh start/running, process 1509
[ OK ]

```sudo lshw -C network
```

  *-network:0 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:c6:b2:96
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:3000(size=256) memory:b0106000-b01060ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:cc:ce:bb
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.70 latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:b0107000-b0107fff

```lspci -nnk | grep -iA2 net
```

06:06.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
        Subsystem: Hewlett-Packard Company nc6120/nx8220/nw8240 [103c:12f6]
        Kernel driver in use: ipw2200

```iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"TeliaGateway58-98-35-37-80-65"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 58:98:35:37:80:65
          Bit Rate:36 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/100  Signal level=-63 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:0   Missed beacon:2

```rfkill list all
```

0: hp-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```lsmod
```

Module                  Size  Used by
joydev                 17393  0
hp_wmi                 13652  0
sparse_keymap          13658  1 hp_wmi
pcmcia                 39822  0
i915                  509554  1
snd_intel8x0           33318  0
ipw2200               146179  0
libipw                 46701  1 ipw2200
snd_ac97_codec        106082  1 snd_intel8x0
psmouse                63474  0
ac97_bus               12642  1 snd_ac97_codec
cfg80211              172427  2 ipw2200,libipw
tifm_7xx1              12937  0
drm_kms_helper         32889  1 i915
yenta_socket           27465  0
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              12990  0
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
snd_timer              28932  1 snd_pcm
tifm_core              15040  1 tifm_7xx1
drm                   196290  2 i915,drm_kms_helper
snd                    55902  4 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
lib80211               14570  2 ipw2200,libipw
soundcore              12600  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
binfmt_misc            17292  1
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
wmi                    18744  1 hp_wmi
lp                     17455  0
parport                40930  1 lp
firewire_ohci          35846  0
8139too                23283  0
firewire_core          56937  1 firewire_ohci
8139cp                 26762  0
sdhci_pci              13658  0
sdhci                  27360  1 sdhci_pci
crc_itu_t              12627  1 firewire_core

```sudo cat /var/log/syslog | grep -e ipw
```

Feb 19 15:41:04 owfs kernel: [    8.994268] libipw: 802.11 data/management/control stack, git-1.1.13
Feb 19 15:41:04 owfs kernel: [    8.994273] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Feb 19 15:41:04 owfs kernel: [    9.185350] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Feb 19 15:41:04 owfs kernel: [    9.185354] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Feb 19 15:41:04 owfs kernel: [    9.185478] ipw2200 0000:06:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb 19 15:41:04 owfs kernel: [    9.185508] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Feb 19 15:41:04 owfs kernel: [   11.028787] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
Feb 19 15:41:10 owfs NetworkManager[702]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)

```

---

### Post by praseodym on 2012-02-19
Hi,

maybe the driver (outdated!!! I recommend buying a new card or to use Ubuntu 10.04 with installed "linux-backports-modules-wireless-lucid-generic" in an up-to-date system) doesnt support it (anymore)?! Try the firmware 3.0 from here
[http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)
and unpack it via:
```
sudo tar -xvf ipw2200-fw-3.0 -C /lib/firmware
```

---

### Post by Perkins on 2012-02-21
The various encryption schemes require both the hardware and the drivers to support it.  I don't remember for certain, but I think the 2200BG supports WEP and *maybe* WPA.  I vaguely recall it not supporting WPA2, but it is possible that there are new drivers for it somewhere that will make it work.  Most likely though you would be time and energy ahead to get a newer adapter.  Decent b/g/n USB adapters that work with Linux often come on sale for around $6.

---

### Post by PatrikN78 on 2012-02-21
Thanks for your effort in my issue. The solution was to use the updated driver as mentioned by "praseodym".
WPA2 is now connected :)

As I'm not that familiar with the various commands in Ubuntu I made a mistake when using command provided above to extract the compressed driver. Everything ended up in a sub folder. So.. when I moved my original driver (to backup dir) nothing worked...

---

