---
title: "Realplayer sound problem in 8.10 64-bit"
date: 2009-04-08
forum: Multimedia Software
---

### Post by abds on 2009-04-08
Hi

When nothing else is running, realplayer works fine. However whan i have another software running like firefox then there is no sound in realplayer. Running from the command line I get the following output: 

/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
ALSA lib ../../../src/pcm/pcm_dmix.c:1008: (snd_pcm_dmix_open) unable to open slave

Any ideas on how I can resolve this? Any help would be greatly appreciated.

Thanks!

---

### Post by abds on 2009-04-09
Anyone?

---

### Post by abds on 2009-04-09
bump

---

### Post by abds on 2009-04-09
So I fixed the issue. Here is how i did it:

1. In realplayer go to Settings->Hardware. Under Audio driver select "OSS".

2. Edit /usr/bin/realplay and replace the line:
```
$HELIX_LIBS/realplay.bin "$@"
```
with 
```
padsp $HELIX_LIBS/realplay.bin "$@"
```

Now run realplayer and the sound should be working fine.

---

### Post by dmccasland on 2009-05-01
Hey ADBS,

That is the first solution to the stupid Ubuntu Realplayer problem that actually worked!  Thanks!  :)

BTW, I did this in Jaunty 9.04, which apparently has fixed all the other stupid sound problems found in 8.10.

---

