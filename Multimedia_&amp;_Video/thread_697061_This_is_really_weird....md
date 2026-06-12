---
title: "This is really weird..."
date: 2008-02-14
forum: Multimedia &amp; Video
---

### Post by upthelum on 2008-02-14
I have a dual boot xp and ubuntu and when i boot into xp with the speakers/monitor plugged into mobo sound port thats fine. When i boot into ubuntu i have to move the plug into the sound cards port to get sound in ubuntu. I'm happy to have sound but it's starting to bug having to change the plug over every time i boot the other os. 
I cant see any settings for it in the bios too.
#-o

---

### Post by Gen2ly on 2008-02-14
This looks like an ALSA deal.  There are ordinarily pre-configurations for alsa drivers and specific cards but for the life of buddha forget where they are located.

---

### Post by upthelum on 2008-02-14
Its a creative audio pci sound card and asus A8V-VM SE board if thats any help.

---

### Post by Gen2ly on 2008-02-15
got it:

[http://gentoo-wiki.com/HOWTO_Compile_Kernel_with_ALSA#Configure_module_options](http://gentoo-wiki.com/HOWTO_Compile_Kernel_with_ALSA#Configure_module_options)

---

