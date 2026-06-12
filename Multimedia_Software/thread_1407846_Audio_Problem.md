---
title: "Audio Problem"
date: 2010-02-15
forum: Multimedia Software
---

### Post by Cooter2543 on 2010-02-15
I have searched these forums as well as other sites for a solution, but none seem to work for me.

My sound stopped working last night. The volume control is gone, and when I try to go into System > Preferences > Sound, it tells me "Waiting for sound system to respond," indefinitely until I cancel it. According to lspci, it sees my sound card (00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02).

Looking in my Log Files under syslog, it is repeating this every 5 or 6 seconds:

*(Date, time and my name)* pulseaudio[19186]: module.c: Failed to load  module "module-alsa-source" (argument: "device=hw:1,0"): initialization failed.
"             " pulseaudio[19186]: main.c: Module load failed.
"             " pulseaudio[19186]: main.c: Failed to initialize daemon.
"             " pulseaudio[19181]: main.c: Daemon startup failed.

I have tried reinstalling pulseaudio, upgrading alsa, deleting ~/.pulse, and various other things recommended elsewhere with no avail. I have a recording session coming up in a couple days, and this computer is our recording studio. I would rather not have to downgrade back to windows, especially since I have been boasting to my friends about how great Linux is.

---

### Post by Cooter2543 on 2010-02-15
I powered down my computer and switched the sound card to a different pci slot. When I booted back up, the sound magically worked again. I don't know why or how, but to anyone reading this that has tried everything else, you may want to try what I did.

---

