---
title: "Sound has signal noise"
date: 2009-10-14
forum: Multimedia Software
---

### Post by gnuvistawouldbecool on 2009-10-14
But, it only affects the Right Channel.  Thought it was all sound before, then when using headphones, I can tell it's only the right hand side.

Sound works fine in Windows, using on Motherboard system, lspci reports as:

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

lshw

```
             description: Multimedia audio controller                                                                                                                                                      
             product: VT8233/A/8235/8237 AC97 Audio Controller                                                                                                                                             
             vendor: VIA Technologies, Inc.                                                                                                                                                                
             physical id: 11.5                                                                                                                                                                             
             bus info: pci@0000:00:11.5                                                                                                                                                                    
             version: 60                                                                                                                                                                                   
             width: 32 bits                                                                                                                                                                                
             clock: 33MHz                                                                                                                                                                                  
             capabilities: pm cap_list                                                                                                                                                                     
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx    
```

Using 9.04, does this in both GNOME and KDE (I guess it's a kernel level problem/driver issue).

---

