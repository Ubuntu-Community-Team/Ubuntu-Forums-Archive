---
title: "VLC shuts down immediately"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by orengolan on 2007-12-01
after upgrading to 7.10 my VLC stopped working-
it opens and closes immediately before playing the video.

when I run It from the command line I get this (I copy pasted the last lines):

```
b7cd3000-b7d07000 r-xp 00000000 08:03 3703818    /usr/lib/libdbus-1.so.3.3.0
b7d07000-b7d08000 rw-p 00033000 08:03 3703818    /usr/lib/libdbus-1.so.3.3.0
b7d08000-b7d09000 rw-p b7d08000 00:00 0 
b7d09000-b7d14000 r-xp 00000000 08:03 3705896    /usr/lib/libhal.so.1.0.0
b7d14000-b7d15000 rw-p 0000b000 08:03 3705896    /usr/lib/libhal.so.1.0.0
b7d15000-b7edc000 r-xp 00000000 08:03 3706196    /usr/lib/libvlc.so.0.0.0
b7edc000-b7ee3000 rw-p 001c7000 08:03 3706196    /usr/lib/libvlc.so.0.0.0
b7ee3000-b7ee7000 rw-p b7ee3000 00:00 0 
b7ee7000-b7ee9000 r-xp 00000000 08:03 3784724    /usr/lib/vlc/audio_filter/libheadphone_channel_mixer_plugin.so
b7ee9000-b7eea000 rw-p 00002000 08:03 3784724    /usr/lib/vlc/audio_filter/libheadphone_channel_mixer_plugin.so
b7eea000-b7ef1000 r-xp 00000000 08:03 4424445    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7ef1000-b7ef3000 rw-p 00006000 08:03 4424445    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7ef3000-b7efa000 r--s 00000000 08:03 4638813    /usr/lib/gconv/gconv-modules.cache
b7efa000-b7efb000 r--p 00000000 08:03 3784782    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7efb000-b7efd000 rw-p b7efb000 00:00 0 
b7efd000-b7f17000 r-xp 00000000 08:03 4390927    /lib/ld-2.6.1.so
b7f17000-b7f19000 rw-p 00019000 08:03 4390927    /lib/ld-2.6.1.so
bfa3f000-bfa53000 rwxp bfa3f000 00:00 0          [stack]
bfa53000-bfa55000 rw-p bfa53000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

---

### Post by holch on 2008-01-02
Same problem here. Did you find a solution?

---

### Post by orengolan on 2008-01-02
I haven't searched because Totem works ok.
let me know if u figure it out.

thanks

---

