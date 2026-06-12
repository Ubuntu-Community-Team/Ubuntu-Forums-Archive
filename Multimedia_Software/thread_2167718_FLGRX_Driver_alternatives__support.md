---
title: "FLGRX Driver alternatives / support"
date: 2013-08-14
forum: Multimedia Software
---

### Post by eumpfenbach on 2013-08-14
Started with Ubuntu 10.x. Switched to 12.04 (there currently). 

10.x had great, seemless video. Ever since I went to 12.04 I have dealt wtih no sound, video on fast forward, and just small glitches in the video (look like lines across the screen, almost like something buffering).

I got my system set up in a way that minimizes the video glitches (and eliminates problems with sound / playback speed), but I'm getting sick of them. Has anyone been doing work in the newer versions of Ubuntu to get better video support? Anyone just get sick of these problems (I know from searching this board when I was having trouble that there were a lot of others) and just wipe their drive and install an old version?

Just hoping someone has found an answer in the months since I last checked here...

---

### Post by QIII on 2013-08-14
Hello!

Can you tell us a little about your machinec's specs, particularly the GPU?

Is this 12.04, 12.04.1 or 12.04.2?

Which version of fglrx do you have installed?

---

### Post by eumpfenbach on 2013-08-14
12.04 (no more numbers)

It's an HTPC that I run via HDMI to a projector. This cover the rest?

 *-display               
       description: VGA compatible controller
       product: RS880 [Radeon HD 4250]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:feaf0000-feafffff memory:fe900000-fe9fffff



Thanks!!

---

