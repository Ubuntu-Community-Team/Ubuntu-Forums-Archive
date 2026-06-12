---
title: "Realtek acl655 Rev1 not operating properly"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by DarKmaN-07 on 2007-04-14
Hi, I been using Ubuntu for about 3-4 months casually now on an Asus p5s800-VM, where everything worked perfectly. 
The audio and Nvidia properties worked like a charm and were all auto-detected via the OS. 

I recently upgraded (this is where is goes wrong) to an Asus P5VDC-MX mobo and after installation I noticed there was no sound. 
I went into bios and changed the PnP option to be detected by the OS and not the mobo (where it would assign an address to a device) , and now I have some audio, but its extremely faint and needs to be at 100% on all volume controls in the manager and on the speakers themselves. 

I'm using the alsa manger and drivers, the VIA chipset and realtek ALC655 devices are also detected in the manager, but I don't know how to get it working 100%. 

Any ideas???

---

### Post by DarKmaN-07 on 2007-04-15
I figured out that it wasn't the operating system at all, and that it is the new case I'm using instead. The front panel audio connectors are the cause of the lack of audio from the back. 

I suspected as much but knew that it was wired correctly, its just the case n mobo combo that got me. No front panel audio for me and I had to put the jumpers back to fix the rear panel audio :(

---

### Post by DarKmaN-07 on 2007-04-16
It happened again and the realtek alc655 device isn't even being recognized by the os (Ubuntu 6.10 Edgy)

I installed the drivers from the Realtek site also. The ones for Realtek alc655 + Linux OS - Other. 
They were working, but then when I restarted something went wrong and they ceased to work. 
Now all audio has been stopped again and the only thing I can see in audio properties for mixing etc is alsamixer. 

I'm almost out of energy when it comes to fixing this OS please if anyone has any ideas please reply, 
I would really appreciate it.

---

