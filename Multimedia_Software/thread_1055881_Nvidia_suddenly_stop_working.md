---
title: "Nvidia suddenly stop working"
date: 2009-01-31
forum: Multimedia Software
---

### Post by s0mmer on 2009-01-31
Hi everybody,

After turning on my thinkpad t61p this morning, i got the famous warning about linux running in low-graphics mode because nvidia kernel module couldn't load. I may remember, there were some new updates yesterday i installed. What have caused this problem? And how do i fix it? I cant do much in the nvidia server settings. Just says i should run nvidia-xconfig in console, but didnt help. I also noticed when i run hardware-drivers my nvidia drivers isnt activated, and i cant activate them anymore?

And oh ye im running ubuntu 8.10

Could you please help me..

---

### Post by jason0x21 on 2009-02-07
Was there a kernel upgrade in the upgrades you did?  I've found that moving from linux-image-2.6.24-22-generic to linux-image-2.6.24-23-generic on Hardy caused the nVidia drivers to stop loading.  I'm still trying to figure out why, though.

---

### Post by themusicalduck on 2009-02-07
Reinstalling the NVidia drivers might fix it if you haven't tried already.

---

### Post by 4ebees on 2009-02-16
> **jason0x21 said:**
> Was there a kernel upgrade in the upgrades you did?  I've found that moving from linux-image-2.6.24-22-generic to linux-image-2.6.24-23-generic on Hardy caused the nVidia drivers to stop loading.  I'm still trying to figure out why, though.

Yes!

I updated by daughter's machine and had to revert back to linux-image-2.6.24-22-generic and reinstall the driver for an nVidia FX5200. 

It was a complete pain in the ****!

I'm surprised there are not more posts about this.

---

