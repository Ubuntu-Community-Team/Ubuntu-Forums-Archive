---
title: "No sound after installing Ibex."
date: 2008-11-01
forum: Multimedia Software
---

### Post by kkilps on 2008-11-01
I have no sound after installing ibex. I have a via 82xx sound card. Here is from the terminal

kurt@ubuntu:~$ aplay -l
aplay: device_list:215: no soundcards found...
kurt@ubuntu:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Subsystem: Gateway 2000 Device 0216
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp

00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
	Flags: bus master, medium devsel, latency 0
	Kernel modules: via-agp

00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: d4000000-d4ffffff
	Prefetchable memory behind bridge: d0000000-d3ffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:0c.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Gateway 2000 Device 0216
	Flags: bus master, medium devsel, latency 168, IRQ 19
	Memory at 38000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: 34000000-37fff000
	I/O window 0: 00002000-000020ff
	I/O window 1: 00002400-000024ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

00:0c.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Gateway 2000 Device 0216
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at 38001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

00:0c.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
	Subsystem: Gateway 2000 Device 0216
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at 38002200 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at 2800 [size=256]
	Memory at 38002000 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>
	Kernel driver in use: rtl8180
	Kernel modules: rtl8180

00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Device 0216
	Flags: bus master, medium devsel, latency 64, IRQ 20
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 1c80 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_via
	Kernel modules: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: Gateway 2000 Device 0216
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at 1c00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: Gateway 2000 Device 0216
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at 1c20 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: Gateway 2000 Device 0216
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at 1c40 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: Gateway 2000 Device 0216
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at 1c60 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20)
	Subsystem: Gateway 2000 Device 0216
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at d5200000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
	Subsystem: Gateway 2000 Device 0216
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: i2c-viapro

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: Gateway 2000 Device 0216
	Flags: medium devsel, IRQ 7
	I/O ports at 1000 [size=256]
	Capabilities: <access denied>
	Kernel modules: snd-via82xx

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
	Subsystem: Gateway 2000 Device 0216
	Flags: medium devsel, IRQ 7
	I/O ports at 1400 [size=256]
	Capabilities: <access denied>
	Kernel modules: snd-via82xx-modem

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
	Subsystem: Gateway 2000 Device 0216
	Flags: bus master, medium devsel, latency 16, IRQ 23
	I/O ports at 1800 [size=256]
	Memory at d5200400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-rhine
	Kernel modules: via-rhine

01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)
	Subsystem: Gateway 2000 Device 0216
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d0000000 (32-bit, prefetchable) [size=64M]
	Memory at d4000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>

---

### Post by tlongren on 2008-11-03
I've got this exact problem, did you ever figure out how to fix this?

---

### Post by silas216 on 2008-11-05
Had the same problem after upgrading to Ibex.

> steven@steven-desktop:~$ lspci -v             
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)                                                                       
        Flags: bus master, fast devsel, latency 0                               
        Memory at f8000000 (32-bit, prefetchable) [size=64M]                    
        Capabilities: <access denied>                                           
        Kernel driver in use: agpgart-intel                                     
        Kernel modules: intel-agp                                               

00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)                                                                         
        Flags: bus master, 66MHz, fast devsel, latency 32                       
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32           
        Memory behind bridge: fc900000-fe9fffff                                 
        Prefetchable memory behind bridge: e4600000-f46fffff                    
        Kernel modules: shpchp                                                  

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
        Flags: bus master, fast devsel, latency 0              
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff                         
        Memory behind bridge: fea00000-feafffff                      
        Prefetchable memory behind bridge: f4700000-f47fffff         
        Kernel modules: shpchp                                       

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
        Flags: bus master, medium devsel, latency 0                    
        Kernel modules: iTCO_wdt, intel-rng                            

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05) (prog-if 80 [Master])                                                             
        Subsystem: Dell Device 0115                                             
        Flags: bus master, medium devsel, latency 0                             
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]                                                                             
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]                                                                             
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]                                                                             
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]                                                                             
        I/O ports at ffa0 [size=16]                                             
        Kernel driver in use: ata_piix                                          
        Kernel modules: ata_piix                                                

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
        Subsystem: Dell Device 0115                                             
        Flags: bus master, medium devsel, latency 0, IRQ 17                     
        I/O ports at ef40 [size=32]                                             
        Kernel driver in use: uhci_hcd                                          
        Kernel modules: uhci-hcd                                                

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
        Subsystem: Dell Device 0115                                   
        Flags: medium devsel, IRQ 10                                  
        I/O ports at efa0 [size=16]                                   
        Kernel modules: i2c-i801                                      

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
        Subsystem: Dell Device 0115                                             
        Flags: bus master, medium devsel, latency 0, IRQ 16                     
        I/O ports at ef80 [size=32]                                             
        Kernel driver in use: uhci_hcd                                          
        Kernel modules: uhci-hcd                                                

01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)                                                                        
        Subsystem: nVidia Corporation Device 010f                               
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 21             
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]                
        Memory at e8000000 (32-bit, prefetchable) [size=128M]                   
        Expansion ROM at fe9f0000 [disabled] [size=64K]                         
        Capabilities: <access denied>                                           
        Kernel driver in use: nvidia                                            
        Kernel modules: nvidia_new, nvidia_legacy, nvidia, nvidiafb, rivafb     

02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
        Subsystem: Creative Labs Device 8022                                
        Flags: bus master, medium devsel, latency 32, IRQ 3                 
        I/O ports at df80 [size=32]                                         
        Capabilities: <access denied>                                       

02:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
        Subsystem: Creative Labs Device 0020                              
        Flags: bus master, medium devsel, latency 32                      
        I/O ports at dff0 [size=8]                                        
        Capabilities: <access denied>                                     
        Kernel driver in use: Emu10k1_gameport                            
        Kernel modules: emu10k1-gp                                        

02:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax/Voice/Spkp Modem (rev 01)                                                             
        Subsystem: GVC Corporation Device 0219                                  
        Flags: bus master, medium devsel, latency 32, IRQ 11                    
        Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]                
        I/O ports at dfe0 [size=8]                                              
        Capabilities: <access denied>                                           

02:0b.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)                                                    
        Subsystem: Device 4554:434e                                             
        Flags: bus master, medium devsel, latency 32, IRQ 16                    
        I/O ports at d800 [size=256]                                            
        Memory at feaefc00 (32-bit, non-prefetchable) [size=256]                
        Expansion ROM at f4700000 [disabled] [size=256K]                        
        Capabilities: <access denied>                                           
        Kernel driver in use: dmfe                                              
        Kernel modules: dmfe                                                    

02:0c.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10)
        Subsystem: Belkin Device 0001
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at feaed000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ohci_hcd
        Kernel modules: ohci-hcd

02:0c.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10)
        Subsystem: Belkin Device 0001
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at feaee000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ohci_hcd
        Kernel modules: ohci-hcd

02:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20)
        Subsystem: Belkin Device 0002
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at feaef800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
        Kernel modules: ehci-hcd


---

