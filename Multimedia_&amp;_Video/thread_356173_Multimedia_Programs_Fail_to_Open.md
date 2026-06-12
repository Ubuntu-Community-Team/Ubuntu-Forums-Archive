---
title: "Multimedia Programs Fail to Open"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by agrajagzz9 on 2007-02-08
Hi

I'm not so sure that this post is in the right forum, but the problem has only happened with multimedia players so far...

Anyway, the problem is that when i tried to open Kaffeine, a bar appears in the taskbar and a bouncing icon appears beneath the cursor as usual, but after a minute or so the bar and icon disappear and kaffeine has failed to open. I tried rebooting the computer and then completely purging and reinstalling kaffeine with no luck.

Then, later that night, amarok shut down without warning and for no apparent reason. When I tried reopening the program, the same thing happens as described above. :confused: 

By the way, i'm using Kubuntu 6.10 with all the latest updates.

Ideas, anyone???

---

### Post by RomeReactor on 2007-02-08
I suggest opening the programs from the command line: Open Konsole and type **kaffeine** and try to open a file. If it crashes, look at the output in the terminal, as it might give you a hint to what's wrong. Same for **amarok**. Post the output of both if they crash.

---

### Post by rahjman on 2007-02-08
Once I had the same problem. Running from console does not solved it. Becouse when I run it on command line, nothing happened. Kaffeine didn't opened and no any messages on console. Completely removing didn't worked too. So I go to the home directory (~.kde/share/apps) and deleted the kaffeine directory. I tried to open kaffeine and it worked:lolflag:

---

### Post by agrajagzz9 on 2007-02-08
rahjman was right, opening with the shell does nothing. deleting the folders in .kde/share/apps seems to have worked for amarok although sometimes it still won't open and all my playlists and album art is gone :( . Still no luck for kaffeine though :( :(

---

