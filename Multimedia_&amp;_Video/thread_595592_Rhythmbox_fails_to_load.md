---
title: "Rhythmbox fails to load"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by jeighty7 on 2007-10-28
Hey all,

I cannot count how many times this forum as helped me. It truly is a great resource.

But alas, I have an issue that I cannot find an answer to by searching.

Earlier today, I upgraded from fiesty to gutsy. Everything went pretty smooth. Upon reboot, Rhythm box didn't work. So I went into Synaptic and completely removed it. Then I went and deleted the .rhythmbox folder and the rhythmbox wolder in my home folder. Reinstalled and still no joy. I ran "rhythmbox -d" in terminal and here is the output:

(21:52:28) [0x80fb408] [rb_debug_init_match] rb-debug.c:153: Debugging enabled
(21:52:28) [0x80fb408] [main] main.c:171: initializing Rhythmbox 0.11.2
(21:52:28) [0x80fb408] [rb_threads_init] rb-util.c:460: GMutex isn't recursive
(21:52:28) [0x80fb408] [main] main.c:179: going to create DBus object
(21:52:28) [0x80fb408] [main] main.c:322: THE END

Any ideas guys? I'm using Banshee right now, but I still like the interface of Rhythmbox more.

---

### Post by jeighty7 on 2007-10-29
I removed rhythmbox via synaptic (again) and the icon for rhythmbox is still in the Sound and Video menu. I would hate to go ahead deleting stuff when I am not entirely sure what to delete. Any insight?

...and now Banshee crashes when I try to play a song. Any song.

---

