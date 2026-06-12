---
title: "error opening X... (help needed, am a nebie)"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by Tiago_ on 2006-06-03
Hi,
I just installed Ubuntu 6.06 on my notebook (Toshiba 2805-S302). It works fine while boot "live", but once I've installed it and rebooted, it gives the following error: "error opening security policy file /etc/X11/xserver/SecurityPolicy"
Actually, there no such directory /xserver/ under X11.

Anyway, I'm totally new to Ubuntu and would like to be able to get really into it (I enjoyed it a lot "live").

I hope you can give me a hand with this...

T_

---

### Post by tseliot on 2006-06-04
[QUOTE=Tiago_]Hi,
I just installed Ubuntu 6.06 on my notebook (Toshiba 2805-S302). It works fine while boot "live", but once I've installed it and rebooted, it gives the following error: "error opening security policy file /etc/X11/xserver/SecurityPolicy"
Actually, there no such directory /xserver/ under X11.

Anyway, I'm totally new to Ubuntu and would like to be able to get really into it (I enjoyed it a lot "live").

I hope you can give me a hand with this...

T_[/QUOTE]
Try this quick fix.

1) Boot in Recovery mode (you can select it from the GRUB menu almost as soon as you turn your computer.

In this way the xserver won't be started.

2) Reconfigure the Xserver:

```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver when it asks you. If you don't know the answer to the other questions just press ENTER to use the default answer.

3) Restart your computer:
```
reboot
```

Boot as usual and you should be able to see the graphical interface (the desktop enviroment).

If that doesn't work, repeat the process I described above but this time set the driver to "vga".


P.S. After you're able to use the Desktop Environment I suggest you to install the right drivers for your graphic card in order to make the most of it.

---

### Post by Tiago_ on 2006-06-04
Hi tseliot!
Thanks for the reply. Unfortunately, I tried both options, but I get the same error... any other idea?
I'm going to try to re-install Ubuntu and see how it behave.
T_

---

