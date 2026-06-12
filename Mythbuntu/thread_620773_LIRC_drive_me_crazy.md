---
title: "LIRC drive me crazy"
date: 2007-11-23
forum: Mythbuntu
---

### Post by MauroKTM on 2007-11-23
Dear,
I've installed  Mythbuntu but I've a big problem with LIRC:
I'm using an Hauppauge Nova-S that use i2c module.

I know that Ubuntu Edgy introduces support in the kernel to directly manage some remotes via the i2c bus. I followed the instructions to rebuild the module ir-common here:
[http://ubuntuforums.org/showthread.php?t=288229](http://ubuntuforums.org/showthread.php?t=288229)

but when I've tried to compile the module this is the answer:

"The present kernel configuration has modules disabled.
Type 'make config' and enable loadable module support.
Then build a kernel with module support enabled. "

I've load the configuration of the kernel in "menuconfig" and the 
 Loadable module support is enabled....

Any Idea How can I solve the problem? I would like to use my remote whith mythbuntu... 

Thnx..
M.

---

