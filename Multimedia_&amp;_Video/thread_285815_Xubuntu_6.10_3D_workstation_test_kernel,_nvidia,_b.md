---
title: "Xubuntu 6.10 3D workstation test: kernel, nvidia, blender optimization thread"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by n00b0id on 2006-10-27
Ok embarking once again on a dangerous mission to create a nice 3D workstation.

SO FAR I have 
0. downloaded, burned on cd and installed the Xubuntu 6.10 final from xubuntu.org - and its very nice, clean, and importantly uses less than half of the memory (~190 MB) that kubuntu desktop does (did), so theres 200 MB more to use for 3D graphic objects and render trees. 

GOAL is to 
1. Compile kernel so that its optimized for this processor
2. then install nvidia viddy card drivers.
3. Finally Blender 2.42a or CVS version, compiled with optimizations for this processor, perhaps yafray or indigo raytracers, too.
4. If possible figure out if Gimp can be optimized.

I have compiled a kernel before once or twice about a year ago. Any help appreciated :)

First I will read a few documents on kernel compilation so I know what I am doing, and what (if any?) optimizations are possible?

See these two for a nice overview
[http://blogs.cyberciti.biz/hm/index.php/2005/09/28/exploring-linux-kernel/](http://blogs.cyberciti.biz/hm/index.php/2005/09/28/exploring-linux-kernel/)
[http://doc.gwos.org/index.php/Kernel_Compilation](http://doc.gwos.org/index.php/Kernel_Compilation)

---

### Post by japurcell on 2006-10-27
I followed this tutorial for 2.6.18 [http://www.ubuntuforums.org/showthread.php?t=217657]("http://www.ubuntuforums.org/showthread.php?t=217657") still on dapper though.  Not all of my old configs copied over and I didn't get iptables, which disabled firestarter, killed my usplash, and I can't mount my iPod for some reason.  But then again I may have miss clicked some things too.  I'm interested to know how your kernel turns out for you.

---

### Post by josys36 on 2006-10-27
Every single time I have tried to compile the kernel it is been a big huge flop. Personally I don't like the process and feel it best to leave it to folks who know much more about what they are doing.

Jason

---

### Post by n00b0id on 2006-10-29
I am still researching. So many options! I wont do a kernel compile&update until I am 95% certain about everything. 

Still actually also researching if there will be any benefit for compiling for this athlon XP...

---

