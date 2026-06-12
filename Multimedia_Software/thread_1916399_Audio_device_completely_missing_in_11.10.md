---
title: "Audio device completely missing in 11.10"
date: 2012-01-27
forum: Multimedia Software
---

### Post by OlympicSoftworks on 2012-01-27
I am being asked to help a new GNU/Linux user trying to install Ubuntu who is having a hell of a time with his laptop and it's sound.  I've never seen something like this before, and I've been using Ubuntu since 6.6.
 

 It is an HP Pavilion dv6500.  I've asked him to do a **sudo lshw > hardware_loadout** and under 11.10 the audio hardware is simply not present.  Other than this, the OS is totally stable and he likes it a great deal.
 

 I've asked him to get 10.04 downloaded and installed on a USB stick to boot from in order to do the same **LSHW** command to see what happens under a different kernel, and sure enough it shows up.
 

 Here is the start of the LSHW from 10.04, it's the same as 11.10 though.  I have this here just to show the exact model and MoBo.
 

 

ubuntu 
    description: Notebook 
    product: HP Pavilion dv6500 Notebook PC 
    vendor: Hewlett-Packard 
    version: Rev 1 
    serial: xxxxxxxx 
    width: 32 bits 
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp 
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=434E4637-3431-3156-4356-001B24B6AE40 
  *-core 
       description: Motherboard 
       product: 30CF 
       vendor: Quanta 
       physical id: 0 
       version: 85.24 
       serial: None1 
     *-firmware 
          description: BIOS 
          vendor: Hewlett-Packard 
          physical id: 0 
          version: F.25 (11/29/2007) 
          size: 110KiB 
          capacity: 960KiB 
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery 


Here is the interesting part that only shows up under 10.04:
 
     *-multimedia UNCLAIMED 
          description: Audio device 
          product: MCP67 High Definition Audio 
          vendor: nVidia Corporation 
          physical id: 7 
          bus info: pci@0000:00:07.0 
          version: a1 
          width: 32 bits 
          clock: 66MHz 
          capabilities: pm msi ht cap_list 
          configuration: latency=0 maxlatency=5 mingnt=2 
          resources: memory:f6480000-f6483fff


And here is the same device iterated with **LSPCI -vvnn**

 00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1) 
    Subsystem: Hewlett-Packard Company Device [103c:30cf]
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 21
    Region 0: Memory at f6480000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
        Masking: 00000000  Pending: 00000000
    Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel modules: snd-hda-intel

 
And here is the same device iterated with **LSPCI -vvnn**
 

00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1) 
    Subsystem: Hewlett-Packard Company Device [103c:30cf]
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 21
    Region 0: Memory at f6480000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
        Masking: 00000000  Pending: 00000000
    Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel modules: snd-hda-intel

  Under 11.10 slot 00:07.0 this simply isn't iterated.  It skips from 00:04.1 to 00:08.0.  One other thing that is curious; according to the HP website, this laptop is supposed to have a Conexant chip for sound.
 

 If I could get any help or idea on how to get this guy's sound set up I'd be very appreciative, and he will be even more appreciative still.

---

### Post by BicyclerBoy on 2012-01-28
May be a long shot..
MCP67 has problems with message signalled interrupts especially with audio component.
I think the alsa driver automatically loads MCP67a with snd_hda_intel nomsi option.

But your problem is that the system does not find the h/w so then no driver is loaded..

You could try grub boot option:
pci=nomsi

---

### Post by MoreOrLess on 2012-01-28
So lshw doesn't see it, but lspci does? Does aplay -l find it?
```
aplay -l
```

> this laptop is supposed to have a Conexant chip for sound
It probably does. Nvidia doesn't make codecs, they just slap their name in the OEM field :P
The best way to tell is using alsa info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by OlympicSoftworks on 2012-01-28
Thanks for the help folks.

BicyclerBoy, I'll look up what that grub boot option does and try it.  Thank you!
pci=nomsi



MoreOrLess, neither LSPCI nor LSHW find the audio hardware in 11.10.  But both find it in 10.04.  Aplay won't work because there is only a dummy audio device that just sinks the data sent to it and does nothing useful.

I'll ask for them to do use [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo) and see what we get.


The data retrieved in Ubuntu 10.04 show 10de:055c as the device identifier:
vendor: 10de ("*NVIDIA Corporation*"), device: 055c ("*MCP67 High Definition Audio*")

I also found this:
[http://openbenchmarking.org/linux/PCI/0403/10de:055c](http://openbenchmarking.org/linux/PCI/0403/10de:055c)

It links to the hardware's page in the database.  MoBo #2 is the mobo in question here.

[http://openbenchmarking.org/s/NVIDIA%20MCP67%20HD%20Audio](http://openbenchmarking.org/s/NVIDIA%20MCP67%20HD%20Audio)

So this is NVidia hardware, but it seems to use the Intel HD Audio drivers.

Thanks for the help. I will post again once I get the Alsa info back from them.

---

### Post by MoreOrLess on 2012-01-28
> **OlympicSoftworks said:**
> So this is NVidia hardware, but it seems to use the Intel HD Audio drivers.

Correct. Intel was the primary creator of the HDA standard, so their name is on the sound driver too.

---

