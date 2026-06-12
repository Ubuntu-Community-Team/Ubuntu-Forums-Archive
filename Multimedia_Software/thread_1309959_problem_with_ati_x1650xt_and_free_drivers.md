---
title: "problem with ati x1650xt and free drivers"
date: 2009-11-01
forum: Multimedia Software
---

### Post by mcfly2309 on 2009-11-01
hello, i just installed kubuntu 9.10 and i can only use it with the vesa driver. Also, the live cd wouldn't start except on safe-graphics mode. I do everything in this guide to use the "ati" driver ([https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)), but the screen stays blank when the os is booting. The propietary drivers for my card (ver 9.3) won't install so i have to use the open source ones. Anyone have a solution?

---

### Post by psidrum on 2009-11-01
have the same problem too i have x1600, old driver stopped working, cant use 3d desktop

---

### Post by epek on 2009-11-01
1 see man 4 radeon, probably your config has "radeonhd"?
2 load the framebuffer radeonfb -> add to /etc/modules

3 Are you an the right platform? linux-generic or linux-386 - probably the chipset drivers pcie or the agp brigde are not loaded, when using the "wrong" kernel ...

4 reboot and try.

post you lspci -v output
what does /var/log/Xorg.0.log say?

---

### Post by mcfly2309 on 2009-11-01
> **epek said:**
> 
3 Are you an the right platform? linux-generic or linux-386 - probably the chipset drivers pcie or the agp brigde are not loaded, when using the "wrong" kernel ...

This must be it, cos i have an amd64 processor. Does this mean i have to install ubuntu for amd64 from scratch?¿ :/ well i will try the live cd.

$ lspci -v
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 7252
        Flags: bus master, 66MHz, fast devsel, latency 0         
        Capabilities: <access denied>                            

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 7252      
        Flags: 66MHz, fast devsel                                      

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 7252      
        Flags: 66MHz, fast devsel                                      

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 7252      
        Flags: 66MHz, fast devsel                                      

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 7252      
        Flags: bus master, 66MHz, fast devsel, latency 0               

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 7252
        Flags: bus master, 66MHz, fast devsel, latency 0         
        Capabilities: <access denied>                            

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 7252      
        Flags: 66MHz, fast devsel                                      

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 7252      
        Flags: 66MHz, fast devsel                                      

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
        Flags: bus master, fast devsel, latency 0                     
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0  
        Capabilities: <access denied>                                 
        Kernel driver in use: pcieport-driver                         
        Kernel modules: shpchp                                                                                                                                                                           
                                                                                                                                                                                                         
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)                                                                                                                                   
        Flags: bus master, fast devsel, latency 0                                                                                                                                                        
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0                                                                                                                                     
        I/O behind bridge: 0000e000-0000efff                                                                                                                                                             
        Memory behind bridge: feb00000-febfffff                                                                                                                                                          
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff                                                                                                                             
        Capabilities: <access denied>                                                                                                                                                                    
        Kernel driver in use: pcieport-driver                                                                                                                                                            
        Kernel modules: shpchp                                                                                                                                                                           

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 7252
        Flags: bus master, 66MHz, fast devsel, latency 0         
        Capabilities: <access denied>                            

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: Micro-Star International Co., Ltd. Device 7252
        Flags: bus master, 66MHz, fast devsel, latency 0         

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: Micro-Star International Co., Ltd. Device 7252
        Flags: 66MHz, fast devsel, IRQ 5                         
        I/O ports at 5000 [size=64]                              
        I/O ports at 6000 [size=64]                              
        Capabilities: <access denied>                            
        Kernel driver in use: nForce2_smbus                      
        Kernel modules: i2c-nforce2                              

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
        Subsystem: Micro-Star International Co., Ltd. Device 7252                    
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21                     
        Memory at feabe000 (32-bit, non-prefetchable) [size=4K]                      
        Capabilities: <access denied>                                                
        Kernel driver in use: ohci_hcd                                               

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
        Subsystem: Micro-Star International Co., Ltd. Device 7252                    
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23                     
        Memory at feabfc00 (32-bit, non-prefetchable) [size=256]                     
        Capabilities: <access denied>                                                
        Kernel driver in use: ehci_hcd                                               

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Device 7252                           
        Flags: bus master, 66MHz, fast devsel, latency 0                                    
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]         
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]         
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]         
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]         
        I/O ports at ffa0 [size=16]                                                         
        Capabilities: <access denied>                                                       
        Kernel driver in use: pata_amd                                                      

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Device 7252                                             
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22                                              
        I/O ports at d800 [size=8]                                                                            
        I/O ports at d480 [size=4]                                                                            
        I/O ports at d400 [size=8]                                                                            
        I/O ports at d080 [size=4]                                                                            
        I/O ports at d000 [size=16]                                                                           
        Memory at feabd000 (32-bit, non-prefetchable) [size=4K]                                               
        Capabilities: <access denied>                                                                         
        Kernel driver in use: sata_nv                                                                         

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
        Flags: bus master, 66MHz, fast devsel, latency 0                     
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=64        
        Capabilities: <access denied>                                        

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 7252
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at feab8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: Micro-Star International Co., Ltd. Device 7252
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at feabc000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at cc00 [size=8]
        Capabilities: <access denied>
        Kernel driver in use: forcedeth
        Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>
        Kernel driver in use: k8temp
        Kernel modules: k8temp

02:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 XT (Primary) (PCIE) (rev 9a)
        Subsystem: ASUSTeK Computer Inc. Device 0184
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at febe0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at e000 [size=256]
        Expansion ROM at febc0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel modules: radeon

02:00.1 Display controller: ATI Technologies Inc Radeon X1650 XT (Secondary) (PCIE) (rev 9a)
        Subsystem: ASUSTeK Computer Inc. Device 0185
        Flags: bus master, fast devsel, latency 0
        Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

---

### Post by mcfly2309 on 2009-11-02
hello, well i tried kubuntu amd64 live cd and it was the same thing, only "safe-graphics" work.

i have tried writing both "ati" and "radeon" in xorg.conf, but never "radeonhd" cos that wouldn't be right, my card is supposedly supported by "radeon" driver.

about loading the radeonfb module, how do i do that? and what is that module? :P

---

### Post by mcfly2309 on 2009-11-03
any ideas?

---

