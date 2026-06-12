---
title: "Video/Flash Choppy with Mobile 915GM/GMS/910GML Express Graphics Controller"
date: 2010-09-30
forum: Multimedia Software
---

### Post by Jakeotron on 2010-09-30
Has anyone been able to optimize this video card for use with 10.04?  Flash seems excessively choppy, as are full-screen videos.  It's possible the card just can't handle it, but it seems quite bad.  My laptop is an Acer Travelmate 4060.

Flash plugin will crash sometimes as well in firefox.  Works again on  page reload.  I have flash version 10 for linux, as downloaded from  adobe.

lshw produces:

```
description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2004MiB
     *-cpu
          product: Intel(R) Pentium(R) M processor 1.73GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.13.8
          size: 1067MHz
          capacity: 1067MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:b0080000-b00fffff ioport:1800(size=8) memory:c0000000-cfffffff(prefetchable) memory:b0000000-b003ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: memory:84c00000-84c7ffff
```I'm not sure if this is a bad thing, but when I go to System > Administration > Hardware Drivers it says "No proprietary drivers are in use on this system."

I've searched around, but cannot find anything specific to 915GM video card.

---

### Post by besweeet on 2010-11-06
I wasn't very pleased with the Flash performance of the 915GM in my old DV1000. It plays videos just fine while in YouTube's little player window, but in full screen, choppy chop chop. Performance is better in Windows XP. Can play 1080p videos just fine via VLC, though.

---

### Post by lovinglinux on 2010-11-06
> **besweeet said:**
> I wasn't very pleased with the Flash performance of the 915GM in my old DV1000. It plays videos just fine while in YouTube's little player window, but in full screen, choppy chop chop. Performance is better in Windows XP. Can play 1080p videos just fine via VLC, though.

Then get [FlashVideoReplacer]("http://flvideoreplacer-extension.blogspot.com/"). You will be able to play 1080p on YouTube. Make sure you get version 1.0.6 from the [GitHub download repository]("http://github.com/lovinglinux/flvideoreplacer/downloads") or from the [versions page at Mozilla]("https://addons.mozilla.org/en-US/firefox/addon/161869/versions/"). I just uploaded version 1.0.6, so it needs to be reviewed by Mozilla before entering the Stable Channel on my site.

---

### Post by besweeet on 2010-11-11
> **lovinglinux said:**
> Then get [FlashVideoReplacer]("http://flvideoreplacer-extension.blogspot.com/"). You will be able to play 1080p on YouTube. Make sure you get version 1.0.6 from the [GitHub download repository]("http://gith*******/lovinglinux/flvideoreplacer/downloads") or from the [versions page at Mozilla]("https://addons.mozilla.org/en-US/firefox/addon/161869/versions/"). I just uploaded version 1.0.6, so it needs to be reviewed by Mozilla before entering the Stable Channel on my site.

Hmm... Is there anything like this for Chrome? I'm not a Firefox user.

---

### Post by lovinglinux on 2010-11-12
> **besweeet said:**
> Hmm... Is there anything like this for Chrome? I'm not a Firefox user.

I'm trying to port it to Opera and Chrome. Subscribe to the extension [RSS feed]("http://flvideoreplacer-extension.blogspot.com/feeds/posts/default") to get news about this.

You could also use a Greasemonkey script, although I don't know it will work on Chrome. See the replacement section of [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by TonyB911 on 2010-11-12
Try switching off hardware acceleration.

Right click on the video you are trying to play and untick the hardware acceleration box.

---

