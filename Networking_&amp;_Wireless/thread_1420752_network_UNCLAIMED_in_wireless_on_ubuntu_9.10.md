---
title: "network UNCLAIMED in wireless on ubuntu 9.10"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by ravindika on 2010-03-03
Can anyone tell me how to find wireless network drivers for ubuntu 9.10 on Compaq 510 notebook.
Here is the output of  "lshw -C network"

  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: ioport:6000(size=256) memory:e8000000-e8003fff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: eth0
       version: 10
       serial: 18:a9:05:d2:e5:0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A ip=192.168.1.2 latency=0 multicast=yes
       resources: irq:29 memory:e0000000-e0003fff ioport:2000(size=256)

---

### Post by chili555 on 2010-03-03
Please post:```
lspci -nn
```Thanks.

---

### Post by ravindika on 2010-03-05
**Here is the output of lspci -nn**

**Thanks.**

00:00.0 Host bridge [0600]: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub [8086:2a10] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller [8086:2a12] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller [8086:2a13] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
10:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8171] (rev 10)
30:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4357] (rev 10)

---

### Post by chili555 on 2010-03-05
Your Realtek uses the driver *r8192se_pci*. You will need to get an ethernet connection and get some files from the internet:```
sudo apt-get install linux-headers-generic build-essential
```Then go here: [http://ubuntuforums.org/showpost.php?p=8754255&postcount=5](http://ubuntuforums.org/showpost.php?p=8754255&postcount=5)

You can follow each step carefully and even copy and paste his commands into a terminal. There is one correction, however, his two commands that start with 'sed' should be run as sudo; that is, sudo sed ...etc.

You should then disconnect the wire and click the Network Manager icon and connect wirelessly.

I tested this just now and it compiles with a couple of warnings but no errors. The module built and loaded without problems.

---

### Post by ravindika on 2010-03-05
It works for me :P 

Thanks.

---

### Post by arturieto on 2010-04-22
Dear Chili555,

please help me get my wireless connection working.  I follow this thread and here is my lspci -nn:

art@art-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub [8086:2a10] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller [8086:2a12] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller [8086:2a13] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
30:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4357] (rev 10)
art@art-laptop:~$ 


My ubuntu os is lucid 10.04, kernel linux 2.6.32-20-generic,gnome 2.30.0, if these data are needed.

Please help me, I been with Ubuntu since version 8.04 but it is only this time with karmic and lucid i get this problem.

---

### Post by chili555 on 2010-04-22
> Intel Corporation PRO/Wireless 3945ABG The native driver ought to connect immediately. What does this tell us?```
dmesg | grep iwl
rfkill list
```Thanks.

---

### Post by arturieto on 2010-04-23
dear sir,

here are the result of the command executed:

art@art-laptop:~$ dmesg | grep iwl
[   16.747806] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   16.747810] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   16.747925] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.747940] iwl3945 0000:10:00.0: setting latency timer to 64
[   16.857506] iwl3945 0000:10:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   16.857510] iwl3945 0000:10:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   16.857664] iwl3945 0000:10:00.0: irq 31 for MSI/MSI-X
[   16.893762] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   17.058676] iwl3945 0000:10:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   17.118021] iwl3945 0000:10:00.0: loaded firmware version 15.32.2.9
[   17.199740] Registered led device: iwl-phy0::radio
[   17.199761] Registered led device: iwl-phy0::assoc
[   17.199817] Registered led device: iwl-phy0::RX
[   17.199835] Registered led device: iwl-phy0::TX
[   56.603253] Modules linked in: nls_utf8 isofs binfmt_misc snd_hda_codec_idt ppdev fbcon tileblit font bitblit softcursor vga16fb vgastate arc4 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iwl3945 iwlcore snd_timer snd_seq_device i915 drm_kms_helper mac80211 led_class uvcvideo videodev v4l1_compat joydev drm intel_agp snd cfg80211 psmouse serio_raw agpgart i2c_algo_bit video output soundcore snd_page_alloc lp parport usbhid hid ahci sky2
art@art-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
art@art-laptop:~$

---

### Post by chili555 on 2010-04-23
Everything looks perfect! When you click the Network Manager icon, do you see networks? Does it try to connect? What does this tell us?```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by arturieto on 2010-04-25
dear Chili555,

here's the result:

[I]art@art-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for art: 
wlan0     Interface doesn't support scanning : Network is down[/I]

art@art-laptop:~$

I can connect to the wireless auto but in a minute or two the wireless disconnects.  it search again, get connected, then disconnected . . . this goes on and on.

---

### Post by chili555 on 2010-04-25
Let's have a look at:```
ifconfig
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```Thanks.

---

### Post by arturieto on 2010-05-06
dear chili555,

art@art-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:b3:56:ae:21  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:b3ff:fe56:ae21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4085532 (4.0 MB)  TX bytes:596976 (596.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4440 (4.4 KB)  TX bytes:4440 (4.4 KB)

art@art-laptop:~$ sudo ifconfig wlan0 up
[sudo] password for art: 
art@art-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1A:EF:06:57:4D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"Ramigoso"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b6f9168f
                    Extra: Last beacon: 1640ms ago
                    IE: Unknown: 000852616D69676F736F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0700E04C01020300

art@art-laptop:~$

---

### Post by chili555 on 2010-05-06
If you detach the wire and let Network Manager start controlling the wireless, what does this tell us?```
iwconfig wlan0
```Does it connect and stay connected?

All your settings look perfect.

---

### Post by LouisBlank on 2010-09-11
Re: network UNCLAIMED in wireless on ubuntu 10.04 (32bit)
Here is the output of lspci -nn


Thanks.

```
extra@extra-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82P965/G965 Memory Controller Hub [8086:29a0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82P965/G965 PCI Express Root Port [8086:29a1] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G965 Integrated Graphics Controller [8086:29a2] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller [8086:2810] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller [8086:2820] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller [8086:2825] (rev 02)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
03:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
03:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
05:01.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
05:04.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)

```

---

### Post by francisco.dornelles on 2011-08-11
sorry to bother, but i have the same problem:


00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
03:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822]
03:00.1 System peripheral [0880]: Ricoh Co Ltd Memory Stick Host Controller [1180:e230]
03:00.4 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822]
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
3f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
3f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)


thanks in advance!

---

