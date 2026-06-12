---
title: "Poor resolution from HDMI out in Ubuntu 10.10, great resolution in Windows 7."
date: 2011-07-03
forum: Multimedia Software
---

### Post by martinp8 on 2011-07-03
Hope this is the right place to post this! 

I've been using Ubuntu 10.10 64bit on my Thinkpad SL500 for a while now and I love it but I get poor resolution on my TV when I use the HDMI out. I get 1280x720 and that appears as the max resolution. However, in Windows 7 I can get a max 1920x1080 output from the HDMI port. This is very annoying as I have to reboot and swap to Windows every time I want to watch a movie in 1080p. Any help would be hugely appreciated.

---

### Post by mxyzptlk on 2011-07-03
> **martinp8 said:**
> Hope this is the right place to post this! 

I've been using Ubuntu 10.10 64bit on my Thinkpad SL500 for a while now and I love it but I get poor resolution on my TV when I use the HDMI out. I get 1280x720 and that appears as the max resolution. However, in Windows 7 I can get a max 1920x1080 output from the HDMI port. This is very annoying as I have to reboot and swap to Windows every time I want to watch a movie in 1080p. Any help would be hugely appreciated.

didi you check the drivers for your video card?

maybe you need privative drivers for it

go to system configuration> hardware> aditional drivers and click on it

the system itself is gonna do a short test in case any device needs an aditional driver it will tell you to search for it in ubuntu sftware control

---

### Post by martinp8 on 2011-07-03
Yeah I tried that, it says no propriety drivers are in use on this system. When I type lshw I get:

             *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:fd300000-fd3fffff

I reckon that UNCLAIMED isn't a good thing.

---

### Post by mxyzptlk on 2011-07-03
> **martinp8 said:**
> Yeah I tried that, it says no propriety drivers are in use on this system. When I type lshw I get:

             *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:fd300000-fd3fffff

I reckon that UNCLAIMED isn't a good thing.

thats not the lshw for the hdmi output thats for your monitor let me see

---

### Post by martinp8 on 2011-07-03
This is the only other bit that looks like it's relevant to graphics, if this stuff is even useful at all: 

*-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:46 memory:fd400000-fd7fffff memory:d0000000-dfffffff ioport:5c00(size=8)

---

### Post by mxyzptlk on 2011-07-03
> **martinp8 said:**
> This is the only other bit that looks like it's relevant to graphics, if this stuff is even useful at all: 

*-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:46 memory:fd400000-fd7fffff memory:d0000000-dfffffff ioport:5c00(size=8)

after a short searmy mind and my system itself. i believe that you need to ugrade the kernel or installt he latest version of ubuntu wich is 11

there are plenty of bugs regarding on intel mobile series but maybe the kernel upgrade will solve it.

i f you dont want to get rid of your current ubuntu distro, ubuntu 11 has a a dual boot capability (i think you alredy know it) and try both

---

### Post by uteck on 2011-07-04
Or just try the live cd and see how well that works.

---

### Post by martinp8 on 2011-07-04
Yeah that's exactly what I was thinking. 

Oh and thanks for replying guys.

---

### Post by martinp8 on 2011-07-04
No it doesn't work in 11.04 either :/

---

### Post by createdcreature on 2011-07-04
Install the proprietary drivers in System>Administration>Additional Drivers, or try and turn on visual effects. Update your system, especially the kernel, in System>Administration>Update Manager.;)

---

### Post by martinp8 on 2011-07-04
There are no propriety drivers, visual effects are already turned on and everything is updated.

---

