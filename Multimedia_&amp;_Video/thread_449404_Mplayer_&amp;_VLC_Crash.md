---
title: "Mplayer &amp; VLC Crash"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by the_maassk on 2007-05-20
Read from a post here and installed the xserver-xorg-driver-intel. Replaced i810 with intel in xorg.conf. Since then my Mplayer and VLC have started crashing :(

This is what I get in Mplayer  (am using xv output module) -

[I]X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0 

MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.[/I]

This is what I get in VLC - 

[I]X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
[/I]
XV was working fine earlier. I also tried reverting back to i810 in xorg.conf, reinstalled both mplayer and VLC..but does not work!

HELP!

---

### Post by the_maassk on 2007-05-22
Bump!

---

### Post by agim on 2008-01-23
I am getting the same vlc error. If anyone has any pointers I would appreciate it.

---

### Post by eye208 on 2008-01-24
Hardware video overlay (XVideo) does not work with Compiz. Either disable Compiz or set your media player to use OpenGL (if available) or X11 software rendering instead.

Don't be surprised if your videos look ugly in software rendering mode. There will be no anti-aliasing if you scale the video or switch it to fullscreen.

---

### Post by agim on 2008-01-25
Of course! If anything goes wrong, especially with video content, turn off compiz. I should know that.
Thanks

---

