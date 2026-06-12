---
title: "No splash screen on boot"
date: 2009-10-20
forum: Multimedia Software
---

### Post by zenkaon on 2009-10-20
Hello,

I have a ATI Technologies Inc RV280 [Radeon 9200 SE] graphics card and a Viewsonic 26" monitor running at 1920x1200 resolution.

During boot of ubuntu 9.04 I see no splash screen. This is very annoying when fsck runs its check of my hard disk, as I can't see what's going on.

Is there a way to fix this, or to do an old skool text display boot?

I really don't care about a text display boot, it only takes 40 seconds to boot my pc, I just want to see what fsck is doing

Cheers

---

### Post by iTheBadGuy on 2009-10-20
I had this problem, someone told me it might be resolutions/color depth problem. Try messing with StartUp-Manager and see if you can get a good resolution/color depth that works. I'm not sure if this will help you, but it helped me.

I installed StartUp-Manager from the Add/Remove.

---

### Post by zenkaon on 2009-10-20
Solved it. Really easy thinking about it.

Simply edit /boot/grub/menu.lst and remove splash from the kernel parameters.

Works a treat! I can actually see what's going on with boot and fsck.

---

