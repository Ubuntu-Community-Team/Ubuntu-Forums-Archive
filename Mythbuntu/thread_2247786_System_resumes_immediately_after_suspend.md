---
title: "System resumes immediately after suspend"
date: 2014-10-10
forum: Mythbuntu
---

### Post by Jason_Gauthier on 2014-10-10
Hey Everyone,

 A few years back I was putting my backend into S3 sleep state while there wasn't usage.  I ended up increasing my storage by adding an external USB drive. Unfortunately,  that ended my suspend days (see [here]("http://ubuntuforums.org/showthread.php?t=1780012")).

I've removed all my external USB drives, and migrated everything to a network NAS.  Now, I'm back to suspending.. but not.

The machine resumes immediately after suspend.  I've spent a goodly amount of time trying to figure out why, and I've not had any luck.

Basically, I am doing these steps before the suspend:
Stooping the GUI
Stopping the backend
Stopping lirc
Unloading the nvidia modules
Unloading the hdpvr modules for lirc/v4l
Disabling all USB interfaces

After this, I took it a bit further and removed all the modules that had a 0 use, with the exception of the network adapter.
Still, resumes.

I'm looking for further suggestions on what could be causing this to resume, or if the kernel would tell me that would be great.
But, the kernel doesn't seem to tell me. (that I can find)

Thanks!

---

