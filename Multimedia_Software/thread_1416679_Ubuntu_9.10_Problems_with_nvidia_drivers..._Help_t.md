---
title: "Ubuntu 9.10 Problems with nvidia drivers... Help the newbie"
date: 2010-02-26
forum: Multimedia Software
---

### Post by Tsabikos on 2010-02-26
Hello all,

 First of all I must apologise if I bring up a subject that seems to come up again and again. But being a complete beginner in Linux I didn't want to  follow blindly what was posted in other threads and mess things up to a point there was no return.

 The situation is as follows. I installed Ubuntu 9.10 last night, single boot, nothing else in the hard disk just Ubuntu. I am using a Acer Aspire 7520g laptop, with an nvidia GeForce 8600m GS.

  After updating and installing the nvidia drivers (version185) from System->Administration->Hardware drivers, I was getting the usual black screen of death.
Following the tips in [http://ubuntuforums.org/showthread.php?t=1349553](http://ubuntuforums.org/showthread.php?t=1349553) :
> 1) Install driver via Hardware Driver and do not reboot.
2) run a terminal and type: *sudo nvidia-xconfig --nvagp=1*
to create /etc/X11/xorg.conf with nvidia's agp enabled. You don't need to reboot.
3) type in the terminal: *sudo /etc/init.d/gdm stop*
4) log in and type *sudo gdm stop*
5) your pc now should use nvidia driver

I managed to get around the black screen of death but now  computer stops to error message when booting:

Ubuntu is running in low-graphics mode
The following error was encountered. :
> 
You may need to update your configuration to solve this.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Any help is greatly appreciated... just go easy on me, although I am willing to sink my teeth into the Linux world, I am after all a newb.

Thanks in advance for your help

---

### Post by DokterSun on 2010-03-03
Hello,

I've got a similar problem with my Nvidia chipset and it's causing trouble with the wireless. I'm using a network cable since end '09

I am using the same model laptop, the Aspire 7520G and i also got Ubuntu 9.10(64x) installed and got a GeForce 8600m G (ver. 185). As ethernet controller it has an "Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)"..

When I try to connect to an wireless network in 'System>Preferences>Network Connections>Wireless' it doesn't give me any signal. I've got ndiswrapper installed on my system, linux-backports-modules-intrepid-generic_2.6.27.17.21_amd64.deb drivers installed and tried ath5k and switched to older versions in 'System>Administration>Hardware Drivers' to try the Nvidia (ver. 173) but I booked no result.

When I want to take a look to the wlan settings in ifconfig command, there doesn't appear any wlan dialog at all as you can see below:
```

pelski@pelski-laptop:~/Desktop$ 

ifconfig                                                      
eth0      Link encap:Ethernet  HWaddr 00:1b:38:d3:00:74                                          
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0                         
          inet6 addr: fe80::21b:38ff:fed3:74/64 Scope:Link                                       
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                                     
          RX packets:14804 errors:0 dropped:0 overruns:0 frame:0                                 
          TX packets:14700 errors:0 dropped:0 overruns:0 carrier:0                               
          collisions:0 txqueuelen:1000                                                           
          RX bytes:8770754 (8.7 MB)  TX bytes:3406698 (3.4 MB)                                   
          Interrupt:28 Base address:0xa000                                                       

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0                            
          RX bytes:956 (956.0 B)  TX bytes:956 (956.0 B)       

virbr0    Link encap:Ethernet  HWaddr 36:46:58:6a:47:ab  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0                
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0             
          collisions:0 txqueuelen:0                                         
          RX bytes:0 (0.0 B)  TX bytes:6705 (6.7 KB)                        
pelski@pelski-laptop:~/Desktop$

```

The wireless drivers are installed in ndiswrapper trough 'System>Administration>Windows Wireless Drivers' but won't show up.
When I take a look in lspci -i to see if my network cards are installed I see my Atheros as you can see below

```
pelski@pelski-laptop:~/Desktop$ lspci && lspci -n
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)       
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)                 
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)   
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)          
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)    
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)                 
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)         
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)          
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)         
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)         
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)         
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration                                                                                   
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map              
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller          
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control    
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)                  
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)       
01:04.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)            
01:04.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)                      
02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M G] (rev a1)             
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
00:00.0 0500: 10de:0547 (rev a2)                                                                 
00:01.0 0601: 10de:0548 (rev a2)                                                                 
00:01.1 0c05: 10de:0542 (rev a2)                                                                 
00:01.2 0500: 10de:0541 (rev a2)                                                                 
00:01.3 0b40: 10de:0543 (rev a2)                                                                 
00:02.0 0c03: 10de:055e (rev a2)                                                                 
00:02.1 0c03: 10de:055f (rev a2)                                                                 
00:04.0 0c03: 10de:055e (rev a2)                                                                 
00:04.1 0c03: 10de:055f (rev a2)                                                                 
00:06.0 0101: 10de:0560 (rev a1)                                                                 
00:07.0 0403: 10de:055c (rev a1)                                                                 
00:08.0 0604: 10de:0561 (rev a2)                                                                 
00:09.0 0101: 10de:0550 (rev a2)                                                                 
00:0a.0 0200: 10de:054c (rev a2)                                                                 
00:0b.0 0604: 10de:0562 (rev a2)                                                                 
00:0c.0 0604: 10de:0563 (rev a2)                                                                 
00:0d.0 0604: 10de:0563 (rev a2)                                                                 
00:18.0 0600: 1022:1100                                                                          
00:18.1 0600: 1022:1101                                                                          
00:18.2 0600: 1022:1102                                                                          
00:18.3 0600: 1022:1103                                                                          
01:04.0 0c00: 1180:0832 (rev 05)                                                                 
01:04.1 0805: 1180:0822 (rev 22)                                                                 
01:04.2 0880: 1180:0592 (rev 12)                                                                 
01:04.3 0880: 1180:0852 (rev 12)                                                                 
02:00.0 0300: 10de:0428 (rev a1)                                                                 
05:00.0 0200: 168c:001c (rev 01)                           
pelski@pelski-laptop:~/Desktop$

```


I hope this post provides more information for debugging

---

