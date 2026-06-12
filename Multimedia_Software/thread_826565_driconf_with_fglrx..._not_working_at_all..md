---
title: "driconf with fglrx... not working at all."
date: 2008-06-12
forum: Multimedia Software
---

### Post by Twilight in Zero on 2008-06-12
Hi, guys. I'm trying to use driconf to configure some settings for my ATI Radeon Xpress 1150 in my laptop, using the fglrx driver. I stumbled upon driconf while looking for something to fix a tearing problem (probably VSync related) that I was experiencing while playing Cave Story and ZSNES, and also when rotating my desktop cube.

ZSNES runs terribly too, so I was hoping that maybe driconf could help with that too.

Except I can't get driconf to start in anything other than expert mode. It gives the following message when I start it: "Could not detect any configurable direct-rendering capable devices. DRIconf will be started in expert mode." If I start it from the terminal, "Driver "fglrx" is not installed or does not support configuration." appears, and then a bunch of deprecation warnings appear after I click away the message box.

I can't configure my card this way. I'm good with Windows computers, but I'm just starting to learn Linux. I'm no expert. Can anyone help me to get this working properly?

If it's any help, I've attached a .txt duplicate of my xorg.conf file.

EDIT: Forgot to mention: Direct Rendering is yes, and the output of fglrxinfo is good (no mesa stuff).

---

### Post by Twilight in Zero on 2008-06-12
I hate bumping, but I don't like being ignored either.

---

### Post by sim-value on 2008-06-12
Why not use amdcccle ?

---

### Post by Twilight in Zero on 2008-06-12
You mean the Catalyst Control Center? It does nothing useful. The vsync setting there has no effect. And as my computer runs right now (under Ubuntu, that is; performance is great in Windows), messing with the other settings there (the only ones being anti-aliasing and anisotropic filtering) is useless.

My computer performs abysmally under Ubuntu. I was hoping to get that to run just to fix my vsync problem, but any steps I take to getting driconf to run (as well as actually running it) may be means to a greater end.

---

### Post by markbuntu on 2008-06-12
You need to be using aticonfig. There is some useful info about how to make changes here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by Twilight in Zero on 2008-06-13
Actually, I've followed that guide word for word. I had to change a few things to stop videos from flickering, though. I did recently update to Catalyst 8.5, so I may try to do the things in there again.

---

### Post by markbuntu on 2008-06-13
I did too and what I found was the best preformance as far as window flickering and full screen play went was to set TexturedVideo "off" for my HD3650 1GB.

Other than that, it made my general screen performance much better and took a lot of the load off the cpu and put it on the gpu where it belongs.

---

### Post by Twilight in Zero on 2008-06-14
I wish I could say something like that.

I actually resorted to trying out the radeon driver. Now that's a fantastic piece of work. It ran ZSNes wonderfully, at full speed. And there was no tearing, either! But compiz really stunk on it. It was very slow.

With fglrx, the situation is totally opposite. Compiz is great, but I have the tearing, and 3d apps are slow.

I want the best of both worlds. I want good compiz and good 3d games. I know it's possible. But what should I do?

EDIT: And no, turning off Compiz makes NO difference.

---

### Post by madmed on 2008-06-20
I have exactly the same problem with driconf! I need it to fix some issues withe google earth. help plz!!

---

