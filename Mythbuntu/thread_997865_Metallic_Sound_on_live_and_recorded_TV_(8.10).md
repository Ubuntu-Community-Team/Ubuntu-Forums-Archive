---
title: "Metallic Sound on live and recorded TV (8.10)"
date: 2008-11-30
forum: Mythbuntu
---

### Post by thusgaard on 2008-11-30
Hi 

I have tested this with MythTV as well as VLC.
But I get a metallic sound. 

I tried this: [https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#Razzing/tinny/metalic%20sound](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#Razzing/tinny/metalic%20sound) but it did't solve the problem. 

I have the following: 
- HDA Intel Realtek ALC880
- ASUS TV-FM7134 (SAA7134)

I had this working before doing a complete reinstall to 8.10, but I can not remember what I did back then!

Can any one please help me. I need to record a program for my 2 year old every day in december...  ;-)

J;-)

---

### Post by thusgaard on 2008-11-30
I have narrowed it down. It's not the sound card. So I't either some TV card setting or the TV card driver!

---

### Post by thusgaard on 2008-11-30
Sound is perfect in TVtime too...

---

### Post by thusgaard on 2008-11-30
OK. 

When sound comes from CD. It goes through the soundcard and all is good.  
When sound comes from TV Tuner and is played with TVTime it goes via the CD connection on the soundcard and all is good. 

When sound comes from TV Tuner and is played with VLC or MythTV it goes through CD to the soundcard is compressed and replayed. the replay is distorted. 

So my hardware and my drivers are OK. But I have a bad setup. And I badly need some help with that!

---

### Post by thusgaard on 2008-12-01
Here I am still thinking about this problem. Could it be some sort of Codec problem. And where can I change sound Codec?

---

### Post by uncle hammy on 2008-12-01
For what it's worth, my 8.10 frontend just started having a similar issue yesterday, right after latest updates were applied.  When watching LiveTV or Recorded TV, the sound is now tinny and it also echos.  It also started playing audio from LiveTV over top of recordings, and occasionally starting to play music when choosing a recording to watch.

I have found that exiting to the "Do you want to exit" screen and selecting no and "refreshing" the frontend seems to fix it for a while.  

I am seriously considering going back to 8.04 with this frontend tonight, I've had too many issues with 8.10.

---

### Post by thusgaard on 2008-12-01
Reinstalling is not an option, I havn't got the time. 

And refreshing or restarting dosn't help me. 

Maybe the weekend will bring a reinstall.

---

### Post by Ronno6 on 2008-12-01
Try this:
Frontend Setup>Recording Proiles>(your encoder)>Default(and all the rest)>Then navigate to the screen with the sound encoding method and sampling bitrate. Pump it up to 48000. This is the one you need for HD TV.

That cured it for me on HD programming. Try it for your situation.

Good luck.

---

### Post by thusgaard on 2008-12-02
> **Ronno6 said:**
> Try this:
Frontend Setup>Recording Proiles>(your encoder)>Default(and all the rest)>Then navigate to the screen with the sound encoding method and sampling bitrate. Pump it up to 48000. This is the one you need for HD TV.


First of all it's not a HD setup. It's pure Analog!

Second your suggestion is part of the Ubuntu documentation. But you couldn't possibly know that I have already tried it: [https://help.ubuntu.com/community/MythTV/Install/Feisty/Troubleshooting#Razzing/tinny/metalic%20sound](https://help.ubuntu.com/community/MythTV/Install/Feisty/Troubleshooting#Razzing/tinny/metalic%20sound)

Thanks for trying. ;-)

---

### Post by uncle hammy on 2008-12-02
What video drivers are you using?  If you're using the NVidia 177 series, try dropping to the 173 and see what happens.  I have seen some audio related issues mentioned with the 177 drivers.

---

### Post by thusgaard on 2008-12-02
> **uncle hammy said:**
> What video drivers are you using?  If you're using the NVidia 177 series, try dropping to the 173 and see what happens.  I have seen some audio related issues mentioned with the 177 drivers.

I'm using 173. 177 dosn't work for me at all.

==> lshw <==
computer
description: Desktop Computer
product: PW693AA-ABY t3055.dk
vendor: HP Pavilion 061
version: 0qy0211RE101PUFFM00
serial: [REMOVED]
width: 32 bits
capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
configuration: boot=normal chassis=desktop cpus=1 uuid=C012763C-CB5B-D911-A469-8344212B374D
*-core
description: Motherboard
product: Puffer
vendor: ASUSTeK Computer INC.
physical id: 0
version: 1.xx
serial: [REMOVED]
*-firmware
description: BIOS
vendor: American Megatrends Inc.
physical id: 0
version: 3.18 (02/16/2005)
size: 64KiB
capacity: 448KiB
capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
*-cpu
description: CPU
product: Intel(R) Pentium(R) 4 CPU 2.93GHz
vendor: Intel Corp.
physical id: 4
bus info: cpu@0
version: 15.4.1
serial: [REMOVED]
slot: CPU 1
size: 2933MHz
capacity: 3800MHz
width: 32 bits
clock: 133MHz
capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up pebs bts pni monitor ds_cpl tm2 cid xtpr
configuration: id=0
*-cache:0
description: L1 cache
physical id: 5
slot: L1-Cache
size: 16KiB
capacity: 16KiB
capabilities: pipeline-burst internal varies data
*-cache:1
description: L2 cache
physical id: 6
slot: L2-Cache
size: 1MiB
capacity: 1MiB
capabilities: pipeline-burst internal varies unified
*-cache:2 DISABLED
description: L3 cache
physical id: 7
slot: L3-Cache
capabilities: internal varies
*-memory
description: System Memory
physical id: 21
slot: System board or motherboard
size: 1GiB
*-multimedia
description: Audio device
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
vendor: Intel Corporation
physical id: 1b
bus info: pci@0000:00:1b.0
version: 03
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=HDA Intel latency=0 module=snd_hda_intel
*-network:1
description: Wireless interface
product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
vendor: Intersil Corporation
physical id: 4
bus info: pci@0000:03:04.0
logical name: wmaster0
version: 01
serial: [REMOVED]
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=prism54pci ip=[REMOVED] latency=64 maxlatency=28 mingnt=10 module=p54pci multicast=yes wireless=IEEE 802.11bg
*-multimedia
description: Multimedia controller
product: SAA7134/SAA7135HL Video Broadcast Decoder
vendor: Philips Semiconductors
physical id: 5
bus info: pci@0000:03:05.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=saa7134 latency=64 maxlatency=255 mingnt=255 module=saa7134

---

### Post by thusgaard on 2008-12-03
I did a complete reinstall last night. 
I still have the problem.

---

### Post by thusgaard on 2008-12-04
[http://www.mythtv.org/docs/mythtv-HOWTO-7.html#ss7.2](http://www.mythtv.org/docs/mythtv-HOWTO-7.html#ss7.2)

Didn't solve the problem...

... untill I reread this line and understood it

> Try reducing the percentages by 5-10% and checking again

I reduced by 50% and have perfect sound.

---

