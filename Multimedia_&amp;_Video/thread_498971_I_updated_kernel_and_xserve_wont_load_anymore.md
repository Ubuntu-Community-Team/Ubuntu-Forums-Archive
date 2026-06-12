---
title: "I updated kernel and xserve wont load anymore"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by FoolFromHell on 2007-07-12
I updated the kernel from the -15 to -16 and now xserve wont reboot. Grub still has the -15 on the list, so i can still use the old kernel.
I am a newbie, but can follow instructions.
I have an 8800GTX, so maybe the drivers arent working. Xserve still loads on the old kernel.
I tried reconfiguring xserve and it asked me to choose drivers, etc. I used the "nvidia" drivers. not "nv".
Does sudo apt-get install nvidia-glx-new?
Or something like that?

---

### Post by thespinesplitter on 2007-07-12
first let me explain to you that the kernel is loaded just once as the system boots, it is the heart of the operating system think of it as the glue that holds everything together,   whats happening here is that every time you updgrade the kernel you must recompile the nvidia kernel module (this is my experience with ATI cards BTW), in any case you should follow some isntructions on installing the proprietary nvidia drivers

---

### Post by thespinesplitter on 2007-07-12
it helps to look at the error that the xserver chrash reports, in the linux world logs are your "bestest" freinds :)

---

