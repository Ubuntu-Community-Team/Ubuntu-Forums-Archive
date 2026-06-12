---
title: "Broadcom 318 wireless no-go + install cd quit running"
date: 2012-07-01
forum: Networking &amp; Wireless
---

### Post by joe needs help on 2012-07-01
Hello, 
 
I'm trying to get an older Compaq laptop up and running with 12.04.  I can't get the wireless card to work.  I've tried several things in this post:  [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)  including post #44 without success.  Most of the time, wireless networking doesn't even show up in the Networking menu up near the clock.  Also read some of post [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868) 
 
I'm starting to worrry that I damaged the wireless card or the bios during the install of Ubuntu because the install cd hung when I tried to turn on the wifi switch.  The machine had XP sp2 on it and ran okay when I booted it a couple of times.  Running XP the wireless showed available networks, but I didn't try and log on to one.  It's a new pc to me, and this is what I've done to it far: 
    I booted the 12.04 install cd and tried 12.04.  It seemed fine. 
    I booted the pc with a program called Spinrite to do some maintenance on the hard drive (all was fine). 
    I booted the pc with a program called DBAN and overwrote the hard drive (all went fine). 
    I booted the 12.04 install cd, selected &quot;Install Ubuntu&quot;, the &quot;checklist window&quot; came up and said I didn't have an internet connection.  I noticed that the wifi switch light wasn't on, so I pushed it.  Then I started to move the mouse to the network menu up by the clock and the pc froze.  The only way I could get it to do anything was to reboot by pressing and holding the power button.  The 12.04 install cd has not booted since (6 - 8 attempts).  I burned a new 12.04 install cd and it won't boot.  It hangs after &quot;Ubuntu&quot; appears in the middle of the screen and the dots have changed from white to orange to white a few times.  I've let it sit at that point for 3.5 minutes without it doing anything before holding the power button down to shut it down. 
 
    I booted the 10.04 install cd and installed 10.04.    I got the message about proprietary drivers being available and activated the Broadcom driver.  The wireless didn't work. 
    I booted the 11.10 install cd and installed 11.10 over 10.04.  The wireless didn't work. 
    I updated 11.10, then upgraded to 12.04.  The wireless doesn't work. 
    I've used Synaptic Package manager to install and remove the various Broadcom files multiple times. 
    I tried the tips given in Post #44 (of the 1st thread mentioned above), both the internet connected and without connection tips.  No luck. 
 
Based on post# 44 and the card in the laptop, it needs the following installed: 
    bcmwl-kernel-source 
    firmware-b43-installer 
    b43-fwcutter 
but I have tried the sta driver as well.
 
I definitely need help at this point.  Besides the wireless problem any suggestions on why the 12.04 install cd won't run would also be appreciated. 
 
Thanks - Joe 
 
Here is the info on the pc: 
 
Compaq Presario V2000     p/n:  ez625ua#abl 
 
Broadcom BCM4318  (14e4:4318) (Rev 02) 
 

joe@laptop1:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: Advanced Micro Devices [AMD] nee ATI IXP SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller




joe@laptop1:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



joe@laptop1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:6e:42:43  
          inet addr:192.168.1.117  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe6e:4243/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37214 (37.2 KB)  TX bytes:32338 (32.3 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8630 (8.6 KB)  TX bytes:8630 (8.6 KB)



joe@laptop1:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.



joe@laptop1:~$ lsmod
Module                  Size  Used by
rfcomm                 38139  0 
arc4                   12473  2 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
b43                   342643  0 
binfmt_misc            17292  1 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
joydev                 17393  0 
bcma                   25651  1 b43
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
pcmcia                 39791  0 
snd_atiixp             19337  2 
snd_atiixp_modem       18604  0 
snd_ac97_codec        106082  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
snd_seq_midi           13132  0 
snd_pcm                80845  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
radeon                729591  3 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  12 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87213  0 
serio_raw              13027  0 
yenta_socket           27428  0 
ssb                    50691  1 b43
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
k8temp                 12905  0 
i2c_piix4              13093  0 
snd_page_alloc         14115  3 snd_atiixp,snd_atiixp_modem,snd_pcm
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
video                  19068  0 
i2c_algo_bit           13199  1 radeon
wmi                    18744  1 hp_wmi
shpchp                 32325  0 
mac_hid                13077  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
8139too                23283  0 
8139cp                 22633  0 
pata_atiixp            12999  4 


Not posting the dmeg because it's so large and couldn't scroll all way to the top of it.



joe@laptop1:~$ sudo lshw -C network
[sudo] password for joe: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:6e:42:43
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.117 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
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
       serial: 00:14:a5:b6:2f:81
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-26-generic firmware=508.1084 link=no multicast=yes wireless=IEEE 802.11bg



joe@laptop1:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

eth0      Interface doesn't support scanning.



joe@laptop1:~$ lsb_release -d
Description:    Ubuntu 12.04 LTS



joe@laptop1:~$ uname -mr
3.2.0-26-generic i686



joe@laptop1:~$ sudo /etc/init.d/networking restart
[sudo] password for joe: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by joe needs help on 2012-07-02
Solved

I figured out the wireless problem.  It was operator error.  Before I had the wireless problem, the 12.04 install cd stopped booting.  While trying to fix that I changed some things in the BIOS.  One of the things I changed was to disable the wireless adapter, and I forgot to re-enable it!  Once I re-enabled the wireless adapter, the wireless started working.

For anyone having trouble with a Broadcom 4318 adapter, the following driver works for me:

firmware-b43-installer
b43-fwcutter

It is version 1:015-9

Joe

---

