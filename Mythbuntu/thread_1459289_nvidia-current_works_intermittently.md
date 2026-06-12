---
title: "nvidia-current works intermittently"
date: 2010-04-21
forum: Mythbuntu
---

### Post by falcon15500 on 2010-04-21
Hi all,

  As the subject suggests, I am having trouble with nvidia-current.  I am running an AMD socket micro ATX motherboard that has GeForce 8200 on board.

I was previously running 9.04 (or 9.10, can't recall) just fine and had even seen no trouble after updating to 10.04b2.  I didn't have it in this configuration for long, however.  I did a fresh install of 10.04b2 i386 and have had this trouble since then.

Basically, intermittently, when I boot up I will be presented with the failsafe screen advising that the nvidia drivers didn't respond.

Looking at the dmesg log (attached) nothing looks wrong.  Looking at the Xorg.log (also attached) nothing looks wrong until just after the "RENDER" directive.  It's here that the log complains about..

"(EE) Apr 21 20:15:33 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:2:0:0."

If I look at the associated logs under /var/log/gdm there is one extra line of info that isn't in the normal Xorg log and that is...

"NVIDIA: could not open the device file /dev/nvidia0 (Input/output error)."

Which appears just prior to the "Failed to initialize" line seen above.

I have tried fully removing and re-installing the driver.  Still the same.

Anyone? :)

M.

---

### Post by falcon15500 on 2010-04-22
Hey all,

  In the end I did (yet) another clean install and it's all working fine now.  Which really does my head in.  As far as I can see, everything is the same - yet it's working as good as gold.  Unfortunately this means I have no insights to offer for anyone else who comes across this - apart from doing a re-install.

M.

---

