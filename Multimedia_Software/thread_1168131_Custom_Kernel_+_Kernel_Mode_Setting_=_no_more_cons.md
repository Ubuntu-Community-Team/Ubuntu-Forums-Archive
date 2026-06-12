---
title: "Custom Kernel + Kernel Mode Setting = no more consoles"
date: 2009-05-23
forum: Multimedia Software
---

### Post by jon.reeve on 2009-05-23
So I tried compiling my own kernel, based on the instructions I found here: [http://wiki.msiwind.net/index.php/Kernel_Mode-setting]("http://wiki.msiwind.net/index.php/Kernel_Mode-setting") 

but I've come up with a few problems. One problem is I've lost my consoles, i.e. Ctrl+Alt+F1, F2, etc. Also, I think the resolution of the terminal is off, judging from the startup text I get. Since I'm using kernel mode-setting, I don't know how to correct this anymore. Any ideas?

---

### Post by Kareeser on 2009-05-23
With Ubuntu?

As far as I know, even Karmic doesn't support kernel mode setting yet. Ideally, the kernel should fall back to the normal method, but it sounds like it's not...

Have you tried the Karmic Koala forum?

---

### Post by jon.reeve on 2009-05-28
Turns out this was a problem with VESA or something not being enabled by default in the .config. Anyway since then I upgraded to Karmic and this has solved the problem (though, unfortunately, created several others). 

Some info here:

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

