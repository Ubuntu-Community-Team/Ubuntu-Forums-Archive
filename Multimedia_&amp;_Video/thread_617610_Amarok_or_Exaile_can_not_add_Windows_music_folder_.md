---
title: "Amarok or Exaile can not add Windows music folder to collection"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by madeinbrazil on 2007-11-19
Hello, I am now a happy dual boot Windows and Gutsy Ubuntu user!

I've installed Amarok and Exaile and tried to add my music files to the collection but can't in either programs (my preference for now is to use Amarok). All of my music is on Windows folder NTFS partition (/MyMusic) and neither one of these programs do I see that folder listed when I'm trying to build my Collection.

For now I'd rather not switch my music files to Ubuntu's partition since then Windows won't be able to read it.

If I want to play individual files I can see the Windows directory fine, but not when I try to build the Collection.

Any help here?

---

### Post by Mithrilhall on 2007-11-19
If you issue a

```

ls -la

```

Who's listed as the owner? root:root or youruser:youruser?

---

### Post by madeinbrazil on 2007-11-19
Thanks for the reply Mithrilhall,

meuser:meuser is shown for Exaile, couldn't see Amrok on the list.

By the way, I am complete noob on Linux so pardon if I these questions are stupid. :)

---

### Post by madeinbrazil on 2007-11-19
Anyone with guidance?

---

### Post by Mithrilhall on 2007-11-19
What are the permission on the "/MyMusic" directory?

---

### Post by madeinbrazil on 2007-11-20
Its also locked to the owner. But when I try to "Build collection" from Amarok it doesn't see anything from Windows, only if I choose "add media" to play individual songs.

---

### Post by thechilipepper0 on 2008-02-16
i had the exact same problem until literally just about 5 minutes ago. it's so obvious considering how ubuntu has structured windows partitions, i'm kind of upset i didn't notice it earlier.

anyway, when you click on build collection, you get that menu of ubuntu locations. expand the 'media' folder. you should have some sda options. one of those will be your windows hard drive. from there you can navigate as if you were in windows. i've got amarok to see My Music as its home folder. i'm pretty sure it's not altering it.

it's there, just a little hidden. now i pretty much have ubuntu set up the way i want it, and i'm mostly happy. the only problem is the ctrl+shift+<direction> won't select an entire word. i'm working on that...

---

