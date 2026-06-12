---
title: "Can not enable 8192U wireless usb in Karmic"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by hoptimusPrime on 2010-02-27
i am trying to get a wireless driver(s) to work in Karmic.  maybe this should be in beginner talk, so bare with me

I have 2 wireless network adapters:
a usb wirelss N (net8192U), and an internal pci wireless G (RT2500pci).
i installed the xp driver for the 8192U using ndiswrapper.  it gives an error message, but then says 'device present: yes'

I also have a wired ethernet connection i am using now in the meantime.  neither wireless devices will connect to the router or internet

I seem to have the 8192U driver installed, but i can not enable wireless in network manager applet, it is grey and the box can not be checked..

here are the outputs for some commands:

~$** lshw:**

(I will only show the last few lines, the output is quite long)
........
*-network:1 DISABLED
                description: Wireless interface
                product: RT2500 802.11g Cardbus/mini-PCI
                vendor: RaLink
                physical id: 9
                bus info: pci@0000:02:09.0
                logical name: wlan1
                version: 01
                serial: 00:13:d3:73:8e:2f
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2500pci latency=64 multicast=yes wireless=IEEE 802.11bg
                resources: irq:22 memory:fbffc000-fbffdfff
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2
             resources: irq:17 memory:fbdfcc00-fbdfccff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan5
       serial: 00:02:72:85:d6:f4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8192u driverversion=1.55+Realtek Semiconductor Corp. link=yes multicast=yes wireless=IEEE 802.11g



~$ **iwconfig:**

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wlan5     IEEE 802.11g  ESSID:"Stake's not free any more"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:02:72:85:D4:23   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


$-**ifconfig**:

eth0      Link encap:Ethernet  HWaddr 00:16:17:4e:7b:71  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe4e:7b71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:343230 (343.2 KB)  TX bytes:43925 (43.9 KB)
          Interrupt:18 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan5     Link encap:Ethernet  HWaddr 00:02:72:85:d6:f4  
          inet6 addr: fe80::202:72ff:fe85:d6f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3698 (3.6 KB)  TX bytes:6499 (6.4 KB)

wlan5:avahi Link encap:Ethernet  HWaddr 00:02:72:85:d6:f4  
          inet addr:169.254.11.146  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

 
any suggestions on how to troubleshoot?
i would like to get one or both of these wireless adapters working

---

