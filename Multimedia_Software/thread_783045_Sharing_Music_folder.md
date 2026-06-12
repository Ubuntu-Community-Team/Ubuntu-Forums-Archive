---
title: "Sharing Music folder"
date: 2008-05-05
forum: Multimedia Software
---

### Post by ram100987 on 2008-05-05
I have a lot of Music in the Music folder but the problem is that when my fiase logs into her account they do not show up in her Music folder.  I've seen how to share folder over ssh, but how can I share folders simply between users on the same computer?

I'm sure this has been asked many times but I cannot manage to find it another.  Thanks in advance for helping.

---

### Post by dido89 on 2008-05-05
Why do you put that music in another folder?

---

### Post by Zorael on 2008-05-05
This is on the same computer, right?

Likely your music folder is located inside your user directory, which is only accessible to you and you alone. One solution would be to move said music collection elsewhere and give both you and your fiancée read and write permissions.

Then you could make [symbolic links](http://en.wikipedia.org/wiki/Symbolic_links) to that directory, making it *appear* like that directory is in fact located in **/home/*<user*/Music/**. I think you can right-click drag directories in Nautilus and then choose *link* in the menu that pops up, but I'm not certain. There are, of course, terminal commands to doing that.

---

