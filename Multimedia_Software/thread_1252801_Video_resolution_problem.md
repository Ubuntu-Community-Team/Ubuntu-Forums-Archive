---
title: "Video resolution problem"
date: 2009-08-29
forum: Multimedia Software
---

### Post by orange2k on 2009-08-29
I have an Nvidia card and it works fine, but I cant get the resolution to be remembered across boots. I set it with Nvidia X server settings to 1280x1024 but when I reboot it goes back to 1024x768. What should I do?

---

### Post by argos3016 on 2009-08-29
Nvidia is a trademark, then the controlers of you must use is privatives.
Go System->Administration-> Hardware Controllers and Ubuntu will be detect the controllers.
Follow the instructions on screen and hypothetically Nvidia will be right.
Yes?

---

### Post by jim_naisium on 2009-09-26
I am having the exact same problem with 9.04 as Orange2K, this is a brand new system that I just built that has a nVidia PCI-e video card in it.

I boot up and find the resolution at 1024x768, then I go into /System/Administration/NVIDIA X server settings/ then go into the configuration settings and switch it to "1280x1024" it switches and everything works great, then if I reboot or shut down when it boots up the next time the resolution is right back on 1024x768 again.

I thought maybe this was a problem with my KVM switch so I completely bypassed it and plugged the monitor right into the video card but it is still doing it.

Aargos3016: I do not have anything called: "System->Administration-> Hardware Controllers".

Any suggestions?

---

