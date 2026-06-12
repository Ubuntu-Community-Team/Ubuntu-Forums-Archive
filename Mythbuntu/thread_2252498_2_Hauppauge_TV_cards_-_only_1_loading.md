---
title: "2 Hauppauge TV cards - only 1 loading"
date: 2014-11-12
forum: Mythbuntu
---

### Post by Mike_Brown on 2014-11-12
I posted this in the hardware forum, but got no responses. I hope someone here has a solution.

Using Mythbuntu 14.04.

I have 2 Hauppauge HVR-1600 TV cards. Only 1 of them can be accessed. 


My lspci -v section showing the cards is:
```

03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
    Subsystem: Hauppauge computer works Inc. Device 7400
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at f4000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: [44] Vital Product Data
    Capabilities: [4c] Power Management version 2
    Kernel driver in use: cx18




03:02.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
    Subsystem: Hauppauge computer works Inc. WinTV HVR-1600
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at f8000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: [44] Vital Product Data
    Capabilities: [4c] Power Management version 2

```
As you can see, the 1 in the 1st pci slot has 'Kernel driver in use: cx18' and the second does not show a driver in use. 


This is the return from dmesg | grep cx
```

[    8.731923] cx18:  Start initialization, version 1.5.1
[    8.731957] cx18-0: Initializing card 0
[    8.731958] cx18-0: Autodetected Hauppauge card
[    8.735391] cx18-0: cx23418 revision 01010000 (B)
[    8.949625] cx18-0: Autodetected Hauppauge HVR-1600
[    8.949626] cx18-0: Simultaneous Digital and Analog TV capture supported
[    9.189668] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[    9.381018] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[    9.381020] DVB: registering new adapter (cx18)
[    9.627461] cx18 0000:03:00.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[    9.627566] cx18-0: DVB Frontend registered
[    9.627568] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[    9.627620] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[    9.627664] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[    9.627707] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[    9.627748] cx18-0: Registered device radio0 for encoder radio
[    9.627750] cx18-0: Initialized card: Hauppauge HVR-1600
[    9.627772] cx18-1: Initializing card 1
[    9.627774] cx18-1: Autodetected Hauppauge card
[    9.630943] cx18-1: ioremap failed. Can't get a window into CX23418 memory and register space
[    9.630948] cx18-1: Each capture card with a CX23418 needs 64 MB of vmalloc address space for the window
[    9.630951] cx18-1: Check the output of 'grep Vmalloc /proc/meminfo'
[    9.630953] cx18-1: Use the vmalloc= kernel command line option to set VmallocTotal to a larger value
[    9.630958] cx18-1: Error -12 on initialization
[    9.630963] cx18: probe of 0000:03:02.0 failed with error -12
[    9.630978] cx18:  End initialization
[    9.708326] cx18-alsa: module loading...
[   10.412092] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   10.564968] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   10.571521] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   11.453014] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   11.472650] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)

```


lspci shows each card having 64Mb, but grep cx says that there is insufficient memory allocated. I am new enough to Ubuntu that I am not sure of how to make the change that grep cx says needs to be made.


I have had to re-load Mythbuntu several times to get it working somewhat. One of those previous times, both cards worked -- all other times, only the 1st card.


Any help would be appreciated. Like I said, I am new enough that the instructions need to be step-by-step.


Thanks for any help.

---

### Post by aelfric55 on 2014-11-12
The dmesg output says your virtual memory allocation (vmalloc) value at boot is too low. Set it higher so the modules have memory space to load into. Particularly if using an NVidia card --the nvidia proprietary driver and the cx18 driver tend to trip over each other playing musical chairs for the same memory space.

vmalloc adjusts in 128M increments. Usually 1 Hauppauge card + an NVidia card requires vmalloc=128M or vmalloc=256M Two Hauppauge cards with an NVidia card will normally require vmalloc=256M or even vmalloc=512M. Try the various values starting at vmalloc=128M to find the lowest value that works consistently for you.

Vmalloc is a kernel command and is set in your bootloader. For grub2, directions can be found here, among other places: [https://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small](https://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small)  However, it looks like the example the mythtv wiki gives for grub2 may have a typo --their example should probably read  "vmalloc=256M" rather than "vmalloc=256MB"

---

### Post by dannyboy79 on 2014-11-12
you could implement this temporarily to see if it works by editing the kernel boot command during boot up, hold shift so your grub menu appears, then hit the e key on whichever kernel you want to effect (the first menu entry may njust say Ubuntu) which edits the boot command, then use the down arrow to get to the line that has 
```
quiet splash $vt_handoff
```
and make it look like this
```
quiet splash $vt_handoff  vmalloc=256M
```
and then to boot just hit ctrl+x on your keyboard. Good luck!  Here's a great guide if needed.  [http://www.howtogeek.com/196520/grub2-101-how-to-access-and-use-your-linux-distributions-boot-loader/](http://www.howtogeek.com/196520/grub2-101-how-to-access-and-use-your-linux-distributions-boot-loader/)

---

### Post by Mike_Brown on 2014-11-12
> **aelfric55 said:**
> The dmesg output says your virtual memory allocation (vmalloc) value at boot is too low. Set it higher so the modules have memory space to load into. Particularly if using an NVidia card --the nvidia proprietary driver and the cx18 driver tend to trip over each other playing musical chairs for the same memory space.

vmalloc adjusts in 128M increments. Usually 1 Hauppauge card + an NVidia card requires vmalloc=128M or vmalloc=256M Two Hauppauge cards with an NVidia card will normally require vmalloc=256M or even vmalloc=512M. Try the various values starting at vmalloc=128M to find the lowest value that works consistently for you.

Vmalloc is a kernel command and is set in your bootloader. For grub2, directions can be found here, among other places: [https://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small](https://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small)  However, it looks like the example the mythtv wiki gives for grub2 may have a typo --their example should probably read  "vmalloc=256M" rather than "vmalloc=256MB"

I had tried the Grub fix, but entered the "256MB" instead of just "256M" (which did not work) -- I'll try that when I get home from work.

Thanks

---

### Post by Mike_Brown on 2014-11-17
Thanks for the help. The change in Grub worked --  both cards are now in use.

---

### Post by Mike_Brown on 2014-11-18
The 'fix' only worked for 1 day. Now the 2nd card is showing up in the pci list, but does not have an IRQ address -- the 1st card has IRQ 16. Is there some other way to get it active. They both are Hauppauge HVR-1600 cards with the Conexant/Samsung processors.

Thanks for any help.

---

### Post by aelfric55 on 2014-11-18
Is this the same issue as before? Does the dmesg output show the same vmalloc shortfall as previously? Did the 1600 run OK until after reboot, or did it stop running prior to rebooting? Have you cold-booted since the problem appeared? If the card failed prior to rebooting, does the backend log (or the syslog) show anything from the time of failure?

You've never mentioned what video driver you're using on the machine (with what video card). When I've used 2 1600 cards with an NVidia card, I've only been able to get away with vmalloc=256M when I've used the nouveau driver --with NVidia's proprietary driver and 2 1600s, I've always had to use vmalloc=512M

The 1600 is known to occasionally fail while trying to tune a signal (result: a 0-byte recording --either analog or digital) and then it goes into a state from which it can be roused only by a hard shutdown and cold start. A warm restart doesn't do it. The card also has problems during the first boot after a dirty poweroff (like after a power outage)

The card is also a bit fussy about which PCI slot it's put into. If you have another slot available, you may wish to try the second card there. Also, swapping the 2 cards in their respective slots could potentially confirm that it's not the card itself failing.

---

### Post by Mike_Brown on 2014-11-18
Thanks for the reply.

The 2nd card worked until re-booting -- but I've only done re-starts - not cold re-boots.

I increased the vmalloc from 256M to 320M -- but the 2nd is still not recognized, but again did a re-start instead of cold boot.

I will do a cold boot this evening and if that doesn't cure it, will get and post the logs. 

Thanks again.

---

