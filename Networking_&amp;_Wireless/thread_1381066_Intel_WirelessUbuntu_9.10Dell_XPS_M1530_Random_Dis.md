---
title: "Intel Wireless/Ubuntu 9.10/Dell XPS M1530/ Random Disconnects Help"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by Oprych on 2010-01-14
Hi guys, 

I installed The latest version of Ubuntu over the weekend and I was having a little problem I wondered someone out there may be able to help me with.

When logging into Ubuntu sometimes my wireless card won't be active, the wireless light on my computer will be off as well. The thing is that this seems to be totally random. I had a look around but can't seem to find a fix.

Anyway, I'll list my system info below as the other post states:

Dell XPS M1530 Laptop

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:c3:dd:a0  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fec3:dda0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2809 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2627013 (2.6 MB)  TX bytes:504901 (504.9 KB)

wlan0     IEEE 802.11abg  ESSID:"BeBox"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:17:31:CC:ED   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Module                  Size  Used by
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
hidp                   14268  1 
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
joydev                 10240  0 
arc4                    1660  2 
ecb                     2524  2 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
iwl3945                77372  0 
iwlcore               112796  1 iwl3945
mac80211              181140  2 iwl3945,iwlcore
snd_hda_codec_idt      59844  1 
dell_wmi                2564  0 
btusb                  11856  4 
ricoh_mmc               3676  0 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
psmouse                56500  0 
serio_raw               5280  0 
cfg80211               93052  3 iwl3945,iwlcore,mac80211
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
led_class               4096  3 iwl3945,iwlcore,sdhci
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                      8964  0 
parport                35340  2 ppdev,lp
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
nvidia               9586440  38 
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
usbhid                 38208  0 
usb_storage            52576  1 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
sky2                   46528  0 
intel_agp              27484  0 
agpgart                34988  2 nvidia,intel_agp

 *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:c3:dd:a0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.71 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:f1eff000-f1efffff

wlan0     Scan completed :
          Cell 01 - Address: 00:24:17:31:CC:ED
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"BeBox"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000015e57818b
                    Extra: Last beacon: 61580ms ago
                    IE: Unknown: 00054265426F78
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180202F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

Description:    Ubuntu 9.10

2.6.31-17-generic i686

* Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 2179
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1c:bf:c3:dd:a0
Sending on   LPF/wlan0/00:1c:bf:c3:dd:a0
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.254 port 67
avahi-daemon start/running, process 2935
WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.



I know thats a lot of info, but hopefully someone will be able to help.

Cheers!

---

### Post by Oprych on 2010-01-14
Bump

---

### Post by Oprych on 2010-01-15
And Again.

---

### Post by levis501 on 2010-01-20
Hi Oprych,
  I also have an XPS M1530, albeit with different wireless hardware than your configuration (mine came with Broadcom 4328, not the 3945 like you have).

  I have had some issues with resuming networking from standby, and have only resolved it by bringing down/up the interface with ifconfig.

Levis501

---

### Post by zaphod777 on 2010-01-29
I also have this issue with a xps 1530 same network card. It appears to happen more often when downloading torrents.

However I have done some digging and it looks like what we may need to do is install 9.04 and then do a upgrade to 9.10.

look a the bottom of this bug report
[https://bugs.launchpad.net/dell/+bug/190664](https://bugs.launchpad.net/dell/+bug/190664)

and here:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1999615.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1999615.html)

I have an extra HDD so I think I will give it a try and see how it goes.

---

### Post by ger_ac on 2010-01-31
There's no need to do a fresh install or change boot options. Just do the following...

```
sudo apt-get install wicd
```

WICD is by far better than GNOME network manager. I have a m1530 and all the wireless problems are gone. The only drawback is that you cannot set up a VPN connection but you can use Kvpnc and problem solved :D

---

### Post by zaphod777 on 2010-01-31
How about when downloading a ton of torrents? 

I ran WICD for a while but still had the issue although less frequently. I am now testing 10.04 hoping to find a fix before the new release to help all of the others with this problem. 

Setting the BSSID seams to have helped a bit. But not totally.

---

### Post by zaphod777 on 2010-02-06
Well after trying basicly everything even 10.4 beta. I Re-installed 9.04 then upgraded to 9.10 and it seams to work perfect. There seams to be some issue with the current drivers.

---

### Post by Megaptera on 2010-02-06
Glad you solved it.
There may be this option too for other, works with _buntu 9.10 on Dell Inspiron 1545

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by zaphod777 on 2010-02-06
Thanks yeah I checked that but I have an intel card.

---

### Post by ger_ac on 2010-02-08
> **zaphod777 said:**
> How about when downloading a ton of torrents? 

I ran WICD for a while but still had the issue although less frequently. I am now testing 10.04 hoping to find a fix before the new release to help all of the others with this problem. 

Setting the BSSID seams to have helped a bit. But not totally.

You're right! There's still the problem but it is less random...

---

### Post by zaphod777 on 2010-02-09
I was able to resolve it completely by installing 9.04 and upgrading to 9.10.

If you get a chance please comment on this bug. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429035](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429035)

---

### Post by ger_ac on 2010-02-12
> **zaphod777 said:**
> I was able to resolve it completely by installing 9.04 and upgrading to 9.10.

If you get a chance please comment on this bug. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429035](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429035)

Hi there!

I tried installing 9.04 (fresh one) and my wireless was completely dead, so I tried again 9.10.

I have not had any problem at all so far... everything seems to be working just fine. But the difference among my previous attempts was that I did not install the "startupmanager" (quite handy tool) and no problem at all?

I reckon I so in the related bug that people were even thinking problems were coming from the new grub2. So, I'm wondering if any of you has installed the startupmanager on 9.10 and experience the problem described. If that's true, I shall post on the bug topic...

Cheers :popcorn:

---

