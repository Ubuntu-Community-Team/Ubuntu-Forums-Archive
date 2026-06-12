---
title: "Grip from source."
date: 2010-02-05
forum: Multimedia Software
---

### Post by chrispche on 2010-02-05
Hi,

I'm trying to install grip from source. I get this error message. Can anyone help. This is after running ./configure

checking for libgnomeui-2.0 >= 2.2.0... Package libgnomeui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeui-2.0' found
configure: error: Library requirements (libgnomeui-2.0 >= 2.2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
chrisc@chrisc-desktop:~/Desktop/grip-3.2.0$ 

Thanks.

---

### Post by chrispche on 2010-02-05
I think this question might be in the wrong forum. Mods?

---

### Post by mc4man on 2010-02-05
Well it's not in the wrong forum per se, (unless it belongs in Ab. Beginner...) I guess there's some presumption if you're going to compile you'd know to search what's reported not found in synaptic and install the -dev(s) if available.

Anyway you're looking for libgnomeui-dev

This would probably take care of all

```
sudo apt-get install libcdparanoia0-dev libcurl4-gnutls-dev libglib2.0-dev \
libgnome2-dev libgnomeui-dev libgtk2.0-dev libid3-3.8.3-dev libvte-dev
```

---

### Post by chrispche on 2010-02-07
Encoders are not working now. How do I uninstall something I installed from source? I'll try another ripper seeing as this one is not supported anymore anyway.

---

### Post by nothingspecial on 2010-02-07
Read the README.

Probably ```
sudo make uninstall
``` from the directory.

But not definitely

---

### Post by chrispche on 2010-02-07
I'll check it out. Cheers. Just to note I ended up using RipOff.

---

