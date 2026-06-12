---
title: "Isn't It Time To Rethink Linux's Sound Drivers?"
date: 2008-11-09
forum: Multimedia Software
---

### Post by SuperMike on 2008-11-09
For the last time on my laptop, I'm fed up with coming out of suspend mode and finding my sound halted and no fixes I've read thus far have helped me.

And I think I infer here that sound on Linux is only loaded into the kernel space, rather than a small library in the kernel and the rest loaded into user space. It would be great, essentially, if we could load and unload our sound drivers at will simply by bouncing a service much like I can do with my print drivers and to some degree my network drivers.

By the way, I have an Acer Extensa 4420 laptop and Ubuntu 8.04, if that means anything.

---

### Post by DrDagostino1 on 2008-11-09
I have had similar sound problems that I thought was the device driver but one day I stumbled upon an interesting fix quite randomly. All I did was set all the playback devices in the sound preferences to ALSA and all my sound problems were fixed! Just go to System>Preferences>Sound to do this.

---

### Post by psyke83 on 2008-11-09
> **SuperMike said:**
> For the last time on my laptop, I'm fed up with coming out of suspend mode and finding my sound halted and no fixes I've read thus far have helped me.

And I think I infer here that sound on Linux is only loaded into the kernel space, rather than a small library in the kernel and the rest loaded into user space. It would be great, essentially, if we could load and unload our sound drivers at will simply by bouncing a service much like I can do with my print drivers and to some degree my network drivers.

By the way, I have an Acer Extensa 4420 laptop and Ubuntu 8.04, if that means anything.

You should search on Launchpad (or file a bug) for your specific issue.

You *can* "unload" and "reload" your sound card driver - it's a kernel module. The only caveat is that an active session can prevent the modules from unloading, though it's possible to force this action...

The command "lsmod | grep snd" will give you an idea of the name of your kernel module.

See the ALSA homepage for information on your card, and the man pages of "modprobe" and "rmmod" for general information on loading and unloading kernel modules.

---

