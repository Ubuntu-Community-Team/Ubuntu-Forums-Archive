---
title: "Can't get surround sound to work"
date: 2009-03-01
forum: Multimedia Software
---

### Post by runebinder on 2009-03-01
have installed Ubuntu today and getting everything set up, one problem is that I can't get the surround sound to work, it's just outputting through my 2 front speakers. Have checked some of the guides, ran alsamixer -c 0 in terminal, turned up the volume for surround and centre, yet this hasn't made a difference and now at a bit of a loss at what to do.

I know the hardware is fine as it works in Windows with no issues. Any ideas on what I need to resolve this?

Oh and the results for sudo lshw -C sound brings up:

 *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

And aplay -l brings up: 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I'm going to try a good old fashioned restart to see if that kicks it in, otherwise I'm stumped.

[Edit: Restart didn't make any changes.]

---

