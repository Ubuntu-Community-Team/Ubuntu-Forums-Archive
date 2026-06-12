---
title: "Is the Intel 82801CA ICH3 supported by ALSA?"
date: 2009-03-25
forum: Multimedia Software
---

### Post by Julian David Pitt on 2009-03-25
Can anybody please tell me if the above sound card is supported as I cannot see it listed on the Alsa Project web site. I have lost all application sound but I get hear a bleep when the system boots up. I have tried all the options in "System, Preferences,Sound" but no joy at all. I have worked through the Sticky thread and aplay -l gives me ```
julian@Hardy:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
lspci -v gives me 
```
julian@Hardy:~$ lspci -v                                    
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)                                           
        Subsystem: IBM Device 021d                          
        Flags: bus master, fast devsel, latency 0           
        Memory at d0000000 (32-bit, prefetchable) [size=256M]                                                           
        Capabilities: <access denied>                       
        Kernel driver in use: agpgart-intel                 
        Kernel modules: intel-agp                           

00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)                                             
        Flags: bus master, 66MHz, fast devsel, latency 96   
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64                                                   
        Memory behind bridge: c0100000-c01fffff             
        Prefetchable memory behind bridge: e0000000-ebffffff
        Kernel modules: shpchp                              

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)                                        
        Subsystem: IBM Device 0220                          
        Flags: bus master, medium devsel, latency 0, IRQ 11 
        I/O ports at 1800 [size=32]                         
        Kernel driver in use: uhci_hcd                      
        Kernel modules: uhci-hcd                            

00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 01)                                        
        Subsystem: IBM Device 0220                          
        Flags: bus master, medium devsel, latency 0, IRQ 11 
        I/O ports at 1820 [size=32]                         
        Kernel driver in use: uhci_hcd                      
        Kernel modules: uhci-hcd                            

00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 01)                                        
        Subsystem: IBM Device 0220                          
        Flags: bus master, medium devsel, latency 0, IRQ 11 
        I/O ports at 1840 [size=32]                         
        Kernel driver in use: uhci_hcd                      
        Kernel modules: uhci-hcd                            

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)                                                  
        Flags: bus master, fast devsel, latency 0           
        Bus: primary=00, secondary=02, subordinate=08, sec-latency=64                                                   
        I/O behind bridge: 00002000-00006fff                
        Memory behind bridge: c0200000-cfffffff             
        Prefetchable memory behind bridge: f0000000-f7ffffff
        Kernel modules: shpchp                              

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)                                                
        Flags: bus master, medium devsel, latency 0         
        Kernel modules: iTCO_wdt, intel-rng                 

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01) (prog-if 8a [Master SecP PriP])          
        Subsystem: IBM Device 0220                          
        Flags: bus master, medium devsel, latency 0, IRQ 11 
        I/O ports at 01f0 [size=8]                          
        I/O ports at 03f4 [size=1]                          
        I/O ports at 0170 [size=8]                          
        I/O ports at 0374 [size=1]                          
        I/O ports at 1860 [size=16]                         
        Memory at 50001000 (32-bit, non-prefetchable) [size=1K]                                                         
        Kernel driver in use: ata_piix                      
        Kernel modules: ata_piix                            

00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)                                                  
        Subsystem: IBM Device 0220                          
        Flags: medium devsel, IRQ 5                         
        I/O ports at 1880 [size=32]                         
        Kernel modules: i2c-i801                            

[COLOR="Red"][COLOR="Red"]00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)                      
        Subsystem: IBM Device 0222                          
        Flags: bus master, medium devsel, latency 0, IRQ 5  
        I/O ports at 1c00 [size=256]                        
        I/O ports at 18c0 [size=64]                         
        Kernel driver in use: Intel ICH                     
        Kernel modules: snd-intel8x0                        
[/COLOR][/COLOR]
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)                                                
        Subsystem: IBM Device 01fc                          
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11                                                     
        Memory at c0100000 (32-bit, non-prefetchable) [size=512K]                                                       
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Memory at e0000000 (32-bit, prefetchable) [size=32M]
        [virtual] Expansion ROM at e2000000 [disabled] [size=64K]                                                       
        Capabilities: <access denied>                       
        Kernel modules: savagefb                            

02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller                                            
        Subsystem: IBM Device 023b                          
        Flags: bus master, medium devsel, latency 168, IRQ 11                                                           
        Memory at 50000000 (32-bit, non-prefetchable) [size=4K]                                                         
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176                                                  
        Memory window 0: f0000000-f3fff000 (prefetchable)   
        Memory window 1: c4000000-c7fff000                  
        I/O window 0: 00002000-000020ff                     
        I/O window 1: 00002400-000024ff                     
        16-bit legacy interface ports at 0001               
        Kernel driver in use: yenta_cardbus                 
        Kernel modules: yenta_socket                        

02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller                                            
        Subsystem: IBM Device 023b                          
        Flags: bus master, medium devsel, latency 168, IRQ 5
        Memory at 51000000 (32-bit, non-prefetchable) [size=4K]                                                         
        Bus: primary=02, secondary=07, subordinate=07, sec-latency=176                                                  
        Memory window 0: f4000000-f7fff000 (prefetchable)   
        Memory window 1: c8000000-cbfff000                  
        I/O window 0: 00002800-000028ff                     
        I/O window 1: 00002c00-00002cff                     
        16-bit legacy interface ports at 0001               
        Kernel driver in use: yenta_cardbus                 
        Kernel modules: yenta_socket                        

02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)                                                   
        Subsystem: AMBIT Microsystem Corp. Device 0410      
        Flags: bus master, medium devsel, latency 0, IRQ 11 
        Memory at c0201000 (32-bit, non-prefetchable) [size=256]                                                        
        I/O ports at 6440 [size=8]                          
        I/O ports at 6000 [size=256]                        
        Capabilities: <access denied>                       

02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)            
        Subsystem: IBM Device 0209                          
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at c0200000 (32-bit, non-prefetchable) [size=4K]                                                         
        I/O ports at 6400 [size=64]                         
        Capabilities: <access denied>                       
        Kernel driver in use: e100                          
        Kernel modules: e100, eepro100                      

03:00.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10)                                                       
        Subsystem: Belkin Device 0001                       
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at c4000000 (32-bit, non-prefetchable) [size=4K]                                                         
        Capabilities: <access denied>                       
        Kernel driver in use: ohci_hcd                      
        Kernel modules: ohci-hcd                            

03:00.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10)                                                       
        Subsystem: Belkin Device 1799                       
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at c4001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ohci_hcd
        Kernel modules: ohci-hcd

03:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20)
        Subsystem: Belkin Device 0002
        Flags: bus master, medium devsel, latency 68, IRQ 11
        Memory at c4002000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
        Kernel modules: ehci-hcd

07:00.0 Ethernet controller: Belkin Device 701f (rev 20)
        Subsystem: Belkin Device 701f
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 2800 [size=256]
        Memory at c8000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: rtl8180
        Kernel modules: rtl8180

julian@Hardy:~$

```
Could somebody possibly post screenshots of the ALSA mixer window as I am very confused as to what I should be seeing. When are the switches on for instance? Thanks in advance of any help.

---

### Post by bertolo on 2009-04-06
try this:
open volume control, preferences, enable all the xit there. put volume in max in all parameters.
then in switches choose headphones and disable the other two options below.
ps:select HDA intel drivers.
this was my solution when i had the same problem

---

