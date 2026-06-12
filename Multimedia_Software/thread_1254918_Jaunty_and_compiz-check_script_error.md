---
title: "Jaunty and compiz-check script error"
date: 2009-08-31
forum: Multimedia Software
---

### Post by ApEkV2 on 2009-08-31
Recently I upgraded to 9.04 64bit. The problem is back in 8.10 compiz-check returned no errors whatsoever, but now I get

[color=red] Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) [/color]


As you can see I obviously have no rendering method (whatever that means)
Does this relate to all the failures my 9.04 system is having?
How do I get my precious rendering method back?

Other than the desktop recorders not working for me since 7.10, the following programs fail randomly: ffmpeg (converting formats) doesn't work,
flash video is glitchy (youtube), totem randomly refuses to play videos and music, startup scripts fail on startup (random occurrences), apache freezes after performing a server restart.

---

### Post by ApEkV2 on 2009-09-01
Now compiz doesn't work at all (no cube or any other settings)
only 300mb is being loaded into the ram on startup (usually was 500mb)

I have nothing good to say about this release of Ubuntu, its just been a disaster so far

---

### Post by ApEkV2 on 2009-09-01
I"M DONE WITH UBUNTU
freaking now it can't execute root functions
damn Jaunty is a disaster

here's the error

Error copying '/home/mccarty/.Xauthority' to '/tmp/libgksu-NzbO3b': Permission denied

here's strace gksudo synaptic

[color=red] file or directory)
open("/home/mccarty/.icons/Human/index.theme", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/icons/Human/cursors/xterm", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/icons/Human/index.theme", O_RDONLY) = 16
fstat(16, {st_mode=S_IFREG|0644, st_size=7586, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fca2894d000
read(16, "[Icon Theme]\nName=Human\nComment=U"..., 4096) = 4096
close(16)                               = 0
munmap(0x7fca2894d000, 4096)            = 0
open("/usr/share/pixmaps/Human/cursors/xterm", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/X11R6/lib/X11/icons/Human/cursors/xterm", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/mccarty/.icons/Tangerine/cursors/xterm", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/mccarty/.icons/Tangerine/index.theme", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/icons/Tangerine/cursors/xterm", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/icons/Tangerine/index.theme", O_RDONLY) = 16
fstat(16, {st_mode=S_IFREG|0644, st_size=6853, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fca2894d000
read(16, "[Icon Theme]\nName=Tangerine\nName["..., 4096) = 4096
close(16)                               = 0 [/color]

And it continues like this forever pretty much

---

