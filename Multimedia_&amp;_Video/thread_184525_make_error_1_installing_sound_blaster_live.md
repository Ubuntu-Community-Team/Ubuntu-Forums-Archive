---
title: "make error 1 installing sound blaster live"
date: 2006-05-30
forum: Multimedia &amp; Video
---

### Post by tj54020 on 2006-05-30
Im trying to install my sound blaster live via the instructions in this post

[http://www.ubuntuforums.org/showthread.php?t=19307](http://www.ubuntuforums.org/showthread.php?t=19307)

everythign is fine and dandy until step four - make the package-  when i type

cd modules/alsa-driver && sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r)/ KVERS=$(uname -r)

i get this error message
[COLOR="Red"]
You don't have the compiler that your kernel was built with installed
make: *** [configure-stamp] Error 1[/COLOR]

now i realize this is probably something simple but im too new to know what its talking about.  i mean it honestly took me 3 days to figure out i needed to update the os before i could begin this modification.  what do i do next?  dont assume i know much cuz i know almost nothing about linux.

Thank you to all that took the time to read this.

---

### Post by hw-tph on 2006-05-31
The one big mistake in Ubuntu 5.10 is that the default compiler is not the same version as the one that compiled the kernel - if you compile kernel modules you must use the same compiler as the kernel was built with. So **sudo aptitude install gcc-3.4** and type **export CC=/usr/bin/gcc-3.4** before trying to configure or build any kernel module. This command sets the environment variable $CC to point to the 3.4 version of gcc (which was used to compile the kernel). All sane configure scripts should check the $CC variable to see what compiler to use.


Håkan

---

