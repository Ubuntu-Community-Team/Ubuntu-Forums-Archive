---
title: "Nvidia GeForce4 MX 4000 - Black screen after installation of Nvidia Driver"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by Kasper42 on 2008-01-27
I've tried installing various nvidia drivers yet after rebooting I seem to get a black screen after the ubuntu bootup screen.

I have installed the 9639 Driver manually by downloading from the nvidia website, this resulted in a black screen. I then tried the 9631 driver (from nvidia.com) which also gave a black screen after bootup; I had previously used the 9631 driver with no problems on previous ubuntu distros.

I then went on to install Envy and uninstalled the previous nvidia driver. I have tried to install the correct driver through Envy automatically, it selects the  96.43.01 driver which also gives me a black screen after bootup.

I am currently using the nv driver but I was wondering what I should do to run the nvidia driver :confused:

Thanks

---

### Post by ajgreeny on 2008-01-27
Try the **Restricted Drivers Manager** in **System>Administration**.  I don't have an nvidia card so have no idea if it will work that way, but it must be worth an attempt if you've not already done so.

---

### Post by Kasper42 on 2008-01-27
Whoops, sorry forgot to mention that ajgreeny, I tried that the Restricted Drivers Manager first which gave me a black screen after it installed 'nvidia-glx.'

---

### Post by Kasper42 on 2008-01-28
I tried deleting the nvidia files from /lib/linux-restricted-modules/<my kernel>/ and then reinstalling the 9631 driver ( the 9631 driver has worked on my card before) but I once again was greeted by a black screen. :(

Anyone any ideas? Could there be drivers that I have installed before interfering with new installations?

---

### Post by spyckotic on 2008-01-31
Don't worry, your not the only one with this problem.  Many of us are suffering from this issue.

check out this thread [http://ubuntuforums.org/showthread.php?t=615215&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=615215&highlight=nvidia)

there is also many threads at the nvidia forums on this issue as well.  So far there has been no solution unfortunately.  This has been happening for quite some time with no resolution.

---

### Post by DarinB on 2008-02-28
reinstall your etc file and get your screen back
then remove all nvidia drivers except for the common nvidia driver all else should be removed completely

---

