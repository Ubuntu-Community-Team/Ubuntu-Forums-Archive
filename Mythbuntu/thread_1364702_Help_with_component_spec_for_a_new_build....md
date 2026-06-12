---
title: "Help with component spec for a new build..."
date: 2009-12-26
forum: Mythbuntu
---

### Post by User X on 2009-12-26
My dad is a hardware nut and so I get his hand-me-down parts and I would like to build a Mythbuntu box.  I would like to be able to watch ATSC HD TV and record one ATSC HD program at the same time so I know I will need two tuners.  I have two options for motherboard/procs.  I have an Athalon +4000, and an Athalon X2 +6000.  Both have 4 gigs of RAM.  For video cards I have an Nvidia 9800 GTX, a 9600 GT, an 8600 GT, and an ATI X700.  My initial thoughts were to use the dual core proc and the 9600 GT video card (the 9800 GTX would cover one of my PCI X1 slots), but after reading someone elses post I heard that CPU usage was minimal using the Nvidia video cards and VDPAU.  Could I get away with using the +4000 proc with the nvidia 9600 GT and have a machine that performs well?  This machine will have one hard drive, one DVD optical drive, and no floppy, so would a 500W power supply be enough?  Thanks.

---

### Post by nickrout on 2009-12-26
the nvidia card will reduce cpu usage while watching recordings and video that is either mpeg2 or h264. It will not reduce cpu usage for transcoding or commercial detection. However I think either of the cpus will do fine.

With the gear you have you could consider a separate backend and frontend, and you would then want to use the quietest setup for the frontend. 

Avoid the ATi video card!!!!

---

