---
title: "Intel Wireless 2200bg - Ubuntu 9.10 - ipw2200 - HELP!!"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by Templeman on 2010-03-04
My dear friends,

 I have been trying for months to get my wireless working on my acer laptop and I am now beyond despair. I'm fairly new to the linux/ubuntu world, so please bear with me as I go about things. I using an Acer Extensa 67000 and here is what is at issue:
 

 **ubuntu@ubuntu:~$ lspci -nn | grep 'Wireless'**
 06:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
 

 **ubuntu@ubuntu:~$ lspci -vn**
 On this one I posted just what I thought would be relevant:
 

 06:04.0 0280: 8086:4220 (rev 05) 
     Subsystem: 8086:2701 
     Flags: bus master, medium devsel, latency 32, IRQ 17 
     Memory at b0101000 (32-bit, non-prefetchable) [size=4K] 
     Capabilities: <access denied> 
     Kernel driver in use: ipw2200 
     Kernel modules: ipw2200 



  
 **ubuntu@ubuntu:~$ lsusb**
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 002: ID 059f:1018 LaCie, Ltd  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 

 **ubuntu@ubuntu:~$ ifconfig**
 eth0      Link encap:Ethernet  HWaddr 00:c0:9f:da:08:d5   
           inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: fe80::2c0:9fff:feda:8d5/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:19312 errors:1 dropped:1 overruns:1 frame:0 
           TX packets:18239 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:18079426 (18.0 MB)  TX bytes:2808653 (2.8 MB) 
           Interrupt:16 Base address:0x2000  
  
 eth1      Link encap:Ethernet  HWaddr 00:13:ce:5a:12:b6   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
           Interrupt:17 Base address:0x2000 Memory:b0101000-b0101fff  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:520 (520.0 B)  TX bytes:520 (520.0 B) 
 

 **ubuntu@ubuntu:~$ iwconfig**
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 eth1      unassociated  ESSID:eek:ff/any   
           Mode:Managed  Channel=0  Access Point: Not-Associated    
           Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0   
           Retry limit:7   RTS thr:eek:ff   Fragment thr:eek:ff 
           Power Management:eek:ff 
           Link Quality:0  Signal level:0  Noise level:0 
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 

 **ubuntu@ubuntu:~$ lsmod**
 Module                  Size  Used by 
 pcmcia                 36808  0  
 nf_conntrack           67608  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf  _nat,nf_conntrack_ipv4,nf_conntrack_ftp 
 snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid  i_event 
 ipw2200               140292  0  
 snd_timer              22276  2 snd_pcm,snd_seq 
 snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi  ,snd_seq 
 iptable_filter          3100  1  
snd 59204 19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec, snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_se q_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 libipw                 43148  1 ipw2200 
 lib80211                6432  2 ipw2200,libipw 
 
 **ubuntu@ubuntu:~$ dmesg | grep ipw2200**
 [    8.509829] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[    8.509833] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[    8.642245] ipw2200 0000:06:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.644569] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[    8.644628] ipw2200 0000:06:04.0: firmware: requesting ipw2200-bss.fw
[    9.322372] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

**ubuntu@ubuntu:~$ sudo lshw -C network**
 *-network:0              
        description: Wireless interface 
        product: PRO/Wireless 2200BG [Calexico2] Network Connection 
        vendor: Intel Corporation 
        physical id: 4 
        bus info: pci@0000:06:04.0 
        logical name: eth1 
        version: 05 
        serial: 00:13:ce:5a:12:b6 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm bus_master cap_list ethernet physical wireless 
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated 
        resources: irq:17 memory:b0101000-b0101fff 
   *-network:1 
        description: Ethernet interface 
        product: RTL-8139/8139C/8139C+ 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 8 
        bus info: pci@0000:06:08.0 
        logical name: eth0 
        version: 10 
        serial: 00:c0:9f:da:08:d5 
        size: 100MB/s 
        capacity: 100MB/s 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.3 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s 
        resources: irq:16 ioport:2000(size=256) memory:b0102000-b01020ff 
 

 **ubuntu@ubuntu:~$ iwlist scan**
 lo        Interface doesn't support scanning. 
  
 eth0      Interface doesn't support scanning. 
  
 eth1      No scan results 
 

 **ubuntu@ubuntu:~$ lsb_release -d**
 Description:    Ubuntu 9.10 
 

 **ubuntu@ubuntu:~$ uname -mr**
 2.6.31-19-generic i686
 

 **ubuntu@ubuntu:~$ sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces...
 Ignoring unknown interface wlan0=wlan0. 
                                                                          [ OK ] 
  

 

 END OF LISTING
  

 

 I am grateful for all and any help I can get with this. RFkill doesn't work. I really don't know where else to go with this. I have tried reinstalling the network manager - hasn't worked. Both Wicd and network manager don't even recognise any networks. Everything worked fine under windows. 

Again, thanks for your help in advance.

 Love,
 
 Templeman

---

