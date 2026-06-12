---
title: "Manually configure screen resolution"
date: 2008-09-03
forum: Multimedia Software
---

### Post by jmeissen on 2008-09-03
I know this has been hashed to death. I've searched the forums and read how-to's like [https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto"), so far with mixed results.
My problem is that my monitor sits behind a KVM, so it's not detected. (the card is an ATI X300 that's detected fine. I'm using the 'ati' driver that was installed with the system) It's a Dell widescreen 1680x1050, and I had it working perfectly in an old Mandriva install which I'm trying to replace with Ubuntu 8.04LTS. Copying what I thought were the relevant parts of the old xorg.conf file didn't seem to help much.

What I have accomplished: 
I managed to get Gnome to configure the correct resolution, so it's usable in that environment.

The problem:
I don't particularly care for Gnome. It's pretty, and all the system tools are nicely integrated. But it's big, it won't let me do things like assign arbitrary keys to arbitrary actions and there are things that just don't work well with it (like xterms with transparent backgrounds). And screen resolution isn't really a session thing, it's a global hardware configuration.

I'd like to try alternatives, like FVWM. But GDM insists on bringing up X in 1360x768 mode. If anyone can help me figure this out I'd greatly appreciate it.

I'll try to attach my current xorg.conf file.... it's not very big.

---

### Post by Bablefish on 2008-09-03
I tried the same thing, and all I managed to do was crash my video drivers. I fixed it though.

---

### Post by jmeissen on 2008-09-04
Well, I think I understand what's happening, but I still don't know how to fix it.

If I understand the logs correctly, the X server is loading the right drivers/modules and configuring the correct screen. But in spite of me specifying the exact modeline that I want it still probes for the monitor. Since this KVM appears as a generic analog monitor it reverts to some VESA setting.

After Gnome loads it uses some API to cause the X server to reconfigure according to its specific settings.

Any idea how to get the X server to stop probing for the monitor type?

---

### Post by tukuyomi on 2008-09-04
You might want to pick an eye on this topic: [http://forums.debian.net/viewtopic.php?t=26577](http://forums.debian.net/viewtopic.php?t=26577)
Please give some feedbacks :)

---

### Post by jmeissen on 2008-09-06
That did it. Once I added the line

 [INDENT]Option      "PreferredMode"      "1680x1050_60" [/INDENT]

to the Monitor section it now always starts up in the correct mode.

("1680x1050_60" is the identifier string for the modeline I specified)

Thanks, everybody. Now I can get on to trying the other window managers.

Is there any way  to do serious customizing to Gnome? It's not bad, but I'm used to assigning various keyboard shortcuts to arbitrary commands and window actions, and the integrated configuration won't let me do that.

---

