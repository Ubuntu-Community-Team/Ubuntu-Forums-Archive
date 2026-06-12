---
title: "i810 3d support"
date: 2006-02-12
forum: Multimedia &amp; Video
---

### Post by cburb on 2006-02-12
Hi,

I have an i810 graphics card - the onboard graphics iin my SD31P shuttle case. I am running Ubuntu 5.10 on it, and am using the ubuntu-supplied i810 driver.

I have been unable to get any 3D working at all. glxgears simply displays nothing, and glxinfo hangs. The program I am trying to use is kpovmodeler, which relies on opengl. This program hangs when run, unless I comment out the GLcore and glx modules in the xorg.conf file. 

I am running at 1280x1024, with 24bit colour. I have also tried 16bit colour.

Can anyone help? Just to get opengl running - either software or hardware processing would be great. I dont play computer games.

Thanks,

Chris

---

### Post by cburb on 2006-02-12
Ok, I just commented out the dri module in xorg.conf, and nothing crashes anymore - I can run kpovmodeler fine, and glxgears now works:

4487 frames in 5.0 seconds = 891.264 FPS
4548 frames in 5.1 seconds = 889.092 FPS
4560 frames in 5.1 seconds = 892.125 FPS
4560 frames in 5.1 seconds = 892.057 FPS
4560 frames in 5.1 seconds = 890.783 FPS

Is this dri thing important? Do I need it? As I said, I dont need games, so can I just leave it out? What does it actually do?

Thanks

---

