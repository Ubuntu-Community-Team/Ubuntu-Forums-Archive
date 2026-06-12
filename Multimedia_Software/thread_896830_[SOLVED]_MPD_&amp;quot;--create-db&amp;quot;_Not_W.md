---
title: "[SOLVED] MPD &amp;quot;--create-db&amp;quot; Not Working"
date: 2008-08-21
forum: Multimedia Software
---

### Post by Sammm_ on 2008-08-21
I just switched from Ubuntu to Xubunutu (I use ratpoison and smaller apps, so I didn't need the gnome bloat clogging up my hard drive) and now mpd doesn't work.

I run "mpd --create-db" it looks like it's adding all my music to the database but "mpc search" isn't showing any results and there's nothing in the sontana libary. I know the config file works because I was using it about an hour ago, any idea what's going on or how I can find out what's causing the error?

**Edit:** just checked error.log, it says "Aug 21 15:58 : problems opening state file "/var/lib/mpd/state" for writing: Permission denied" I'll see if changing the permissions fixes it all.

Well I don't know wether it was changing the permissions on that file, or just turning my computer off and on, but it works now.

---

