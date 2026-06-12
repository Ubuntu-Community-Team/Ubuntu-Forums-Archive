---
title: "Maverick latest kernel 2.6.35-19 or 2.6.35-22?"
date: 2010-09-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by bprins on 2010-09-24
Hi,

Short question, what is the latest kernel in maverick? Is it 2.6.35-19 or 2.6.35-22? I keep getting updates about 2.6.35-22 but if I ask uname -r I am still running on kernel version 19. 

```

bas@ubuntu-lt:~$ uname -r
2.6.35-19-generic

```

Also in /lib/modules I do have an entry for kernel version 22 but it's pretty empty:
```

**Version 19 contents**
bas@ubuntu-lt:~$ ls /lib/modules/2.6.35-19-generic/
build              modules.builtin.bin  modules.inputmap   modules.softdep
initrd             modules.ccwmap       modules.isapnpmap  modules.symbols
kernel             modules.dep          modules.ofmap      modules.symbols.bin
modules.alias      modules.dep.bin      modules.order      modules.usbmap
modules.alias.bin  modules.devname      modules.pcimap     updates
modules.builtin    modules.ieee1394map  modules.seriomap

```

```

**Version 22 contents**
bas@ubuntu-lt:~$ ls /lib/modules/2.6.35-19-generic/
build              modules.builtin.bin  modules.inputmap   modules.softdep
initrd             modules.ccwmap       modules.isapnpmap  modules.symbols
kernel             modules.dep          modules.ofmap      modules.symbols.bin
modules.alias      modules.dep.bin      modules.order      modules.usbmap
modules.alias.bin  modules.devname      modules.pcimap     updates
modules.builtin    modules.ieee1394map  modules.seriomap

```

Am I missing something here? Is something going wrong? What is the status of 2.6.35-22? Should I do something extra to get version 22 activated?

Thanks in advance!

---

### Post by tad1073 on 2010-09-24
```
:~$ uname -r
2.6.35-22-generic

```

---

### Post by cariboo on 2010-09-24
Have you updated grub, so that it points to 2.6.35-22?

---

### Post by koso on 2010-09-24
Maybe stupid question, but have you restarted your system after kernel update?

---

### Post by bprins on 2010-09-24
I've manually installed version 22 and it seems to work. Did you also install it manually or did it came with normal ubuntu updates? If so, why didn't it come automatically here?

Thanks

---

### Post by cariboo on 2010-09-24
When a kernel is installed via updates, it automagically runs update-grub, did you notice this happening when you manually installed the kernel?

---

### Post by bprins on 2010-09-24
Thanks for the reply. 

I'm not 100% sure but I am sure it tried to install the kernel. I can only remember that something behaved strange during the updates of grub, but I was a bit too excited and rebooted right after the updates were finished (ubuntu did ask for a reboot so I thought it installed the kernel properly).

I don't want to make an issue out of nothing. If I am the only 1 with this issue its probably nothing and just an error between keyboard and user... :). And after all, it seems to work.. Don't know. A bit strange but "f**k it" I guess :).

---

### Post by bprins on 2010-09-24
> **koso said:**
> Maybe stupid question, but have you restarted your system after kernel update?

Not a stupid question, but thank god I'm not that stupid :). I did :P

---

### Post by bprins on 2010-09-24
Since I am risking any form of credibility for the rest of my forum-time already :P...

Is there a way to manually "update grub" or configure grub? The only thing I found is the startup manager, but that doesn't really allow me to configure grub.

Is there a tool that makes configuring grub easy (command line or via UI)?

thanks again.

---

### Post by scradock on 2010-09-24
If you run the code:
```
sudo update-grub
```
in a terminal, grub will re-generate the grub.cfg file, and print out a line for each flavor/kernel of linux found. Check that the .35-22 kernel is there - it should be the top line (actually, the top two lines) or very close to the top.

One problem that can arise is if you are near the end of a long alpha/beta testing sequence: you may have half a dozen or more different kernels listed in grub.cfg, and therefore in your boot menu. The best way to fix that is to remove all but the latest 2 using synaptic or your favorite alternative.Keeps the clutter down.

HTH

---

### Post by cariboo on 2010-09-24
Synaptic has been pretty good about removing old kernels over the last few weeks, I've gotten an obsolete or unused notification, after that last few kernel updates.

---

