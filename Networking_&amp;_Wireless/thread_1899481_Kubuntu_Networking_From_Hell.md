---
title: "Kubuntu Networking From Hell"
date: 2011-12-23
forum: Networking &amp; Wireless
---

### Post by T-Blanford on 2011-12-23
Lost connection to Internet again after latest Kernal upgrade 2.6.32-37 64 bit

OS -- Kubuntu 10.04 LTS 64 bit
Net/LAN - wired Ethernet, 100 Mbit, Static IP, NO WIRELESS
Network Manger - Permanently Removed

Rechecked data in the following files - 

/etc/network/interfaces
/etc/resolv.conf

can post contents but are unchanged and are as per -

[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

for static IP setups.  

Also checked the following but found nothing that stands  out -

/etc/udev/rules.d/70-persistent
/etc/hosts

$ route -n

$ netstat  (sockets) I have no idea which talk to the outside world

Other references consulted - 

[http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html](http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html)
[http://manpages.ubuntu.com/manpages/lucid/en/man5/interfaces.5.html](http://manpages.ubuntu.com/manpages/lucid/en/man5/interfaces.5.html)
[http://manpages.ubuntu.com/manpages/lucid/man8/route.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/route.8.html)

The command -
sudo ifup eth0

does not bring up eth0

Neither does -
sudo /etc/init.d/networking restart

Machine will ping 127.0.0.1 just fine but nothing else on the LAN

I would appreciated any ideas on what else I can check. 

Thank You

---

### Post by chili555 on 2011-12-23
> Rechecked data in the following files -

/etc/network/interfaces
/etc/resolv.conf

can post contentsPlease do so. Also, are there other computers on the same network? What is a sample IP address and gateway address?

---

### Post by T-Blanford on 2011-12-24
Following is a data dump from the machine - 

$ lspci -knn

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d131]
(rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root
Port 1 [8086:d138] (rev 11)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System
Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and
Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System
Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous
Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link
[8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing
and Protocol Registers [8086:d151] (rev 11)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset
USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
        Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High
Definition Audio [8086:3b56] (rev 05)
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI
Express Root Port 1 [8086:3b42] (rev 05)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI
Express Root Port 5 [8086:3b4a] (rev 05)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI
Express Root Port 6 [8086:3b4c] (rev 05)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.6 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI
Express Root Port 7 [8086:3b4e] (rev 05)                                        
                                                                              
        Kernel driver in use: pcieport                                          
                                                                                
                                                                           
        Kernel modules: shpchp                                                  
                                                                                
                                                                           
00:1c.7 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI
Express Root Port 8 [8086:3b50] (rev 05)                                        
                                                                              
        Kernel driver in use: pcieport                                          
                                                                                
                                                                           
        Kernel modules: shpchp                                                  
                                                                                
                                                                           
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset
USB2 Enhanced Host Controller [8086:3b34] (rev 05)                              
                                                                              
        Kernel driver in use: ehci_hcd                                          
                                                                                
                                                                           
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev
a5)                                                                             
                                                                             
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface
Controller [8086:3b02] (rev 05)                                                 
                                                                                
        Kernel modules: iTCO_wdt                                                
                                                                                
                                                                           
00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4
port SATA IDE Controller [8086:3b20] (rev 05)                                   
                                                                             
        Kernel driver in use: ata_piix                                          
                                                                                
                                                                           
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus
Controller [8086:3b30] (rev 05)                                                 
                                                                               
 
        Kernel modules: i2c-i801                                                
                                                                                
                                                                           
00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 2
port SATA IDE Controller [8086:3b26] (rev 05)                                   
                                                                             
        Kernel driver in use: ata_piix                                          
                                                                                
                                                                           
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0e22]
(rev a1)                                                                        
                                                                            
        Kernel driver in use: nvidia                                            
                                                                                
                                                                           
        Kernel modules: nvidia, nvidiafb, nouveau                               
                                                                                
                                                                           
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0beb] (rev a1)     
                                                                                
                                                                           
02:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network
Connection [8086:10d3]                                                          
                                                                               
        Kernel driver in use: e1000e                                            
                                                                                
                                                                           
        Kernel modules: e1000e
03:00.0 SATA controller [0106]: JMicron Technology Corp. JMB361 AHCI/IDE
[197b:2361] (rev 02)
        Kernel driver in use: ahci
        Kernel modules: ahci
03:00.1 IDE interface [0101]: JMicron Technology Corp. JMB361 AHCI/IDE
[197b:2361] (rev 02)
        Kernel driver in use: pata_jmicron
        Kernel modules: pata_jmicron
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.
RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
        Kernel driver in use: r8169
        Kernel modules: r8169
***********
$ lsmod

Module                  Size  Used by
ppdev                   6375  0 
snd_hda_codec_realtek   279104  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
snd_seq                57481  6
snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
nvidia              12120076  40 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
snd_timer              23681  2 snd_pcm,snd_seq
nouveau               515227  0 
ttm                    61039  1 nouveau
snd_seq_device          6888  5
snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         30742  1 nouveau
usblp                  12407  0 
snd                    71283  16
snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,
snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   200384  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41116  0 
hid                    83888  1 usbhid
ahci                   38350  0 
e1000e                136301  0                                                 
                                                                                
                                                                           
pata_jmicron            2747  0                                                 
                                                                                
                                                                           
r8169                  39714  0                                                 
                                                                                
                                                                           
mii                     5237  1 r8169        

*********

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.121
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

************

$ cat /etc/resolv.conf
search paonia.com
nameserver 216.237.72.66
nameserver 216.237.77.2
nameserver 208.67.222.222
nameserver 208.67.220.220
$ 

***************
$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:25:11:74:37:25  
          inet addr:192.168.0.121  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:35 Base address:0x6000 

eth2      Link encap:Ethernet  HWaddr 00:1b:21:b3:b5:8f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fbde0000-fbe00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68691 (68.6 KB)  TX bytes:68691 (68.6 KB)
$

************ Note - Live Ethernet cable pluged into eth2 at this point

$ dmesg| grep eth
[    1.941021] eth0: RTL8168d/8111d at 0xffffc90000c66000, 00:25:11:74:37:25,
XID 081000c0 IRQ 35
[    2.109450] 0000:02:00.0: eth1: (PCI Express:2.5GB/s:Width x1)
00:1b:21:b3:b5:8f
[    2.109660] 0000:02:00.0: eth1: Intel(R) PRO/1000 Network Connection
[    2.109817] 0000:02:00.0: eth1: MAC: 3, PHY: 8, PBA No: e46981-005
[   13.562037] udev: renamed network interface eth1 to eth2
[   13.604033] r8169: eth0: link down
[   13.604608] ADDRCONF(NETDEV_UP): eth0: link is not ready
$
Additional gory details are as follows - machine is set up as dual boot. The kernel update disabled Internet access for both Linux and Windows. The machine also has a late model Intel Ethernet card installed. I shut the machine down over night, next morning, swapped the Ethernet cable to the Intel board, booted in to Windows and Internet connectivity was restored to Windows but not Kubuntu. 

BTW - the machine my wife is using as a replacement is from 2003-2004, runs Kubuntu 8.x and has had exactly zero networking problems.

Here is an interesting post that may help others as well - 

[http://kubuntuforums.net/forums/index.php?action=printpage;topic=3100052.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3100052.0)

Any information much appreciated. Thanks

---

### Post by chili555 on 2011-12-24
Your interfaces file looks a little busy; I might change it to:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.121
netmask 255.255.255.0
#network 192.168.0.0
#broadcast 192.168.0.255
gateway 192.168.0.1
```With the ethernet plugged in to eth0, reboot and then please let us see:```
sudo ethtool eth0
dmesg | grep -e eth -e r8169
```

---

### Post by T-Blanford on 2011-12-26
The changes to the "interfaces" file had no affect.

When I built the machine I neglected to load the ethtool app and can not now without an Ethernet connection. On reboot - 

Note - Live Ethernet cable plugged into eth0

$ dmesg | grep -e eth -e r8169
[    1.955365] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.955518] r8169 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.955699] r8169 0000:05:00.0: setting latency timer to 64
[    1.955749] r8169 0000:05:00.0: irq 38 for MSI/MSI-X
[    1.956115] eth0: RTL8168d/8111d at 0xffffc90000c56000, 00:25:11:74:37:25,
XID 081000c0 IRQ 38
[    2.112503] 0000:02:00.0: eth1: (PCI Express:2.5GB/s:Width x1)
00:1b:21:b3:b5:8f
[    2.112713] 0000:02:00.0: eth1: Intel(R) PRO/1000 Network Connection
[    2.112871] 0000:02:00.0: eth1: MAC: 3, PHY: 8, PBA No: e46981-005
[   13.333703] udev: renamed network interface eth1 to eth2
[   13.430379] r8169: eth0: link down
[   13.430955] ADDRCONF(NETDEV_UP): eth0: link is not ready
$ 

I downloaded the latest greatest Ubuntu distro and ran it in live mode. Running the same command as above gave essentially the same result. Swapping the Ethernet cable to eth1 (there was no eth2 under ifconfig -a) and running the same command produced the same result for eth0 but eth1 was reported as up and connected at correct speed etc. The networking panel would not let me enter a static addresses or other data so I could try a ping. Same with trying to write a new "interfaces" and "resolv.conf" files. 

At this point Kubuntu will not connect with either eth0 or eth1 (eth2) even though eth1(2) is obviously alive and well. 

Any additional help much appreciated. I love Kubuntu if I can just solve this damnable networking issue.

---

### Post by T-Blanford on 2011-12-26
Problem Solved. The idea that solved the problem came from the Kubuntu forms. Running Ubuntu 10.04.3 in live mode really leads to the problem and how to solve things if you have an additional card. Running - 

dmesg | grep -e eth in live mode

clearly shows that eth1 (eth2 under Kubuntu) is very much alive and well. Editing the "interfaces" file to reflect eth2 not eth0 restored the Internet to the machine. I have no idea why eth0 and eth1 are not working or listed but simply matching what dmesg shows with what is in the "interfaces" file solved the problem as least for now.

Thanks for you interest.

---

