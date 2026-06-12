---
title: "Real Player Seg-faults in Lucid (AMD64)"
date: 2011-03-14
forum: Multimedia Software
---

### Post by dg0 on 2011-03-14
RealPlayer will work for several minutes, then it will seg-fault out of the blue. I am wondering if it has to do with the fact that it cannot load the certain 32-bit libraries (I have them installed,) because it is searching in /usr/lib instead of /usr/lib32.

I need RealPlayer because it seems to be the only player that will properly play rm files (mplayer will work, but the picture will get scrambled and the audio is a very choppy.)

Also, I installed RealPlayer from the .deb on real.com using the --force-architecture flag (I tried the one in the repositories, but it hardly worked at all.)

Here is the terminal output:

```
** (process:2467): WARNING **: Unsupported locale en_US.utf8! Please use a locale with .UTF-8 suffix! For example: export LANGUAGE=en_US.UTF-8

/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/bin/realplay: line 76:  2467 Segmentation fault      $HELIX_LIBS/realplay.bin "$@"

```

Any help would be greatly appreciated.

Thanks

---

