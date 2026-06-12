---
title: "Choppy video after upgrade"
date: 2014-11-16
forum: Multimedia Software
---

### Post by jfacemyer on 2014-11-16
Since I upgraded to 14.10 on my media pc, I've got choppy video in a couple of scenarios:

[LIST]
[*]XBMC HD videos
[*]Firefox and Chrome, but only fullscreen (and apparently only flash)
[/LIST]

I haven't seen the issue with other players (like VLC), only XBMC.

I tried a brand new user profile, same thing.

I've searched for several hours, I see nothing about this - any ideas where to start?

(EDIT)

There've been some crashes watching video, one of which was while using VLC, though mostly with XMBC (just crashing/hanging the app) and the browsers (crashing the whole OS).

---

### Post by Zavation on 2014-11-16
Have you tried upgrading your graphics drivers? It's possible that the newer Kernel doesnt like to play well with your current graphics card.

---

### Post by jfacemyer on 2014-11-16
Zavation,

Thanks for your reply.

I had thought about that, but I've never installed any drivers before (it's an H55-USB3, which has Intel integrated video, which driver is included by default, afaik).

---

### Post by Rob Sayer on 2014-11-20
Read this ...

[http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card](http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card)

... and post the details of what your video adapter actually is.  Use [CODE] tags.

---

### Post by jfacemyer on 2014-12-09
Sorry, went away on vacation before I could respond. Thanks for following up, Rob!

```

  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:f2000000-f23fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f2400000-f24fffff

```

---

### Post by jfacemyer on 2014-12-29
Bump.

I've tried updating several times, but the kernel and driver updates haven't helped. I don't even really know where to begin to file a bug report (or find existing reports). Nothing I've searched has been productive.

---

### Post by frank18 on 2014-12-31
Have tried to delete cache & cookies in XBMC? special in mash up

---

