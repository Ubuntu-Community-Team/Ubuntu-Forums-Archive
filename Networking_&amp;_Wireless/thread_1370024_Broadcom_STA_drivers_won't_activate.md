---
title: "Broadcom STA drivers won't activate"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by gonzogonzo on 2010-01-01
Hello hello.

I have a wireless PCI card that was running the restricted proprietary Broadcom STA drivers. After a new installation, I have tried to get those drivers again and succeeded. Unfortunately, when I go to activate the driver, it prompts me for my password, downloads and installs the driver, but never activates or prompts me to reboot my computer for the driver to take effect. Why won't it activate? I have been at war with this infernal machine for days now and this is the last step to get it fully operational for my use. If I don't get this fixed, **there will be blood.**

Thank you for any help you can give me.

---

### Post by Gramps on 2010-01-01
If your not plugged into ethernet it will go through the motions but not really do anything. Plug into ethernet then try it. You will need to reboot when finished.

---

### Post by gonzogonzo on 2010-01-01
> **Gramps said:**
> If your not plugged into ethernet it will go through the motions but not really do anything. Plug into ethernet then try it. You will need to reboot when finished.
Currently my ethernet cable is plugged in directly to my computer and I'm still having the same problem.

---

### Post by gonzogonzo on 2010-01-01
BUMP!!!!

I need help! the gui refuses to acknowledge that I've activated the driver! What is the problem?!

---

### Post by Ferretti on 2010-01-01
I'm not 100% sure that this will work, but it worked for me. To fix it, I went to System > Administration > Software Sources then checked the box that said "CDROM with Ubuntu 9.10 (Karmic Koala). Then I opened Synaptic Package Manager and searched for "bcmwl-kernel-source" and installed it. After a reboot, everything works perfectly. Hopefully this will work for you too. Best of luck!

---

### Post by gonzogonzo on 2010-01-01
> **Ferretti said:**
> I'm not 100% sure that this will work, but it worked for me. To fix it, I went to System > Administration > Software Sources then checked the box that said "CDROM with Ubuntu 9.10 (Karmic Koala). Then I opened Synaptic Package Manager and searched for "bcmwl-kernel-source" and installed it. After a reboot, everything works perfectly. Hopefully this will work for you too. Best of luck!
Unfortunately I think my CD-ROM drive might be on the outs. Is there anyway I can point the package manager to a USB drive instead? I try and reinstall, with the disc in my drive, and it never reads the disc's info. Computer even says the disc is mounted... Ugh. Anyway, can you reroute software sources to go to usb?

---

### Post by bkratz on 2010-01-01
Here is the directions that the last poster was referring too. 

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

It your wired connection is operational you could find that bcmwl------ in the actual repositories rather than on the live CD.

---

### Post by gonzogonzo on 2010-01-02
It is just one thing after another!

Now, when trying to activate the driver, I am getting this error with a message saying the driver installation failed. Should I just try an earlier distro? This is a nightmare! 

```
/var/log/jockey.log
```

---

