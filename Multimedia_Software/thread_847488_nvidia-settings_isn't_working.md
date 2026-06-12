---
title: "nvidia-settings isn't working"
date: 2008-07-02
forum: Multimedia Software
---

### Post by msimpson3 on 2008-07-02
Hello,

I'm running Ubuntu 8.04 Hardy Haron with 2 17" Acers Nvidia 8600 GT graphics card dual core 3.0 processor 4 gigs. So I know it's possible to have dual monitor setup, but how to enable it without compromizing the yummy eye candy that compiz has shown me!?!

I try to start nvidia settings but when it loads it prompts me saying:

```
You do not appear to be using the NVIDIA X driver. 
Please edit your X configuration file (just run `nvidia-xconfig` 
as root), and restart the X server. 
```

So I do what it tells me, run sudo nvidia-xconfig and reboot and it boots up fine, but it did not fix the issue.

Thanks,
Matt

---

### Post by feenicks on 2008-07-02
Look under System, Administration, Restricted Drivers and check if the nvidia driver is enabled.

---

### Post by johnsto on 2008-07-02
Try 'sudo nvidia-settings -c :0'

---

### Post by msimpson3 on 2008-07-03
It's not enabled, in fact there isn't even an option for me to activate or enable any restricted drivers.  Just blank.

I will try this when I go back into work - will be monday.

> **johnsto said:**
> Try 'sudo nvidia-settings -c :0'

Thanks for the help.

---

