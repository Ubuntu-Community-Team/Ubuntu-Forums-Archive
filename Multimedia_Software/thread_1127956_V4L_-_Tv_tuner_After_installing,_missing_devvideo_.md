---
title: "V4L - Tv tuner: After installing, missing /dev/video directory"
date: 2009-04-17
forum: Multimedia Software
---

### Post by spaceboy909 on 2009-04-17
I'm trying to get my Leadtek tv tuner card running.  After installing the appropriate file(s) listed at linuxtv.org, I am missing the /dev/video directory that it says I should have.  Trying to run the various tv display apps yields either 'no signal' or an 'X' lockup.  Here's a hardware listing for my Leadtek card:
```
*-multimedia:0
                description: Multimedia video controller
                product: Bt878 Video Capture
                vendor: Brooktree Corporation
                physical id: 6
                bus info: pci@0000:03:06.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=bttv latency=32 maxlatency=40 mingnt=16 module=bttv
           *-multimedia:1 UNCLAIMED
                description: Multimedia controller
                product: Bt878 Audio Capture
                vendor: Brooktree Corporation
                physical id: 6.1
                bus info: pci@0000:03:06.1
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32 maxlatency=255 mingnt=4

```

---

### Post by spaceboy909 on 2009-04-18
Bump....any ideas?

---

### Post by spaceboy909 on 2009-04-19
I'm updating this a bit:  Apparently, Ubuntu is using the file 'video0' instead of plain 'video'.  So I guess it's not missing after all.  Also, for anyone looking for the modules.conf file to edit, as some guides suggest, Ubuntu apparently uses the 'options' file in the modprobe.d directory for this.

So, lspci, lsmod and dmesg all seem to be showing that my card has been detected and drivers are in use, but....

I still get no picture.

I have set my options file to: 
options bttv tuner=2 card=34 lumafilter=1 combfilter=1 chroma_agc=1

Xawtv and Zapping Tv give me a full blank screen and lock me out of my desktop.  I'm forced to restart X.

Tvtime Tv viewer gives me a window with  the 'no signal' blue screen.

Digital Tv onlys gives an error:  No tuner found

Myth Tv loads a  process, but closes out before showing a window.

Any ideas at this point?

---

### Post by markackerman8@gmail.com on 2009-12-09
I have the same problem and here is my 

sudo lshw -C multimedia
...
*-multimedia UNCLAIMED
       description: Multimedia video controller
       product: CX23885 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm vpd msi bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f61fffff

and my dmsg is

...

[   10.290031] sdhci-pci 0000:09:09.1: SDHCI controller found [1180:0822] (rev 22)
[   10.290051] sdhci-pci 0000:09:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   10.292157] Registered led device: mmc0::
[   10.293200] mmc0: SDHCI controller on PCI [0000:09:09.1] using PIO
[   10.362468] cx23885: Unknown parameter `tuner'
[   10.517267] cfg80211: World regulatory domain updated:
[   10.517271] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.517274] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.517277] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)

and my

ack@Titan:~$ modprobe cx23885 
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Error inserting cx23885 (/lib/modules/2.6.31-16-generic/kernel/drivers/media/video/cx23885/cx23885.ko): Operation not permitted

and before the last reboot modprobe didn't show any errors but still all the TV Programs recognized only my cam if anything

I have been revisiting this after a year and don't want to go back to WINDOWS!!!  Too much invested

Thanks in advance

Mark

---

