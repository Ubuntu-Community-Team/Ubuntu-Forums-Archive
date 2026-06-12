---
title: "[SOLVED] DVB-T stopped working"
date: 2008-12-06
forum: Multimedia Software
---

### Post by Skender on 2008-12-06
Hi,

I have an AVerTV DVB-T 777 PCI card in my PC. Until yesterday, that worked perfectly with Kubuntu 8.10, but today it no longer works.

This is the relevant dmesg output:
```
verc@medion:~$ dmesg | grep bt8
[   17.136437] bt878: AUDIO driver version 0.0.0 loaded
[   17.176329] bt878: Bt878 AUDIO function found (0).
[   17.176360] bt878 0000:00:06.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.176366] bt878_probe: card id=[0x7711461],[ AVermedia AverTV DVB-T 771 ] has DVB functions.
[   17.176378] bt878(0): Bt878 (rev 17) at 00:06.1, irq: 17, latency: 32, memory: 0xec002000
[   17.649752] dvb-bt8xx: A frontend driver was not found for device 109e/0878 subsystem 1461/0771

```

I have no idea what might have caused this problem. Maybe some update did. Is there any way to find out what apt-get has installed today or yesterday?

Xine says "Sorry, no DVB input device found."
This is the VLC output:
```
[00000410] dvb access error: FrontEndOpen: opening device failed (Bestand of map bestaat niet)
[00000408] main input error: open of `dvb://' failed: could not create access

```

Can anyone help me to find out how to solve this problem?

---

### Post by Skender on 2008-12-06
I didn't include the most interesting dmesg line:
```
                                                   
[   17.280065] mt352_read_register: readreg error (reg=127, ret==-5)                                                                                   
[   17.280162] dvb-bt8xx: A frontend driver was not found for device 109e/0878 subsystem 1461/0771   
```

---

### Post by Skender on 2008-12-06
It works again...

```
                               
[   17.295797] bt878_probe: card id=[0x7711461],[ AVermedia AverTV DVB-T 771 ] has DVB functions.                                   
[   17.295809] bt878(0): Bt878 (rev 17) at 00:06.1, irq: 17, latency: 32, memory: 0xec002000                                        
[   17.455904] DVB: registering new adapter (bttv0)                                                                                 
[   17.693799] usbcore: registered new interface driver snd-usb-audio                                                               
[   17.821017] DVB: registering frontend 0 (Zarlink MT352 DVB-T)... 
```

I don't know what happened. After a few reboots, it worked again. I seems like an issue with my motherboard. Sometimes while booting, my bios doesn't find my harddrive.

---

