---
title: "How do I start X without -nolisten tcp?"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by Jengu on 2010-12-10
I'd like to use X remotely without ssh tunneling. I've read that this means X needs to be launched *without* the "-nolisten tcp" flag. I've edited my /etc/X11/xinit/xserverrc file to not include the flag and rebooted but X is still using it! I can tell because if I use ps to get the pid for X, and then run:

cat /proc/$the_pid_of_x/cmdLine

I can see the "-nolistentcp" still in there. Is it hardcoded somewhere? I grepped through everything in /etc and didn't find any other instance of it.

---

### Post by gmargo on 2010-12-10
Simple to find with grep:
```

$ sudo grep nolisten /etc/X11/*/*
/etc/X11/xinit/xserverrc:exec /usr/bin/X -nolisten tcp "$@"

```

---

### Post by Jengu on 2010-12-10
> **gmargo said:**
> Simple to find with grep:
```

$ sudo grep nolisten /etc/X11/*/*
/etc/X11/xinit/xserverrc:exec /usr/bin/X -nolisten tcp "$@"

```

In the OP I point out I've already changed that line. It still starts with it.

---

### Post by gmargo on 2010-12-10
You're absolutely right; I spoke too quickly.  I'll try to look further into it.

---

### Post by gmargo on 2010-12-10
Ok, here it is.  It's actually in the Help.

Create a new file **/etc/gdm/custom.conf** with this content:
```

[security]
DisallowTCP=false

```Then reboot.

---

### Post by Jengu on 2010-12-11
> **gmargo said:**
> Ok, here it is.  It's actually in the Help.

Create a new file **/etc/gdm/custom.conf** with this content:
```

[security]
DisallowTCP=false

```Then reboot.

Thanks, I'll give that a try :D

---

### Post by bingotailspin on 2012-06-05
If you don't have gdm, you can edit the lightdm configuration as described on [askubuntu]("http://askubuntu.com/questions/72812/how-to-disable-nolisten").  I am running Xubuntu 12.04 and this worked for me.

---

