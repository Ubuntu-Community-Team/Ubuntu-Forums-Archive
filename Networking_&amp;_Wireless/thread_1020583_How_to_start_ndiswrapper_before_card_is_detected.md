---
title: "How to start ndiswrapper before card is detected?"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by collix on 2008-12-24
Hi there,

after successfully booting into Intrepid without sudden freezes (thanks to noapic and irqpoll), I am now struggling with my USB wifi card (Siemens Gigaset Adapter 108).

After logging in, ndiswrapper is loaded, but the card doesn't work.

(It's that old infamous problem:)
```
[  227.844490] usb 4-5: new high speed USB device using ehci_hcd and address 3                                                                 
[  227.979346] usb 4-5: configuration #1 chosen from 1 choice                                                                                  
[  228.100531] usb 4-5: reset high speed USB device using ehci_hcd and address 3                                                               
[  228.237313] ndiswrapper (NdisWriteErrorLogEntry:190): log: C0001391, count: 4, return_address: f0aef7cc                                     
[  228.237326] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xee63ac00                                                                      
[  228.237330] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x1                                                                             
[  228.237333] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x0                                                                             
[  228.237336] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x0                                                                             
[  228.237339] ndiswrapper (mp_init:219): **couldn't initialize device: C0000001                                     **                            
[  228.237344] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)                                    
[  228.237358] ndiswrapper (mp_halt:262): device ee9f8480 is not initialized - not halting                                                     
[  228.237362] ndiswrapper: device eth%d removed                                                                                               
[  228.238954] ndiswrapper: probe of 4-5:1.0 failed with error -22                                                
```

However, when I FIRST manually remove the module (rmmod ndiswrapper) and THEN plug the device out and back in, it's immediately recognized by iwconfig and dmesg says:

```
usb 3-3: new high speed USB device using ehci_hcd and address 6                                                                 
[  326.722776] usb 3-3: configuration #1 chosen from 1 choice                                                                                  
[  326.817511] **ndiswrapper version 1.53 loaded** (smp=yes, preempt=no)                                                                           
[  326.949397] usb 3-3: reset high speed USB device using ehci_hcd and address 6                                                               
[  327.085817] ndiswrapper: driver net5523 (,02/23/2006,1.5.0.110) loaded                                                                      
[  327.087781] ndiswrapper (ZwQueryValueKey:2330): not fully implemented (yet)                                                                 
[  327.734687] wlan0: ethernet device 00:01:e3:5a:bd:40 using NDIS driver: net5523, version: 0x10005, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 129B:160C.F.conf                                                                                                                   
[  327.794232] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK                          
[  327.794769] usbcore: registered new interface driver ndiswrapper                                                                            
[  331.941267] NET: Registered protocol family 17                                                                                              
[  433.630807] NET: Registered protocol family 10                                                                                              
[  433.633115] lo: Disabled Privacy Extensions                                                                                                 
[  433.634877] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                                    
[  444.322641] wlan0: no IPv6 routers present
```

How can I make this happen at boot time? Is this still an IRQ problem? I just don't get it :)

---

### Post by wise-tangerine on 2009-01-04
Exactly same here with Hardy, the only difference is I cannot just plug in the adapter when the module is unloaded, if I try all I get is unusable device and freezed module, and even unplugging doesn't help until I reboot. The only workaround is to load the module first.
Additionally, randomly during usage of device I get the same freezed module issue. Previously it was even causing lockups, but that changed, I think with version 1.52.

---

### Post by Gert-Jan on 2009-05-08
I'm using a Gigaset USB 108 without problems with Jaunty. Use the driver for windows 2000 or vista in ndiswrapper and you can connect to the internet. Still having some problems to connect with WPA2 security though.

---

