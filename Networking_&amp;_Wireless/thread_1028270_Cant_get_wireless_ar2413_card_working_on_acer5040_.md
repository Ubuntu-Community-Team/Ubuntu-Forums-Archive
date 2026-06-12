---
title: "Cant get wireless ar2413 card working on acer5040 ubuntu 8.10live"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by linuxole on 2009-01-02
I new to ubuntu, and cant get the wireless to work. Read through several posts on this issue, and followed instructions on madwifi without luck. Getting some errors when I follow instructions.

I only get wired internet connection on auto eth0. 

Here are the info I learned from other posts: 
> olav@olav-laptop:~$ lspci | grep ath
olav@olav-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
06:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
olav@olav-laptop:~$ 

> olav@olav-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

olav@olav-laptop:~$ 

  
Is there debian drivers for this ?  Or could someone give me a step by step explanation on howto get this working.

Thanks from Norway :D

---

### Post by linuxole on 2009-01-02
Additional info.. now trying to install ndiswrapper.

> olav@olav-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:06:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=80 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:46:26:b0
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.44 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0e:01:5b:c5:21:96
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
olav@olav-laptop:~$ 



> 
When following this instructions: 
sudo apt-get install build-essential patch
wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0)
tar -xzvf ndiswrapper*
cd ndiswrapper*
wget [http://www.slackware.com/~alien/slackbuilds/ndiswrapper/build/ndiswrapper_kernel_2.6.27.patch](http://www.slackware.com/~alien/slackbuilds/ndiswrapper/build/ndiswrapper_kernel_2.6.27.patch)
patch -p0 < ndiswrapper_kernel_2.6.27.patch
make
sudo make install

I get this error message when i try make : 

> olav@olav-laptop:~/download/ndiswrapper-1.53$ make
make -C driver
make[1]: Entering directory `/home/olav/download/ndiswrapper-1.53/driver'
Makefile:51: *** No .config found in , please set KBUILD to configured kernel.  Stop.
make[1]: Leaving directory `/home/olav/download/ndiswrapper-1.53/driver'
make: *** [all] Error 2
olav@olav-laptop:~/download/ndiswrapper-1.53$ 



and sudo make: 

> olav@olav-laptop:~/download/ndiswrapper-1.53$ sudo make install
make -C driver install
make[1]: Entering directory `/home/olav/download/ndiswrapper-1.53/driver'
Makefile:51: *** No .config found in , please set KBUILD to configured kernel.  Stop.
make[1]: Leaving directory `/home/olav/download/ndiswrapper-1.53/driver'
make: *** [install] Error 2
olav@olav-laptop:~/download/ndiswrapper-1.53$ 


---

