---
title: "Sound device"
date: 2009-07-28
forum: Multimedia Software
---

### Post by desperateone on 2009-07-28
Hello;

when I try to run epsxe, it complains that the sound device is not available. The only thing that was using it was Quod Libet, but the sound device is still allegedly not available after shutting down QL. What's the path to the device so I can [FONT="Courier New"]fuser[/FONT] it (I remember doing it some day)? And what could be the cause of the problem?

epsxe log:
[SIZE="1"]```
 * Running ePSXe emulator version 1.5.2.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [..].
 * Init ISO code ... (+subchannel)ok
 * Force NTSC cdrom detected.
 * Init gpu[0][libgpuPeteMesaGL.so.1.0.76]
NVIDIA Corporation
                  GeForce Go 7300/PCI/SSE2/3DNOW!
                                                  * Open gpu[0]
 * Init spu[0][libspuPeopsOSS.so.1.0.9]
Sound device not available!
                            * Open spu[0]
[..]
```[/SIZE]

---

