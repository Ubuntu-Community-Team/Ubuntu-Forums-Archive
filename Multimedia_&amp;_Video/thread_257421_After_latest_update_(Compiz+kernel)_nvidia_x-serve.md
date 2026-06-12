---
title: "After latest update (Compiz+kernel) nvidia x-server don't start"
date: 2006-09-14
forum: Multimedia &amp; Video
---

### Post by VosaxAlo on 2006-09-14
Hi to all,

this evening I have applied all updates on my Ubuntu Dapper 6.06 system:
> - new Linux kernel 2.6.15-26-686
- all compiz packages (CSM 0.12, etc.)

I have rebooted the PC as requested after the kernel update, and now **the server X don't start anymore** !!!

_In the xorg log are present these error messages_:
> [COLOR="DarkRed"](II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found[/COLOR]

Any idea on what can I do to make my x server work again?

I have attached the entire xorg log file

many thank's

---

### Post by alphabeta23 on 2006-09-14
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/60433](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/60433)

"...Expect a new l-r-m package within 24 hours..."

---

