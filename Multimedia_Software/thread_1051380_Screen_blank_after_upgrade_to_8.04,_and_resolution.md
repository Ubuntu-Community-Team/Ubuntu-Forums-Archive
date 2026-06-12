---
title: "Screen blank after upgrade to 8.04, and resolution change."
date: 2009-01-26
forum: Multimedia Software
---

### Post by davemar on 2009-01-26
I've just upgraded my old PC from 7.10 to 8.04, and it went pretty smoothly it first appeared. The only problem was the screen resolution was 1280x1024, not the 1600x1200 my monitor supports. The System->Preference->Screen Resolution didn't allow anything more than 1280x1024, even after adding 1600x1200 to the existing xorg.conf.

I started fiddling around installing Nvidia drivers, to get the right resolutions available, and it did seem to offer 1600x1200. So I did a reboot after the xorg.conf file was updated with the new nvidia settings. Now I just got a blank screen when I'm expecting the login screen. I can still use ctrl-alt-F1, or ssh from my other machine to do stuff. 

I decided to revert xorg.conf to the xorg.conf.failsafe version which I would hope would at least give me a low-res desktop, but nothing. I tried out an old pre-upgrade xorg.conf and that didn't work either giving this error in Xorg.0.log:
(EE) Failed to load module "type1" (module does not exist, 0)
I've also tried uninstalling all the nvidia stuff and keeping it all basic vesa stuff, but that doesn't work either. 

I'm totally stuck now! Can anyone help?

---

### Post by davemar on 2009-01-28
bump....

---

### Post by davemar on 2009-02-02
I've tried copying xorg.conf.failsafe to xorg.conf, and I still get a blank screen. Surely that should give me something, even if at a low resolution?

---

### Post by 73ckn797 on 2009-02-02
Maybe this info could be a help and starting place to figure it out:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by davemar on 2009-02-03
Decided to upgrade to 8.10 to at least get some desktop back. I'm back to 800x600 now, so back to square one.

Tried the instructions in that link, and still no joy. I'm getting utterly hacked off with this now. How hard can this be?

Is there a xorg.conf file I can copy, or modify? The one I seem to have ended up with seems a bit light, and has no resolution list in it. 

My card is a GeForce MX440, and I installed the driver according to those instructions, but I'm not sure if it is detected at all?

Has anyone got NVidia stuff working with 8.10, with simple easy to follow instructions to get it working? I've yet to see anything convincing.

I'm off to have a beer to cool off.  grrrr.

---

### Post by davemar on 2009-02-03
Refreshed after a beer....

Just to add; I get this error dialog popping up when logging in:

```
The following error was encountered. You may need to update
your configuration file to solve this.

(EE) Failed to load module "type1" (module does not exist,0)
(EE) Failed to load module "nvidia" (module does not exist,0)
(EE) No drivers available.

```

No matter how I fix the problem it mentions, it gets no closer to solving the actual problem...

---

