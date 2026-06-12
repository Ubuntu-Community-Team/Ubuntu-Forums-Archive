---
title: "DHCP loses IP after 24-48 hours and cannot re-obtain until reboot"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by thex2 on 2009-06-08
I can obtain an external ip address from verizon fios on my eth0 card. however, after 24-48 hours, it loses the ip address and I cannot renew it (sudo ifdown eth0... sudo ifup eth0) until I reboot my computer. I do not have this issue with any other router that I've tried (3 different linksys routers and 2 different actiontec routers). Any ideas on how to fix the issue of ubuntu dropping the ip address, or at least make it to where it will auto-renew it once it's dropped? Thanks.

Additional Info and a little bit of history:
ubuntu-8.10-desktop-amd64.iso

I did an apt-get remove network-manager (this was interfering with my /etc/network/interfaces file, so somebody on #ubuntu on freenode.org told me to remove it) because I was unable to obtain an external IP address on eth0 before it was removed.

the below information (route -n and joe /etc/network/interfaces) was taken once I went back to my linksys router and changed eth1 to 192.168.1.104 instead of my default gateway of 192.168.1.1

route -n:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

joe /etc/network/interfaces:
auto lo eth0 eth1

iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet static
address 192.168.1.104
netmask 255.255.255.0

Also, the IP address does not change after the reboot or installing a different router. So I don't think that it's my ISP dropping the IP. And if they are, they certainly aren't giving me a new one. My IP changes about once a year from Verizon.

admin@ubuntu:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc R481 [Radeon X850XT-PE]
01:00.1 Display controller: ATI Technologies Inc R481 [Radeon X850XT-PE] (Secondary)
02:08.0 Ethernet controller: Linksys Gigabit Network Adapter (rev 10)
02:09.0 RAID bus controller: 3ware Inc 7xxx/8xxx-series PATA/SATA-RAID (rev 01)
02:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
admin@ubuntu:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
admin@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2f:a7:eb:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:1a:70:11:c8:fe  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:70ff:fe11:c8fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:229203 (229.2 KB)  TX bytes:182761 (182.7 KB)
          Interrupt:19 Base address:0xc00 

eth0:avahi Link encap:Ethernet  HWaddr 00:11:2f:a7:eb:6c  
          inet addr:169.254.8.45  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6608 (6.6 KB)  TX bytes:6608 (6.6 KB)

admin@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

pan0      no wireless extensions.

admin@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: Gigabit Network Adapter
       vendor: Linksys
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth1
       version: 10
       serial: 00:1a:70:11:c8:fe
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.104 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 66:2b:6b:0b:40:6c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by superprash2003 on 2009-06-08
check your router's DHCP settings and increase thre DHCP lease time..

---

### Post by thex2 on 2009-06-08
> **superprash2003 said:**
> check your router's DHCP settings and increase thre DHCP lease time..
ubuntu/firestarter is acting as my router. eth0 is my dhcp nic and eth1 is my default gateway nic. So how do I check with ubuntu on my DHCP settings and how do I increase the DHCP lease time in ubuntu? (this must be done without network-manager because network-manager screws everything up). Thanks.

---

### Post by hansamurai on 2009-06-08
I pretty much have the same problem with my Ubuntu 8.10 machine except I have a Linksys WRT54G with Tomato installed as my router.  I have a static IP and Tomato says my lease time is 24 hours but yet I lose all WAN connections in seemingly less than that, though I don't know for sure.  But shouldn't I re-lease with a static IP?  I have a Xubuntu 9.04 laptop that has been running for over a week without any networking issues.

I can make a new thread about this if necessary.  I've tried dhclient and /etc/init.d/networking restart to no avail.

Also I specifically say WAN connections because I can still reach my router.

---

