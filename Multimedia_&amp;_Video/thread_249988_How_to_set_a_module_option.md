---
title: "How to set a module option?"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by Bourlotieris on 2006-09-03
While trying to find a way to make my Logitech Quickcam Zoom work under Dapper (it doesn't by default) I came upon the pwc module. It is supposed to make this camera work, however I haven't managed to do that (yet). There are instructions for mine specific model to put a module option: power_save=1. From where exactly am I going to set this option?

---

### Post by daou on 2006-09-03
Is the pwc a kernel module? If it is, then you have to put it into the kernel boot option.

In grub, for example, you edit kernel boot line by first pressing 'e' when highlighting Ubuntu, then highlighting the kernel option, again pressing 'e' and then adding the power_save=1 after the 'ro quiet splash' options, or whatever options you may currently have.

If it doesn't work it will give you an error, then just reboot and everything will be back to normal.
If it works, then add the option to your /boot/grub/menu.lst file.

---

### Post by Bourlotieris on 2006-09-10
All I had to do was to put a line like this:

```
options pwc power_save=1
```

in /etc/modprobe.d/options. Now it's working like charm!

---

