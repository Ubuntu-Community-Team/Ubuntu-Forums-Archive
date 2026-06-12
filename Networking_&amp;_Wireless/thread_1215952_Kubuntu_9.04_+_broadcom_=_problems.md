---
title: "Kubuntu 9.04 + broadcom = problems"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by walruspanzer on 2009-07-17
Maybe a little over my head but I am attempting to install Broadcom STA drivers from their website - as kubuntu 9.04 won't recognize the wireless card in my Compaq AMD64 Presario. I followed the README file on the [Broadcom website]("http://www.broadcom.com/support/802.11/linux_sta.php") to no avail so I'm following this [step by step tutorial]("http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61"). I once again get caught up at step 6. 

```

satan@satan-laptop:~/hybrid$ uname -r
2.6.28-11-generic

satan@satan-laptop:~/hybrid$ sudo make -C /lib/modules/2.6.28-11-generic/build M='pwn' clean
make: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
scripts/Makefile.clean:17: /usr/src/linux-headers-2.6.28-11-generic/pwn/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.28-11-generic/pwn/Makefile'.  Stop.
make: *** [_clean_pwn] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'

```I get the same result if I try removing the clean command at the end as well - which is step 7. I'm trying to manually install the drivers because the restricted hardware program doesn't see my Wireless card.

Here is more information about my system. 

```
 satan@satan-laptop:~/hybrid$ lspci
 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
 00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
 00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
 00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
 00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
 00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)         
 00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
 00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
 00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)  
 00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)  
 00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
 00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)                          
 00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)                           
 00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)                                     
 00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)                                
 00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)                   
 00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)                   
 00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)                               
 00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)             
 00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)                           
 00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)              
 00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)                      
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map                             
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller                         
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control                   
  

satan@satan-laptop:~/hybrid$ sudo ifconfig                                                                      
 [sudo] password for satan:                                                                                      
 eth0      Link encap:Ethernet  HWaddr 00:1b:24:d0:01:89                                                         
           UP BROADCAST MULTICAST  MTU:1500  Metric:1                                                            
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0                                                    
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                                                  
           collisions:0 txqueuelen:1000                                                                          
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)                                                                
           Interrupt:20 Base address:0x6000                                                                      
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host      
           UP LOOPBACK RUNNING  MTU:16436  Metric:1                                                                                                                                   
           RX packets:140 errors:0 dropped:0 overruns:0 frame:0                                                                                                                       
           TX packets:140 errors:0 dropped:0 overruns:0 carrier:0                                                                                                                     
           collisions:0 txqueuelen:0                                                                                                                                                 
           RX bytes:10328 (10.3 KB)  TX bytes:10328 (10.3 KB)                                                                                                                         
 

 satan@satan-laptop:~/hybrid$ lshw  
 WARNING: you should run this program as super-user.
 satan-laptop                                        
     description: Computer                           
     width: 64 bits                                  
     capabilities: vsyscall64 vsyscall32             
   *-core                                            
        description: Motherboard                     
        physical id: 0                               
      *-memory:0                                     
           description: System memory                
           physical id: 1                            
           size: 959MiB                              
      *-cpu                                          
           product: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55
           vendor: Advanced Micro Devices [AMD]                    
           physical id: 4                                          
           bus info: cpu@0                                         
           size: 1800MHz                                           
           capacity: 1800MHz                                       
           width: 64 bits                                          
           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq                                                                                  
      *-memory:1 UNCLAIMED                                                                                                                                                           
           description: RAM memory                                                                                                                                                   
           product: C51 Host Bridge                                                                                                                                                  
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 0                                                                                                                                                            
           bus info: pci@0000:00:00.0                                                                                                                                                
           version: a2                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz (15.2ns)                                                                                                                                                     
           capabilities: bus_master cap_list                                                                                                                                          
           configuration: latency=0                                                                                                                                                  
      *-memory:2 UNCLAIMED                                                                                                                                                           
           description: RAM memory                                                                                                                                                   
           product: C51 Memory Controller 0                                                                                                                                           
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 0.1                                                                                                                                                          
           bus info: pci@0000:00:00.1                                                                                                                                                
           version: a2                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz (15.2ns)                                                                                                                                                     
           configuration: latency=0                                                                                                                                                  
      *-memory:3 UNCLAIMED                                                                                                                                                           
           description: RAM memory                                                                                                                                                   
           product: C51 Memory Controller 1                                                                                                                                           
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 0.2                                                                                                                                                          
           bus info: pci@0000:00:00.2                                                                                                                                                
           version: a2                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz (15.2ns)                                                                                                                                                     
           configuration: latency=0                                                                                                                                                  
      *-memory:4 UNCLAIMED                                                                                                                                                           
           description: RAM memory                                                                                                                                                   
           product: C51 Memory Controller 5                                                                                                                                           
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 0.3                                                                                                                                                          
           bus info: pci@0000:00:00.3                                                                                                                                                
           version: a2                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz (15.2ns)                                                                                                                                                     
           configuration: latency=0                                                                                                                                                  
      *-memory:5 UNCLAIMED                                                                                                                                                           
           description: RAM memory                                                                                                                                                   
           product: C51 Memory Controller 4                                                                                                                                           
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 0.4                                                                                                                                                          
           bus info: pci@0000:00:00.4                                                                                                                                                
           version: a2                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz (15.2ns)                                                                                                                                                     
           capabilities: bus_master                                                                                                                                                  
           configuration: latency=0                                                                                                                                                  
      *-memory:6 UNCLAIMED                                                                                                                                                           
           description: RAM memory                                                                                                                                                   
           product: C51 Host Bridge                                                                                                                                                  
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 0.5                                                                                                                                                          
           bus info: pci@0000:00:00.5                                                                                                                                                
           version: a2                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz (15.2ns)                                                                                                                                                     
           capabilities: bus_master cap_list                                                                                                                                          
           configuration: latency=0                                                                                                                                                  
      *-memory:7 UNCLAIMED                                                                                                                                                           
           description: RAM memory                                                                                                                                                   
           product: C51 Memory Controller 3                                                                                                                                           
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 0.6                                                                                                                                                          
           bus info: pci@0000:00:00.6                                                                                                                                                
           version: a2                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz (15.2ns)                                                                                                                                                     
           configuration: latency=0                                                                                                                                                  
      *-memory:8 UNCLAIMED                                                                                                                                                           
           description: RAM memory                                                                                                                                                   
           product: C51 Memory Controller 2                                                                                                                                           
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 0.7                                                                                                                                                          
           bus info: pci@0000:00:00.7                                                                                                                                                
           version: a2                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz (15.2ns)                                                                                                                                                     
           configuration: latency=0                                                                                                                                                  
      *-pci:0                                                                                                                                                                        
           description: PCI bridge                                                                                                                                                   
           product: C51 PCI Express Bridge                                                                                                                                            
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 2                                                                                                                                                            
           bus info: pci@0000:00:02.0                                                                                                                                                
           version: a1                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 33MHz                                                                                                                                                              
           capabilities: pci bus_master cap_list                                                                                                                                      
           configuration: driver=pcieport-driver                                                                                                                                      
      *-pci:1                                                                                                                                                                        
           description: PCI bridge                                                                                                                                                   
           product: C51 PCI Express Bridge                                                                                                                                            
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 3                                                                                                                                                            
           bus info: pci@0000:00:03.0                                                                                                                                                
           version: a1                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 33MHz                                                                                                                                                              
           capabilities: pci bus_master cap_list                                                                                                                                      
           configuration: driver=pcieport-driver                                                                                                                                      
      *-display UNCLAIMED                                                                                                                                                            
           description: VGA compatible controller                                                                                                                                     
           product: MCP51 PCI-X GeForce Go 6100                                                                                                                                       
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 5                                                                                                                                                            
           bus info: pci@0000:00:05.0                                                                                                                                                
           version: a2                                                                                                                                                               
           width: 64 bits                                                                                                                                                            
           clock: 66MHz                                                                                                                                                              
           capabilities: bus_master cap_list                                                                                                                                          
           configuration: latency=0                                                                                                                                                  
      *-memory:9 UNCLAIMED                                                                                                                                                           
           description: RAM memory                                                                                                                                                   
           product: MCP51 Host Bridge                                                                                                                                                
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 9                                                                                                                                                            
           bus info: pci@0000:00:09.0                                                                                                                                                
           version: a2                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz (15.2ns)                                                                                                                                                     
           capabilities: bus_master cap_list                                                                                                                                          
           configuration: latency=0                                                                                                                                                  
      *-isa                                                                                                                                                                          
           description: ISA bridge                                                                                                                                                   
           product: MCP51 LPC Bridge                                                                                                                                                 
           vendor: nVidia Corporation                                                                                                                                                
           physical id: a                                                                                                                                                            
           bus info: pci@0000:00:0a.0                                                                                                                                                
           version: a3                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz                                                                                                                                                              
           capabilities: isa bus_master                                                                                                                                              
           configuration: latency=0                                                                                                                                                  
      *-serial                                                                                                                                                                       
           description: SMBus                                                                                                                                                        
           product: MCP51 SMBus                                                                                                                                                      
           vendor: nVidia Corporation                                                                                                                                                
           physical id: a.1                                                                                                                                                          
           bus info: pci@0000:00:0a.1                                                                                                                                                
           version: a3                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz                                                                                                                                                              
           capabilities: cap_list                                                                                                                                                    
           configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2                                                                                                           
      *-processor UNCLAIMED                                                                                                                                                          
           description: Co-processor                                                                                                                                                 
           product: MCP51 PMU                                                                                                                                                        
           vendor: nVidia Corporation                                                                                                                                                
           physical id: a.3                                                                                                                                                          
           bus info: pci@0000:00:0a.3                                                                                                                                                
           version: a3                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz                                                                                                                                                              
           capabilities: bus_master                                                                                                                                                  
           configuration: latency=0 maxlatency=1 mingnt=3                                                                                                                             
      *-usb:0                                                                                                                                                                        
           description: USB Controller                                                                                                                                               
           product: MCP51 USB Controller                                                                                                                                             
           vendor: nVidia Corporation                                                                                                                                                
           physical id: b                                                                                                                                                            
           bus info: pci@0000:00:0b.0                                                                                                                                                
           version: a3                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz                                                                                                                                                              
           capabilities: bus_master cap_list                                                                                                                                          
           configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3                                                                                                             
      *-usb:1                                                                                                                                                                        
           description: USB Controller                                                                                                                                               
           product: MCP51 USB Controller                                                                                                                                             
           vendor: nVidia Corporation                                                                                                                                                
           physical id: b.1                                                                                                                                                          
           bus info: pci@0000:00:0b.1                                                                                                                                                
           version: a3                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz                                                                                                                                                              
           capabilities: bus_master cap_list                                                                                                                                          
           configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd                                                                                             
      *-ide:0                                                                                                                                                                        
           description: IDE interface                                                                                                                                                
           product: MCP51 IDE                                                                                                                                                        
           vendor: nVidia Corporation                                                                                                                                                
           physical id: d                                                                                                                                                            
           bus info: pci@0000:00:0d.0                                                                                                                                                
           version: f1                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz                                                                                                                                                              
           capabilities: ide bus_master cap_list                                                                                                                                      
           configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3                                                                                                             
      *-ide:1                                                                                                                                                                        
           description: IDE interface                                                                                                                                                
           product: MCP51 Serial ATA Controller                                                                                                                                       
           vendor: nVidia Corporation                                                                                                                                                
           physical id: e                                                                                                                                                            
           bus info: pci@0000:00:0e.0                                                                                                                                                
           version: f1                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz                                                                                                                                                              
           capabilities: ide bus_master cap_list                                                                                                                                      
           configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv                                                                                              
      *-pci:2                                                                                                                                                                        
           description: PCI bridge                                                                                                                                                   
           product: MCP51 PCI Bridge                                                                                                                                                 
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 10                                                                                                                                                           
           bus info: pci@0000:00:10.0                                                                                                                                                
           version: a2                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz                                                                                                                                                              
           capabilities: pci bus_master cap_list                                                                                                                                      
      *-multimedia                                                                                                                                                                   
           description: Audio device                                                                                                                                                 
           product: MCP51 High Definition Audio                                                                                                                                       
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 10.1                                                                                                                                                         
           bus info: pci@0000:00:10.1                                                                                                                                                
           version: a2                                                                                                                                                               
           width: 32 bits                                                                                                                                                            
           clock: 66MHz                                                                                                                                                              
           capabilities: bus_master cap_list                                                                                                                                          
           configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel                                                                                       
      *-bridge                                                                                                                                                                       
           description: Ethernet interface                                                                                                                                            
           product: MCP51 Ethernet Controller                                                                                                                                         
           vendor: nVidia Corporation                                                                                                                                                
           physical id: 14                                                                                                                                                           
           bus info: pci@0000:00:14.0                                                                                                                                                
           logical name: eth0                                                                                                                                                        
           version: a3                                                                                                                                                               
           serial: 00:1b:24:d0:01:89                                                                                                                                                 
           width: 32 bits                                                                                                                                                            
           clock: 66MHz                                                                                                                                                              
           capabilities: bridge bus_master cap_list ethernet physical                                                                                                                 
           configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes                                           
      *-pci:3                                                                                                                                                                        
           description: Host bridge                                                                                                                                                  
           product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration                                                                                                     
           vendor: Advanced Micro Devices [AMD]
           physical id: 100
           bus info: pci@0000:00:18.0
           version: 00
           width: 32 bits
           clock: 33MHz
      *-pci:4
           description: Host bridge
           product: K8 [Athlon64/Opteron] Address Map
           vendor: Advanced Micro Devices [AMD]
           physical id: 101
           bus info: pci@0000:00:18.1
           version: 00
           width: 32 bits
           clock: 33MHz
      *-pci:5
           description: Host bridge
           product: K8 [Athlon64/Opteron] DRAM Controller
           vendor: Advanced Micro Devices [AMD]
           physical id: 102
           bus info: pci@0000:00:18.2
           version: 00
           width: 32 bits
           clock: 33MHz
      *-pci:6
           description: Host bridge
           product: K8 [Athlon64/Opteron] Miscellaneous Control
           vendor: Advanced Micro Devices [AMD]
           physical id: 103
           bus info: pci@0000:00:18.3
           version: 00
           width: 32 bits
           clock: 33MHz
           configuration: driver=k8temp module=k8temp
   *-network DISABLED
        description: Ethernet interface
        physical id: 1
        logical name: pan0
        serial: 66:3b:a6:df:db:93
        capabilities: ethernet physical
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
 
```All of this is off a fresh install. The wireless is such as hassle but I think there are even more drivers to load afterwards. Some helpful insight would be awesome. Thanks in advance

---

### Post by Ayuthia on 2009-07-17
If lspci does not show your wireless card, it usually means hardware problems.  Are you able to see and use your wireless card in Windows?

---

### Post by walruspanzer on 2009-07-17
Currently no windows is installed, had Vista long ago. I installed first ubuntu then kubuntu after failing to find my windows CD when I had all kinds of viruses and etc. Installed ubuntu 8.04 a few months ago - wireless worked great. did a fresh install of 9.04 a couple weeks ago and there is no wireless capability at all. I hope its not a hardware problem! :-( Also I appreciate your response, Thanks very much!

---

### Post by Ayuthia on 2009-07-17
You might try to see if you have another liveCD available and see if your card shows up.

By the way, the message that you are getting in Step 6 with the clean, that is ok.  It just means that you have not tried compiling the code before.

---

### Post by walruspanzer on 2009-07-17
I tried 8.04LTR. Dapper, regular intrepid, and of course ubuntu and kubuntu 9.04 - none of them are interfacing with my wireless device. Only in the live version of kubuntu Isaw it under restricted devices but wouldn't activate it. Once I installed kubuntu any reference in  Jockey to it or the Nvidia drivers was gone. I guess it is a hardware problem, I will make another attempt to find or burn a new windows CD to make sure then post the results here - thanks a bunch!

---

