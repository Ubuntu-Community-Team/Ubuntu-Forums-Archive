---
title: "AR5007 also known as AR424x 802.11abg"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by kamssada on 2008-12-07
can't get my network card to work under kubuntu... I have tried so many different ways of installing this driver with no result

[http://ubuntuforums.org/showthread.php?t=743299&highlight=atheros+ar5007](http://ubuntuforums.org/showthread.php?t=743299&highlight=atheros+ar5007)

in the link above the address for the madwifi was outdated, i went to get the correct one at [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)


also i did try the ndisgtk using the ndiswrapper, by downloading the vista drive for vista, then unpackaged it to an USB, and then downloaded it to kubuntu, and used the ndiswrapper to install it, and disabled the kubuntu preinstalled one in the system>hardware drivers... [http://ubuntuforums.org/showthread.php?t=756318](http://ubuntuforums.org/showthread.php?t=756318)
[http://lxer.com/module/newswire/view/46385/](http://lxer.com/module/newswire/view/46385/)


WHAT CAN I DO??? this is my second day at Kubuntu and its so frustrating... 

```
kenneth@kenneth-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:0f:d1:20  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe0f:d120/64 Scope:Link            
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1            
          RX packets:295 errors:0 dropped:0 overruns:0 frame:0          
          TX packets:375 errors:0 dropped:0 overruns:0 carrier:0        
          collisions:0 txqueuelen:1000                                  
          RX bytes:180002 (180.0 KB)  TX bytes:66459 (66.4 KB)          
          Interrupt:20 Base address:0x2000                              

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0                            
          RX bytes:1700 (1.7 KB)  TX bytes:1700 (1.7 KB)       

kenneth@kenneth-laptop:~$ iwconfig
lo        no wireless extensions. 

eth0      no wireless extensions.

pan0      no wireless extensions.

kenneth@kenneth-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] AddressMap
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
kenneth@kenneth-laptop:~$

```

I also just realized that when i start the computer, and error message pops up... PCI can't be loaded... goes to fast to actually read the whole thing..

---

### Post by kamssada on 2008-12-07
It works, i just didn't take time to reboot the computer... lol :p

still didn't solve the graphing card issue though... NDivia settings are not working

---

