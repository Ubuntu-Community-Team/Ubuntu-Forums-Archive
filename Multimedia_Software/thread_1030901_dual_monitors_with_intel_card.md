---
title: "dual monitors with intel card"
date: 2009-01-04
forum: Multimedia Software
---

### Post by skippymo on 2009-01-04
after reading some bit i'm getting more and more confused. i want dual monitors and really would want my function f8 to toggle but i'm not sure if that is possible....i have a dell d630 video specs are below. thanks guys. anyhow when i use the screen resolution thing i have to restore my xorg.conf file each time i mirror my screens or extend it. HELP!!! very frustrating


WARNING: you should run this program as super-user.
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by densou on 2009-01-05
here you are, lad:
[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

first, add to your /etc/apt/sources.list at the bottom these:
```
deb http://ppa.launchpad.net/intel-gfx-testing/ubuntu intrepid main
deb-src http://ppa.launchpad.net/intel-gfx-testing/ubuntu intrepid main
```

it'll provide Intel video upgrades (unless you want to switch to WIP Jaunty) :P

---

### Post by love007575 on 2009-01-05
[[color=black]ThinkGeek[/color]](http://www.geekideathing.com/)

---

