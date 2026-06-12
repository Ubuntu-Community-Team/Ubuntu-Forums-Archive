---
title: "HowTo: Stop Firefox from Opening Movies with Totem"
date: 2009-02-26
forum: Multimedia Software
---

### Post by Akkifokkusu on 2009-02-26
OK, this is my first real Ubuntu-related post here. This is something that just got to me, that when I downloaded, for example an AVI file, if I doubled-clicked (or whatever) to open it in the Firefox downloads window, it would automatically open with Totem. The annoying solution is to open the folder where the movie was downloaded to and open it from there.

So, I tried Googling for a solution. I tried just about everything, from simply changing Firefox's preferences to editing the mimeTypes.rdf file. Nothing seemed to work.

So, on a whim, I tried this:

```
sudo rm /usr/bin/totem
```

Of course, I made sure it was a symlink and not an actual binary (I was pretty sure it wasn't, but I double-checked just in case).

Anyway, next time I tried double-clicking the file in Firefox, it gave me that "Which Application" dialog. I chose VLC (/usr/bin/vlc), and checked the box to always use it with this file type. I tried it again, and it automatically opened VLC.

Now, I don't really plan on using Totem for anything. But I also don't want to get rid of it and deal with the "ubuntu-desktop" annoyances. Also keeping it for those "just-in-case" scenarios seems like a good idea, anyway.

Like I said, I don't plan on using Totem. But I was also kinda wary as to whether deleting the symlink would kill some functionality somewhere. So, before I found out the hard way, I decided that maybe if I restored the symlink NOW, Firefox would still keep the association.

Well, apparently Firefox doesn't care about associations when dealing with specific filetypes. Because once I restored the symlink, it was back to immediately launching Totem. So, bah, if I ever need Totem, I'll find some other way. On the bright side, once I re-removed the symlink, VLC was the default again.

If anyone has any better solutions that I may have missed (and that might cover more than just Totem & movie files), the floor is yours.

---

### Post by Akkifokkusu on 2009-03-02
An alternative, I guess, is renaming the symlink, but that really only if you plan to keep using Totem, or need it for other programs, in which case you need to change the file they point to either way.

---

