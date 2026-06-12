---
title: "Problems Installing Ubuntu 8.04.1 on my Toshiba L300 1AM"
date: 2008-12-30
forum: Multimedia Software
---

### Post by SlyBlyahoff on 2008-12-30
Hello everybody, 

I am sorry for posting new thread on this, but I really couldn't find some similar to this one. 
My problem: 
I've downloaded ubuntu 8.04.1 firstly for 64bit (I have Toshiba L300-1AM-2g, Intel Dual-Core, 2G, Intel GMA). It didn't work out. 
After that I've downloaded the same version for 32 bits, but unfortunately the same problem pops again. :( 
The exact problem: After I begun the installation progress runs until a certain point every time (loading with U logo) and after that my display starts looking like a crap with many different colours like the default resolution or frequency is way higher than supported. 
I've tried to change the installation options, but neither one seems to be related to the problem. 

PLEASE, give me some advise. 

P.S. Else I am running separated hard with Vista and Kubuntu 8.10 (both are really shitty and unstable, so I decided to turn back to the old buddy :) )

Best Regards,
Sly

---

### Post by Sealbhach on 2008-12-30
When it get's to that point try this:

Press Ctrl+Alt+F2 and login then.

Then do

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This might fix it for you.


.

---

### Post by SlyBlyahoff on 2008-12-30
Well, thanks for the help. I will try this one and will post back what happened later. 

Thanks again.

Best Regards,
Sly

---

### Post by SlyBlyahoff on 2009-01-17
Hello, I am sorry to bother again, but the upper written line didn't help at all. It prompts a message telling something like: 
Configuration file is not accessible. Some other process uses it. 

Do you know some other way to deal with this problem?? 
I also tried F4->Safe graphics, but it didn't work out too. :( 

Please help! I desperately need to install that Ubuntu :) 

Do you know if some other version will be compatible? 

Thanks in advance

---

### Post by zjaster on 2009-10-07
I too have the same problem - Toshiba L305-S5962. I'm trying to get CAElinux 2009 installed, which uses ubuntu 8.04 OS. I have the same issue while installing CAElinux OR Ubuntu 8.04x64

Ubuntu 9.04 works fine-

thanks!

---

