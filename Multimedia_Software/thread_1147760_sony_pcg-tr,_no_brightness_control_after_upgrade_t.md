---
title: "sony pcg-tr, no brightness control after upgrade to jaunty"
date: 2009-05-03
forum: Multimedia Software
---

### Post by scarf on 2009-05-03
on this sony pcg-tr3a laptop, i used to have brightness control in hardy and intrepid with Fn+F5 and Fn+F6, but that ability has disappeared now that i am using jaunty.  i can still control volume with Fn+F2 and Fn+F3, though.  when i remove AC power, the brightness does dim, and it goes back up when i plug back in AC power.

---

### Post by scarf on 2009-05-09
all, i think this is a bug and should be filed.  i will file a bug but i am not sure what package to file against?  can anyone point me in the right direction?

---

### Post by scarf on 2009-05-13
i have filed [bug 374571](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/374571) against the linux package.

---

### Post by Intertricity on 2009-07-20
I have the same problem, PCG-TR2A. Anyone found a fix yet?

---

### Post by Intertricity on 2009-07-21
I'm on 9.04 now, after doing some research, I found that I needed to have the sonypi module loaded. Here's a wiki page for getting sonypi up and running.

[https://help.ubuntu.com/community/SonyVaioBrightness](https://help.ubuntu.com/community/SonyVaioBrightness)

I've confirmed I've been able to change my brightness with spicctrl with this on my PCG-TR2A. Hope this helps someone. :)

---

### Post by scarf on 2009-08-11
when i tried to load the sonypi module, i got this in messages:

```

sonypi: Sony Programmable I/O Controller Driver v1.26.
sonypi: please try the sony-laptop module instead and report failures, see also http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
sonypi: probe of sonypi failed with error -16

```

then i installed spicctrl, and i can change the brightness manually with that command.

i'm not sure if i need sonypi module or not.  sony_laptop is already loaded.

it would be nice if Fn+F5/F6 worked again, but this is better than before.

thanks Intertricity!


edit: i just unloaded sonypi with "sudo modprobe -r sonypi" and confirmed it wasn't loaded any longer by grep'ing /proc/modules, and the spicctrl command still works.  so, it appears the sonypi module is not needed.

---

