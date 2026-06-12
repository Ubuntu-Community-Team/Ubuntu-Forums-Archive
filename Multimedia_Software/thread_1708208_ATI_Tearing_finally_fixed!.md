---
title: "ATI Tearing finally fixed!"
date: 2011-03-16
forum: Multimedia Software
---

### Post by Milamber_Cubed on 2011-03-16
So I have been trying to solve this problem with fglrx driver for a while now and have come up short.

On a whim, I tried downloading the latest drivers today and essentially followed the process in this thread's first post: [http://ubuntuforums.org/showthread.php?t=1512915](http://ubuntuforums.org/showthread.php?t=1512915)

Now, I see a new option called "Tear Free" (see screenshot) which magically makes everything fine and wonderful. 

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=186265&stc=1&d=1300289630[/IMG][/CENTER]

Just discovered it and thought I'd share it in case someone is looking to solve ATI tearing issues because I couldn't find any mention of "Tear Free" anywhere.

---

### Post by xgt001 on 2011-03-31
could u pls share the download link for the drivers???? thanks :) cheers :)

---

### Post by Hoder on 2011-04-04
You can download the new drivers from AMD official site:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

In my case I had to deactivate the existing fglrx drivers (System -> Administration -> Additional Drivers) and run the installation package (after making it executable).

---

### Post by zigomir on 2011-04-10
Thanks for this! I'm staying on Linux because of that at the moment :)

---

### Post by pixeljunk on 2011-05-03
Don't mean to bump up a semi-old thread, but I was thrilled when I saw this feature.  ATI screen tearing has been one of the primary reasons I haven't made the jump to Ubuntu on my desktop.

However, as soon as I enable this feature, everything becomes incredibly choppy.  Opening and closing things, dragging windows across the screen, etc.  (Sort of like if you've ever tried running Windows without video drivers installed, for example.) 

Not sure what the cause is here.  I've been running Ubuntu on a netbook for a few years now and love it.  I'd prefer to run it on my desktop but the screen tearing issue has been a problem.  I've used the open source drivers and they're fine.  But I'd like to run some games from within Wine and need better performance.

---

