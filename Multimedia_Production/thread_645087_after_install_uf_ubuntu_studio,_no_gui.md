---
title: "after install uf ubuntu studio, no gui"
date: 2007-12-19
forum: Multimedia Production
---

### Post by rwarwarwa on 2007-12-19
Hi there,

I just installed Ubuntu Studio from a checked confirmed healthy DVD. All went well but upon start up it doesn't go to a GUI, only the terminal. 

I read a response to a similar issue that said type in startx on the command line. I did that, loaded the dvd in as requested. it then set up mcpp, xauth. xrb. xinit and installed new version of config file /etc.X11/Xsession.options and config file /etc.X11/Xsession ...

I then typed in cat /etc/X11/xorg.conf as suggested by the same person and it said no such file or directory.



Thanks,

rwa

---

### Post by Stochastic on 2007-12-19
try running ```
sudo apt-get install ubuntu-desktop
```

---

### Post by rwarwarwa on 2007-12-20
Hi,

Thanks for the hint. I have done that and it has now stopped after an extensive install. 

I'll give you the last paragraph it gave before it stopped. 

Setting up ubuntustudio-desktop (0.11) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
__@ubuntu-___: $  * Reloading system log daemon...

So that is where it has stayed now for at least a half hour.

Thanks for any help,

rwa

---

### Post by Stochastic on 2007-12-20
what happens after you reboot?

---

### Post by rwarwarwa on 2007-12-20
Hi there,

It started up nicely. Thanks so much.

rwa

---

### Post by mpgarate on 2007-12-20
that happens to me with the rt kernel. I just have to choose the generic in the grub menu before startup, kind of a pain.

---

