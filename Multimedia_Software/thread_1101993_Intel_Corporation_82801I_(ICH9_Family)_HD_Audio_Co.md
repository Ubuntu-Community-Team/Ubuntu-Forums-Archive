---
title: "Intel Corporation 82801I (ICH9 Family) HD Audio Controller - sound greatly unreliable"
date: 2009-03-21
forum: Multimedia Software
---

### Post by soule on 2009-03-21
Hello,

I am having trouble with sound on Kubuntu 8.10. On some rare occassions I can here one oof my music clips, but as aforementioned that hardly ever occurs. I am not much of a newbie; I can trouble-shoot and know all the basics, but am not a master. EDIT: Also, I can hear sounds from my favorite JAVA game and the welcome sounds.
I try to play some sounds under amarok and it fails. I even tried updating to the latest version.

I ran the command "sudo lspci -v", and it returns with this; ```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)                                                                       
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, fast devsel, latency 0                               
        Capabilities: [e0] Vendor Specific Information <?>                      
        Kernel driver in use: agpgart-intel                                     
        Kernel modules: intel-agp                                               

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)                                                  
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, fast devsel, latency 0, IRQ 16                       
        Memory at fe800000 (32-bit, non-prefetchable) [size=512K]               
        I/O ports at bc00 [size=8]                                              
        Memory at d0000000 (32-bit, prefetchable) [size=256M]                   
        Memory at fe700000 (32-bit, non-prefetchable) [size=1M]                 
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-                                                                         
        Capabilities: [d0] Power Management version 2                           

00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)                                                                    
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, fast devsel, latency 0, IRQ 221                      
        Memory at fe8c0000 (32-bit, non-prefetchable) [size=128K]               
        Memory at fe8fe000 (32-bit, non-prefetchable) [size=4K]                 
        I/O ports at c000 [size=32]                                             
        Capabilities: [c8] Power Management version 2                           
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+                                                                         
        Capabilities: [e0] PCIe advanced features <?>                           
        Kernel driver in use: e1000e                                            
        Kernel modules: e1000e                                                  

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)                                                                  
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, medium devsel, latency 0, IRQ 16                     
        I/O ports at c080 [size=32]                                             
        Capabilities: [50] PCIe advanced features <?>                           
        Kernel driver in use: uhci_hcd                                          
        Kernel modules: uhci-hcd                                                

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)                                                                  
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, medium devsel, latency 0, IRQ 21                     
        I/O ports at c400 [size=32]                                             
        Capabilities: [50] PCIe advanced features <?>                           
        Kernel driver in use: uhci_hcd                                          
        Kernel modules: uhci-hcd                                                

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)                                                    
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, medium devsel, latency 0, IRQ 18                     
        Memory at fe8ff400 (32-bit, non-prefetchable) [size=1K]                 
        Capabilities: [50] Power Management version 2                           
        Capabilities: [58] Debug port: BAR=1 offset=00a0                        
        Capabilities: [98] PCIe advanced features <?>                           
        Kernel driver in use: ehci_hcd                                          
        Kernel modules: ehci-hcd                                                

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)                                                                       
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, fast devsel, latency 0, IRQ 22                       
        Memory at fe8f8000 (64-bit, non-prefetchable) [size=16K]                
        Capabilities: [50] Power Management version 2                           
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-                                                                         
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00     
        Capabilities: [100] Virtual Channel <?>                                 
        Capabilities: [130] Root Complex Link <?>                               
        Kernel driver in use: HDA Intel                                         
        Kernel modules: snd-hda-intel                                           

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)                                                                          
        Flags: bus master, fast devsel, latency 0                               
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0            
        Capabilities: [40] Express Root Port (Slot+), MSI 00                    
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+                                                                         
        Capabilities: [90] Subsystem: Hewlett-Packard Company Device 2a5d       
        Capabilities: [a0] Power Management version 2                           
        Capabilities: [100] Virtual Channel <?>                                 
        Capabilities: [180] Root Complex Link <?>                               
        Kernel driver in use: pcieport-driver                                   
        Kernel modules: shpchp                                                  

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)                                                                          
        Flags: bus master, fast devsel, latency 0                               
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0            
        Memory behind bridge: fea00000-febfffff                                 
        Capabilities: [40] Express Root Port (Slot+), MSI 00                    
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+                                                                         
        Capabilities: [90] Subsystem: Hewlett-Packard Company Device 2a5d       
        Capabilities: [a0] Power Management version 2                           
        Capabilities: [100] Virtual Channel <?>                                 
        Capabilities: [180] Root Complex Link <?>                               
        Kernel driver in use: pcieport-driver                                   
        Kernel modules: shpchp                                                  

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)                                                                  
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, medium devsel, latency 0, IRQ 23                     
        I/O ports at c480 [size=32]                                             
        Capabilities: [50] PCIe advanced features <?>                           
        Kernel driver in use: uhci_hcd                                          
        Kernel modules: uhci-hcd                                                

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)                                                                  
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, medium devsel, latency 0, IRQ 19                     
        I/O ports at c800 [size=32]                                             
        Capabilities: [50] PCIe advanced features <?>                           
        Kernel driver in use: uhci_hcd                                          
        Kernel modules: uhci-hcd                                                

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)                                                                  
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, medium devsel, latency 0, IRQ 18                     
        I/O ports at c880 [size=32]                                             
        Capabilities: [50] PCIe advanced features <?>                           
        Kernel driver in use: uhci_hcd                                          
        Kernel modules: uhci-hcd                                                

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)                                                                  
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, medium devsel, latency 0, IRQ 16                     
        I/O ports at cc00 [size=32]                                             
        Capabilities: [50] PCIe advanced features <?>                           
        Kernel driver in use: uhci_hcd                                          
        Kernel modules: uhci-hcd                                                

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)                                                    
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, medium devsel, latency 0, IRQ 23                     
        Memory at fe8ff800 (32-bit, non-prefetchable) [size=1K]                 
        Capabilities: [50] Power Management version 2                           
        Capabilities: [58] Debug port: BAR=1 offset=00a0                        
        Capabilities: [98] PCIe advanced features <?>                           
        Kernel driver in use: ehci_hcd                                          
        Kernel modules: ehci-hcd                                                

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01)
        Flags: bus master, fast devsel, latency 0                           
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32       
        I/O behind bridge: 0000e000-0000efff                                
        Memory behind bridge: fe900000-fe9fffff                             
        Capabilities: [50] Subsystem: Hewlett-Packard Company Device 2a5d   

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)                                                                         
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, medium devsel, latency 0                             
        Capabilities: [e0] Vendor Specific Information <?>                      
        Kernel modules: iTCO_wdt                                                

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])                        
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19              
        I/O ports at 01f0 [size=8]                                              
        I/O ports at 03f4 [size=1]                                              
        I/O ports at 0170 [size=8]                                              
        I/O ports at 0374 [size=1]                                              
        I/O ports at ff90 [size=16]                                             
        I/O ports at ffa0 [size=16]                                             
        Capabilities: [70] Power Management version 3                           
        Capabilities: [b0] PCIe advanced features <?>                           
        Kernel driver in use: ata_piix                                          
        Kernel modules: ata_piix                                                

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
        Subsystem: Hewlett-Packard Company Device 2a5d                         
        Flags: medium devsel, IRQ 3                                            
        Memory at fe8ffc00 (64-bit, non-prefetchable) [size=256]               
        I/O ports at 0400 [size=32]                                            
        Kernel modules: i2c-i801                                               

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])                               
        Subsystem: Hewlett-Packard Company Device 2a5d                          
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19              
        I/O ports at dc00 [size=8]                                              
        I/O ports at d880 [size=4]                                              
        I/O ports at d800 [size=8]                                              
        I/O ports at d480 [size=4]                                              
        I/O ports at d400 [size=16]                                             
        I/O ports at d080 [size=16]
        Capabilities: [70] Power Management version 3
        Capabilities: [b0] PCIe advanced features <?>
        Kernel driver in use: ata_piix
        Kernel modules: ata_piix

01:00.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
        Subsystem: Conexant Systems, Inc. Device 200c
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at fe9e0000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at ec00 [size=8]
        Capabilities: [40] Power Management version 2

01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10)
        Subsystem: Hewlett-Packard Company Device 2a5d
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at fe9ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Kernel driver in use: ohci1394
        Kernel modules: ohci1394

02:00.0 Multimedia video controller: Conexant Systems, Inc. Device 8880 (rev 0f)
        Subsystem: Hauppauge computer works Inc. Device 7801
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
        Capabilities: [40] Express Endpoint, MSI 00
        Capabilities: [80] Power Management version 2
        Capabilities: [90] Vital Product Data <?>
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0Enable-
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [200] Virtual Channel <?>
        Kernel driver in use: cx23885
        Kernel modules: cx23885 
```

I then ran the command "aplay -l", and this was my result;
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Anyhow, thanks for reading, and any assistance would greatly be to my pleasure.

-Soule

---

### Post by soule on 2009-03-21
bump bump

---

### Post by benorner on 2009-03-24
these two links offer alot of information:
[http://ubuntuforums.org/showthread.php?t=843012]("http://ubuntuforums.org/showthread.php?t=843012")
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound")

but my sound issues with 8.10 where ultimately resolved with this post by stego s aurus:

"Just before I went to sleep last night, I found some Other settings by searching for "options snd-hda-intel"... and Someone else had some additional settings that I added to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1 

(add to the bottom, save and reboot)
also make sure that sound preferences are set to either alsa or pulse audio

seems like ICH9 is simply not well supported by ALSA. Hopefully the above will help, but if not, then you might have some luck upgrading to alsa 1.0.19. 

let us know how it goes

---

### Post by Turbomaniac_7 on 2009-03-29
I had this problem that the first .5 sec of the sound being played in an infinite loop. (HP Laptop, ICH9 HDA Audio)

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

These three lines solved that problem.

Thank you benorner

---

### Post by benorner on 2009-03-29
glad to be of some service

---

