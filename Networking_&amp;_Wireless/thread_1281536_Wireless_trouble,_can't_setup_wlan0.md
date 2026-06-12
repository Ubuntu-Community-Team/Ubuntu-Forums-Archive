---
title: "Wireless trouble, can't setup wlan0"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by JSPautsch on 2009-10-03
**EDIT: Got the first problem fixed, *but* another one cropped up. Leaving this post up in case it helps anyone else. See my reply for the new related issue & info.**

I've been searching the internet nonstop for several hours today and yesterday and attempted at least half a dozen fixes to no avail. I have a Toshiba L300D with a Realtek 8192E wireless card. The card itself is fine because it works in vista but I'm having mountains of trouble setting it up in Ubuntu (I have the latest stable version).

I've tried using ndiswrapper to install the windows drivers but it hasn't worked. The closest I get is with a "net819xp.inf" driver I downloaded from Toshiba, where it will give me some "Cannot confirm hardware blah blah" errors but still lists the "Hardware Present" as "Yes." For example:

net819xp : driver installed
    device (10EC:8192) present

However, it still doesn't seem to work. The network tool doesn't list any wireless connection options and I haven't even been able to get wlan0 to show up. This has been the biggest difference I was able to find between my issue and the others I read up on, they always had wlan0 or wifi0 listed, but I do not.

I'm fairly new to Linux.

**1 ) Machine Brand and Model (PC/Laptop)**:
     Code:
     Toshiba Satellite L300D laptop 
**2 ) Wireless Brand, Model and Wireless Chipset:**
     Code:
     $ lspci
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
**3 ) check interface:**

You can see here that no wlan0 interface is displayed.

     Code:
     $ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1e:33:de:09:ba  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:33ff:fede:9ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16261552 (16.2 MB)  TX bytes:1918380 (1.9 MB)
          Interrupt:250 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.


**4 ) Check for modules:**
     Code:
     $ lsmod

Module                  Size  Used by
ndiswrapper           250624  0 
binfmt_misc            18572  1 
ppdev                  16904  0 
radeon                357792  2 
drm                   123232  3 radeon
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  0 
joydev                 20864  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557364  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
i2c_piix4              20112  0 
video                  29204  0 
psmouse                64028  0 
serio_raw              14468  0 
pcspkr                 11136  0 
output                 11648  1 video
input_polldev          12688  0 
shpchp                 44572  0 
r8169                  46596  0 
mii                    14464  1 r8169
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit


**5 ) Kernel boot messages**

Saw these messages, probably a result of me fooling around with this page:

[http://ubuntuforums.org/showpost.php?p=7808142&postcount=11](http://ubuntuforums.org/showpost.php?p=7808142&postcount=11)

     Code:
     $ dmesg

[ 3141.768036] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 3141.815865] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 3141.815884] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 3141.815897] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 3141.815916] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 3141.815928] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[ 3141.815940] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 3141.815958] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 3141.815983] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 3141.816124] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 3141.816164] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 3141.816175] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 3141.816187] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 3141.816206] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 3141.816225] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 3141.816241] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[ 3141.816253] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 3141.816276] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[ 3141.816289] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 3141.816302] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[ 3141.816313] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 3141.816325] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 3141.816337] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 3141.816350] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[ 3141.816362] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 3141.816375] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 3141.816387] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 3141.816399] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[ 3141.816404] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net819xp'
[ 3141.823914] ndiswrapper (load_wrap_driver:108): couldn't load driver net819xp; check system log for messages from 'loadndisdriver'
[ 3141.832180] usbcore: registered new interface driver ndiswrapper

 
**6 ) Network configuration**
     Code:
     $ sudo lshw -C network

  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0


**7 ) Scan for networks:**

Don't know what happened here.
     Code:
     $ iwlist scan wlan0

iwlist: unknown command `wlan0' (check 'iwlist --help')

**8 ) Ubuntu Version: **
     Code:
     $ lsb_release -d

Description:    Ubuntu 9.04

**9 ) Kernel/architecture (including 32 vs. 64 bit): **

It's 64-bit.

     Code:
     $ uname -mr

2.6.28-11-generic x86_64

**10 ) Restarting the network:**

tried manually adding wlan0 to the intefaces file with a suggestion I saw in another thread, but it keeps saying no device found, like when I restart the network. Here were the settings the thread listed:

auto wlan0
iface wlan0 inet dhcp
wireless_mode Auto
wireless_essid any
wireless_rate auto
wireless_txpower auto

     Code:
     $ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

---

### Post by JSPautsch on 2009-10-03
I ended up wiping my system and installing 9.10 32-bit, I heard it was having better luck with wireless and I wanted to wipe my 64bit off and replace it with 32 anyway.

After starting from scratch I followed this guide:

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

And was able to install 32-bit drivers from Samsung's website that were recognized. At long last, Wireless worked.

*Sort of.* The interface is there and I can see the other networks. I was able to connect to one of them (protected by WPA) for about 10 minutes before it mysteriously failed. After that, I'd be lucky if it was even able to establish a connection. Recently it hasn't been able to connect at all. I can still see the networks and it will say I have a good signal, but it just won't connect. I know the credentials are right, it just disconnects.

Is there any way for me to generate an output when I attempt to connect to a wireless network that I can post here? Thanks.

Here's my new info:

 **1 ) Machine Brand and Model (PC/Laptop)**:
     Code:
     Toshiba Satellite L300D laptop  
**2 ) Wireless Brand, Model and Wireless Chipset:**
     Code:
     $ lspci

05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01

**3 ) check interface:**
     Code:
     $ ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:24:d2:c0:d9:3d  
          inet6 addr: fe80::224:d2ff:fec0:d93d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3573 (3.5 KB)  TX bytes:7419 (7.4 KB)
          Interrupt:18 Memory:93100000-93104000 

$ iwconfig

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:26 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**4 ) Check for modules:**
     Code:
     $ lsmod

Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26664  2 
snd_hda_codec          69276  2 snd_hda_codec_realtek,snd_hda_intel
joydev                 10272  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
radeon                636000  1 
ttm                    36212  1 radeon
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
drm                   159584  3 radeon,ttm
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                34988  2 ttm,drm
i2c_algo_bit            5760  1 radeon
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd                    59204  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19380  0 
lp                      8964  0 
x_tables               16544  1 ip_tables
psmouse                56180  0 
soundcore               7264  1 snd
output                  2780  1 video
shpchp                 32272  0 
i2c_piix4               9932  0 
ndiswrapper           185404  0 
serio_raw               5280  0 
parport                35340  2 ppdev,lp
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
usb_storage            52544  0 
r8169                  32064  0 
mii                     5212  1 r8169


**5 ) Kernel boot messages**
     Code:
     $ dmesg[FONT=Verdana]

[    8.609207] wlan0: ethernet device 00:24:d2:c0:d9:3d using NDIS driver: net819xp, version: 0x500a5, NDIS version: 0x500, vendor: 'Realtek RTL8190 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8192.5.conf
[    8.609236] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   13.462870] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   50.674879] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   61.328519] wlan0: no IPv6 routers present

[/FONT] 
 
**6 ) Network configuration**
     Code:
     $ sudo lshw -C network

*-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:d2:c0:d9:3d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net819xp driverversion=1.55+Realtek Semiconductor Corp. latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:18 ioport:2000(size=256) memory:93100000-93103fff


**7 ) Scan for networks:**

This is the one I'm trying to connect to:

     Code:
     $ iwlist scan

Cell 02 - Address: 00:1F:F3:C4:C6:C0
                    ESSID:"Pioneer"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


**8 ) Ubuntu Version: **
     Code:
     $ lsb_release -d

Description:    Ubuntu karmic (development branch)

**9 ) Kernel/architecture (including 32 vs. 64 bit): **
     Code:
     $ uname -mr

2.6.31-11-generic i686


**10 ) Restarting the network:**

Nothing special.

     Code:
     $ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

---

### Post by northd_tech on 2009-10-27
Hi JS,

I had the exact same problem on my nephew's new Toshiba Satellite P505D with both Ultimate Ubuntu 2.2 and 2.3 (esp. with the 64-bit version).  I could not get the Realtek 8192E to install under 64-bit- I suspect there may be a Linux problem with the 64-bit Windows driver.  When I went back to the 32-bit UU 2.3 (based on Jaunty Jackalope 9.04), I had much less trouble (making sure to use the older "Win2KXP" 32-bit driver "rtl819xp.inf").

The Realtek 8192E WiFi still needed "ndiswrapper" installed, and I could never get the 64-bit WiFi driver to work- it said it was installed (and the driver installed), but I could never see "wlan0" interface. I recall the system freezing a few times with the 64-bit driver and 64-bit UU 2.3.

Here is a snippet of hardware diagnostic on that Realtek WiFi interface:
-----------------------------------------------------------------------
118: **udi = '/org/freedesktop/Hal/devices/pci_10ec_8192'**
info.udi = '/org/freedesktop/Hal/devices/pci_10ec_8192'
info.linux.driver = 'ndiswrapper'
linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0'
info.parent = '/org/freedesktop/Hal/devices/pci_1022_9604'
pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0'
**pci.product_id = 33170 (0x8192)**
pci.vendor_id = 4332 (0x10ec)
pci.subsys_product_id = 33153 (0x8181)
pci.subsys_vendor_id = 4332 (0x10ec)
pci.device_class = 2 (0x2)
pci.device_subclass = 128 (0x80)
pci.device_protocol = 0 (0x0)
pci.vendor = 'Realtek Semiconductor Co., Ltd.'
**info.vendor = 'Realtek Semiconductor Co., Ltd.'**
info.subsystem = 'pci'
info.product = 'Unknown (0x8192)'
pci.subsys_vendor = 'Realtek Semiconductor Co., Ltd.'
linux.hotplug_type = 2 (0x2)
linux.subsystem = 'pci'
---------------------------------------------------------------
Edit:  could one of the Mods maybe add "Realtek 8192E WiFi" to the thread title- that might help some find this.

Edit2:  OK- from my experience, the 8192E needs different sourcecode than the 8192SE.  See this thread here for my struggle (and a fix for the 8192 SE version):

[http://ubuntuforums.org/showthread.php?t=1329254](http://ubuntuforums.org/showthread.php?t=1329254)

---

