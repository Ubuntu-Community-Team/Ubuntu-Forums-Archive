---
title: "Can't connect to wireless internet"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by Aaron2694 on 2009-12-06
Im new to ubuntu and i am able to hardwire connect to the internet. However, when ever i try to connect to my wireless network in my home with my linksys USB Wireless Network Adapter the connection is found but it is very weak and often disconnects completely before i can even load google in the web browser. I dont really know whats going on, could it be that im not connecting the right way or is my USB Wireless Network Adapter just bad?

---

### Post by e-Gee on 2009-12-06
Did you try to go System/Administration/Hardware Drivers to see if you need some driver

---

### Post by Aaron2694 on 2009-12-06
It is a Linksys USB Wireless Network Adapter. Here are the specs.
 
**Model:** WUSB54G 
**Standards:** Draft 802.11n v2.0, 802.11g, 802.11b, 802.3, 802.3u 
**Ports:** Power, Internet, Ethernet 
**Buttons:** Reset, Wi-Fi Protected Setup 
**LEDs:** Ethernet (1-4), Wi-Fi Protected Setup, Wireless, Internet, Power 
**Cabling Type:** CAT 5e 
**# of Antennas:** 3 
**Detachable (Y/N):** No 
**RF Pwr (EIRP) in dBm:** 17 
**UPnP able/cert:** Able 
**Security Features:** Up to 256-Bit Wireless Encryption, SPI Firewall 
**Security Key Bits:** 64, 128, 256

---

### Post by Aaron2694 on 2009-12-06
any help?

---

### Post by coffeecat on 2009-12-06
We need to know the chipset and the driver that the device is using. Open a terminal and post the output of:

```
sudo lshw -C network
```

You can copy and paste the terminal output but the terminal keyboard shortcut for copy is shift-ctrl-C.

---

### Post by Aaron2694 on 2009-12-06
Here is the chipset and driver info:

    *-network               
         description: Ethernet interface 
         product: NetXtreme BCM5782 Gigabit Ethernet 
         vendor: Broadcom Corporation 
         physical id: 2 
         bus info: pci@0000:05:02.0 
         logical name: eth0 
         version: 03 
         serial: 00:0f:20:3a:00:18 
         capacity: 1GB/s 
         width: 64 bits 
         clock: 66MHz 
         capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
         configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=5782-v3.13 latency=64 link=no mingnt=64 multicast=yes port=twisted pair 
         resources: irq:20 memory:fc500000-fc50ffff 
    *-network 
         description: Wireless interface 
         physical id: 1 
         logical name: wlan1 
         serial: 00:06:25:ae:5f:f7 
         capabilities: ethernet physical wireless 
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

---

### Post by northd_tech on 2009-12-06
Hi Aaron.

That's not a WiFi that I've worked with personally, but posting the results of these terminal commands here might help too:

```
lsmod

lsusb

lspci

ifconfig

iwconfig

netstat -v
```

You can enclose those results in CODE ("#" button) or HTML ("<>" button above the post entry area) tags to make them easier to read.

---

### Post by coffeecat on 2009-12-07
> **Aaron2694 said:**
> Here is the chipset and driver info:

    *-network               
         description: Ethernet interface 
         product: NetXtreme BCM5782 Gigabit Ethernet 
         vendor: Broadcom Corporation 
         physical id: 2 
         bus info: pci@0000:05:02.0 
         logical name: eth0 
         version: 03 
         serial: 00:0f:20:3a:00:18 
         capacity: 1GB/s 
         width: 64 bits 
         clock: 66MHz 
         capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
         configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=5782-v3.13 latency=64 link=no mingnt=64 multicast=yes port=twisted pair 
         resources: irq:20 memory:fc500000-fc50ffff 
    *-network 
         description: Wireless interface 
         physical id: 1 
         logical name: wlan1 
         serial: 00:06:25:ae:5f:f7 
         capabilities: ethernet physical wireless 
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

Most of the information for the wireless interface is missing. Are you sure that you pasted everything? Compare the lines under 'Ethernet Interface' with those under 'Wireless Interface'. There should be the same number of lines. The fact that you have a Broadcom ethernet interface doesn't help us. We still don't know what the wireless chipset is.

---

### Post by Aaron2694 on 2009-12-07
Hello,
Yes i am sure that i posted everything the terminal put out. I don't know if there is a driver installed for the device i just assumed that because i could find the network when it was plugged in that the device didnt need me to find a driver for it.

---

### Post by Aaron2694 on 2009-12-07
This is a long post.


Results for lsmod: 
  Module                  Size  Used by 
  nls_iso8859_1           3740  1 
  nls_cp437               5372  1 
  vfat                   10716  1 
  fat                    51452  1 vfat 
  arc4                    1660  2 
  ecb                     2524  2 
  at76_usb               71232  0 
  binfmt_misc             8356  1 
  at76c50x_usb           37640  0 
  mac80211              181076  1 at76c50x_usb 
  snd_intel8x0           30168  2 
  snd_ac97_codec        101216  1 snd_intel8x0 
  ac97_bus                1532  1 snd_ac97_codec 
  snd_pcm_oss            37920  0 
  snd_mixer_oss          16028  1 snd_pcm_oss 
  snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss 
  snd_seq_dummy           2656  0 
  snd_seq_oss            28576  0 
  iptable_filter          3100  0 
  ppdev                   6688  0 
  ip_tables              11692  1 iptable_filter 
  x_tables               16544  1 ip_tables 
  snd_seq_midi            6432  0 
  snd_rawmidi            22208  1 snd_seq_midi 
  cfg80211               93052  1 mac80211 
  parport_pc             31940  1 
  psmouse                56500  0 
  serio_raw               5280  0 
  lp                      8964  0 
  parport                35340  3 ppdev,parport_pc,lp 
  snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi 
  snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
  snd_timer              22276  2 snd_pcm,snd_seq 
  snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
  snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
  soundcore               7264  1 snd 
  snd_page_alloc          9156  2 snd_intel8x0,snd_pcm 
  shpchp                 32272  0 
  fbcon                  36640  72 
  tileblit                2460  1 fbcon 
  font                    8124  1 fbcon 
  bitblit                 5372  1 fbcon 
  softcursor              1756  1 bitblit 
  tg3                   109600  0 
  floppy                 54916  0 
  usb_storage            52576  1 
  i915                  221064  3 
  drm                   159584  3 i915 
  i2c_algo_bit            5760  1 i915 
  intel_agp              27484  2 i915 
  agpgart                34988  2 drm,intel_agp 
  video                  19380  1 i915 
  output                  2780  1 video 
   
  Results for lsusb:
  Bus 001 Device 004: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/2/4GB Flash Drive 
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
  Bus 003 Device 003: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter 
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
   
  Results for lspci:
  00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02) 
  00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) 
  00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02) 
  00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) 
  00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) 
  00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) 
  00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) 
  00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) 
  00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02) 
  00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) 
  00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02) 
  00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02) 
  05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03) 
   
  Results for ifconfig:
  wlan1     Link encap:Ethernet  HWaddr 00:06:25:ae:5f:f7  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1 
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
   
  Results for iwconfig:
  wlan1     IEEE 802.11b  ESSID:"Dynex"  
            Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
            Tx-Power=20 dBm   
            Retry  long limit:7   RTS thr:off   Fragment thr:off 
            Power Management:off 
            Link Quality:0  Signal level:0  Noise level:0 
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
   
  Results for netstat -V:
  net-tools 1.60 
  netstat 1.42 (2001-04-15) 
  Fred Baumgarten, Alan Cox, Bernd Eckenfels, Phil Blundell, Tuan Hoang and others 
  +NEW_ADDRT +RTF_IRTT +RTF_REJECT +FW_MASQUERADE +I18N 
  AF: (inet) +UNIX +INET +INET6 +IPX +AX25 +NETROM +X25 +ATALK +ECONET +ROSE 
  HW:  +ETHER +ARC +SLIP +PPP +TUNNEL +TR +AX25 +NETROM +X25 +FR +ROSE +ASH +SIT +FDDI +HIPPI +HDLC/LAPB +EUI64

---

### Post by Aaron2694 on 2009-12-07
Bump

---

### Post by uncaspi on 2009-12-07
Type lshw -C network and please post it:p

---

### Post by coffeecat on 2009-12-08
> **uncaspi said:**
> Type lshw -C network and please post it:p

The OP already has! :wink:

> **Aaron2694 said:**
>  
  Bus 003 Device 003: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter 

That line identifies your wireless device, and a google reveals the ID number 077b:2219 to be an Atmel wireless chipset. I'm not familiar with that device, but googling also brought up this page:

[http://wiki.debian.org/at76_usb](http://wiki.debian.org/at76_usb)

It's for Debian, but this is the important bit:

> Non-free firmware is required for both drivers, which can be provided by installing the atmel-firmware package. It's an old story I'm afraid. The firmware can't be included in a default install because of licensing restrictions - I should imagine. So - go to Synaptic and mark the package 'atmel-firmware' for installation. Don't download it from any of the links in that page. While you're in Synaptic make sure that the package 'wireless-tools' is also installed. Reboot and hopefully the device will be detected and the firmware and driver will be loaded automatically.

I see that the Linksys is a B device and according to that link, it won't support WPA with the Linux driver. If you are relying on WEP you might want to consider getting a replacement 'G' USB wireless dongle anyway. WEP is barely better than no encryption at all. Something to think about.

---

### Post by Aaron2694 on 2009-12-08
Ok, thank you for all of your help. Hopefully after I download and install those packages I can finally connect wirelessly.

---

