---
title: "Computer sees Creative Zen player, but programs do not"
date: 2010-01-04
forum: Multimedia Software
---

### Post by tegnoto89 on 2010-01-04
I'm trying to get my Creative Zen V Plus working.  Ubuntu sees it when I plug it in, and suggests programs to open it with.  Also, it shows up under "$lsusb", but when I tried using gnomad2 and kzenexplorer, they couldn't find any jukeboxes.  Also, rhythmbox doesn't show any players.  Can somebody help me?

---

### Post by tegnoto89 on 2010-01-07
Okay...  Nodoby helped me.  I solved it myself- I had to unmount the device before gnomad would see it for some reason.

---

### Post by granny6989 on 2010-01-12
Somewhere around Intrepid development or so, Gnome thought it would be fun to completely re-design the mount process. They went ahead and changed it so that the Zen gets a full time mount under gvfs, which mounts it as a camera or some such nonsense. With it mounted, any program which actually looks for it can't find it.

I contacted Gnome, etc - and supposedly this is the way it has to be to make the Zen more 'available' to more programs. The reality is, it does not work this way in Windows, or anywhere else, and so far, none of the programs that actually work with the Zen recognize it while mounted to the filesystem. So, YES, for the foreseeable future, the only way to get a Zen to show up is to plug it in, let it mount, unmount it, and then open the program that connects to it. 


Kind of like:

"Hey guys, I made this really cool cart, but it takes a horse to pull it. Anyone ever seen or heard of a horse before?"

;)

---

### Post by vifillr on 2010-01-19
My creative Zen automatically mounts when connected via USB. I unmount it and then starts gnomad - and then it works. Thanks!

---

