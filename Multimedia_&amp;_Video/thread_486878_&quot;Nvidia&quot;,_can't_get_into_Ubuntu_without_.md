---
title: "&quot;Nvidia&quot;, can't get into Ubuntu without edit to &quot;vesa&quot;!"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by Dag J. on 2007-06-28
Hello, I'm Dag.

First of all I found my way to Ubuntu from Windows XP and I've used Linux before but many years ago, so you can say I'm pretty dumb right about now about all of this.

First of all I've checked with my own language forums about this issiue, they failed to fix my problem.

**Here we go!**
I'm currently in the graphic Ubuntu now but in some config file I had to change to "vesa" to enter Ubuntu graphic mode you know.

I've got NVIDIA GeForce 7800GTX and I seems like I can't use it? I don't know what is wrong.
I've got 2GIG RAM, AMD Athlon 64 +3500 2.1GHz

**I have try'd:**
Installing NVIDIA driver and it seem to complete, but still I cannot enabled Desktop 3D effects!
I changed my config file thing, in it - from "vesa" to "nvidia" and reboot then I get same problem as the beginning, can't enter the graphic mode of Ubuntu because of trouble with driver, NVIDIA, etc.

Please, somebody help me.

---

### Post by dabl on 2007-06-28
Hi Dag, and Welcome.

> **Dag J. said:**
> 
Installing NVIDIA driver and it seem to complete

Wow, that's not very confidence-inspiring.  After you thought it installed, and either re-booted or restarted the X server with Ctrl-Alt-Backspace, did you see a pretty green and black Nvidia logo-splash, right before you logged in again?

For newbies, a pretty effective approach to getting your Nvidia driver installed is to download and run the Envy script installer.  Get it here : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
It doesn't always work for me in GUI mode, so after installing it, I just run it in text mode from the console by typing ```
sudo envy -t
```

Hope this helps!  :)

---

