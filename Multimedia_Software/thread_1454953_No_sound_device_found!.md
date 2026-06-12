---
title: "No sound device found!"
date: 2010-04-15
forum: Multimedia Software
---

### Post by casper3 on 2010-04-15
I have installed a wrong driver few days ago from
[http://ubuntuforums.org/showthread.php?t=540296](http://ubuntuforums.org/showthread.php?t=540296)
```
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)
tar xvf alsa-driver-1.0.14.tar.bz2
./configure --with-oss=yes --with-cards=hda-intel
sudo make
sudo make install
sudo modprobe snd-hda-intel
/etc/init.d/alsasound restart
```Then it becomes sound-less = =''
aplay -l:
[SIZE=2]```
aplay: device_list:221: no soundcard found...
```[/SIZE]lspci -v:
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)                                                                   
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: bus master, fast devsel, latency 0                                   
        Memory at <unassigned> (32-bit, prefetchable)                               
        Capabilities: <access denied>                                               
        Kernel driver in use: agpgart-intel                                         
        Kernel modules: intel-agp                                                   

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)                                                             
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: bus master, fast devsel, latency 0                                   

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)                                                             
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: bus master, fast devsel, latency 0                                   

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)                                                                    
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: bus master, fast devsel, latency 0, IRQ 16                           
        Memory at e8000000 (32-bit, prefetchable) [size=128M]                       
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]                   
        I/O ports at 1800 [size=8]                                                  
        Capabilities: <access denied>                                               
        Kernel driver in use: i915                                                  
        Kernel modules: i915                                                        

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)                                                                           
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: bus master, fast devsel, latency 0                                   
        Memory at f0000000 (32-bit, prefetchable) [size=128M]                       
        Memory at e0080000 (32-bit, non-prefetchable) [size=512K]                   
        Capabilities: <access denied>                                               

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)                                                          
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: bus master, medium devsel, latency 0, IRQ 16                         
        I/O ports at 1820 [size=32]                                                 
        Kernel driver in use: uhci_hcd                                              

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)                                                          
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: bus master, medium devsel, latency 0, IRQ 19                         
        I/O ports at 1840 [size=32]                                                 
        Kernel driver in use: uhci_hcd                                              

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)                                                          
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: bus master, medium devsel, latency 0, IRQ 18                         
        I/O ports at 1860 [size=32]                                                 
        Kernel driver in use: uhci_hcd                                              

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)                                                          
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: bus master, medium devsel, latency 0, IRQ 23                         
        Memory at e0100000 (32-bit, non-prefetchable) [size=1K]                     
        Capabilities: <access denied>                                               
        Kernel driver in use: ehci_hcd                                              

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
        Flags: bus master, fast devsel, latency 0                     
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=64 
        I/O behind bridge: 00003000-00003fff                          
        Memory behind bridge: e0200000-e02fffff                       
        Prefetchable memory behind bridge: 30000000-33ffffff          
        Kernel modules: shpchp                                        

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)                                                                                   
        Flags: bus master, medium devsel, latency 0                                 
        Kernel modules: iTCO_wdt, intel-rng                                         

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])                                                      
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: bus master, medium devsel, latency 0, IRQ 18                         
        I/O ports at 01f0 [size=8]                                                  
        I/O ports at 03f4 [size=1]                                                  
        I/O ports at 0170 [size=8]                                                  
        I/O ports at 0374 [size=1]                                                  
        I/O ports at 1810 [size=16]                                                 
        Memory at 34000000 (32-bit, non-prefetchable) [size=1K]                     
        Kernel driver in use: ata_piix                                              

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)                                                                         
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: medium devsel, IRQ 5                                                 
        I/O ports at 1880 [size=32]                                                 
        Kernel modules: i2c-i801                                                    

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)                                             
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: bus master, medium devsel, latency 0, IRQ 17                         
        I/O ports at 1c00 [size=256]                                                
        I/O ports at 18c0 [size=64]                                                 
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]                    
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]                    
        Capabilities: <access denied>                                               
        Kernel driver in use: Intel ICH                                             
        Kernel modules: snd-intel8x0                                                

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)                                                                   
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: medium devsel, IRQ 17                                                
        I/O ports at 2400 [size=256]                                                
        I/O ports at 2000 [size=128]                                                
        Capabilities: <access denied>                                               
        Kernel modules: snd-intel8x0m                                               

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)                                                                             
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: bus master, medium devsel, latency 64, IRQ 16                        
        I/O ports at 3000 [size=256]                                                
        Memory at e0208800 (32-bit, non-prefetchable) [size=256]                    
        Capabilities: <access denied>                                               
        Kernel driver in use: 8139too                                               
        Kernel modules: epl, 8139too, 8139cp                                        

02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)                                                                     
        Subsystem: Hewlett-Packard Company Device 12fa                              
        Flags: bus master, fast devsel, latency 64, IRQ 18                          
        Memory at e0204000 (32-bit, non-prefetchable) [size=8K]                     
        Kernel driver in use: b43-pci-bridge                                        
        Kernel modules: ssb                                                         

02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Hewlett-Packard Company Device 3080                   
        Flags: bus master, medium devsel, latency 168, IRQ 20            
        Memory at e020a000 (32-bit, non-prefetchable) [size=4K]          
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176   
        Memory window 0: 30000000-33fff000 (prefetchable)                
        Memory window 1: 38000000-3bfff000                               
        I/O window 0: 00003400-000034ff                                  
        I/O window 1: 00003800-000038ff                                  
        16-bit legacy interface ports at 0001                            
        Kernel driver in use: yenta_cardbus                              
        Kernel modules: yenta_socket                                     

02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10)                                                                   
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: bus master, medium devsel, latency 64, IRQ 22                        
        Memory at e0208000 (32-bit, non-prefetchable) [size=2K]                     
        Memory at e0200000 (32-bit, non-prefetchable) [size=16K]                    
        Capabilities: <access denied>                                               
        Kernel driver in use: ohci1394                                              
        Kernel modules: firewire-ohci, ohci1394                                     

02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller                                                                             
        Subsystem: Hewlett-Packard Company Device 3080                              
        Flags: bus master, medium devsel, latency 64, IRQ 20                        
        Memory at e0206000 (32-bit, non-prefetchable) [size=8K]                     
        Capabilities: <access denied>
        Kernel driver in use: tifm_7xx1
        Kernel modules: tifm_7xx1

02:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
        Subsystem: Hewlett-Packard Company Device 3080
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at e0209400 (32-bit, non-prefetchable) [size=256]
        Memory at e0209000 (32-bit, non-prefetchable) [size=256]
        Memory at e0208c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci

```then I tried 
[SIZE=2]```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```[/SIZE]```
&
[SIZE=2]sudo apt-get install linux-sound-base alsa-base alsa-utils[/SIZE]
```[SIZE=2]
[/SIZE]but failed
I have also tried
[SIZE=2]```
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
```[/SIZE]```

[SIZE=2]sudo module-assistant a-i   alsa-source
[/SIZE]
```with the same result...
I'm  new to ubuntu, just knowing little about it.
You can ask for more information for my computer
How can I recover the sound ?

---

### Post by Yellow Pasque on 2010-04-15
Yeah, I wish a mod would edit the sound sticky and replace the very outdated commands for building ALSA with this link: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
That links to the ALSA upgrade script (which is current and well-tested), and is an easy way to properly build the latest ALSA from source.

---

### Post by casper3 on 2010-04-17
This works for me Thanks!

---

