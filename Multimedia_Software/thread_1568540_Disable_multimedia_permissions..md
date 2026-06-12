---
title: "Disable multimedia permissions."
date: 2010-09-05
forum: Multimedia Software
---

### Post by abominable on 2010-09-05
Hello to everyone.

I am looking if possible for a way to disable multimedia permission/abilities for certain users on my system. I don't know if it is called like this, but what I actually I want to do is this.

There are certain users on my system, that I want them to have the permission for using graphic interface, but not the permission/ability to watch videos, play music, etc.

Is there any way to manage this;

Thank you in advance for any help.

---

### Post by garvinrick4 on 2010-09-05
> **abominable said:**
> Hello to everyone.

I am looking if possible for a way to disable multimedia permission/abilities for certain users on my system. I don't know if it is called like this, but what I actually I want to do is this.

There are certain users on my system, that I want them to have the permission for using graphic interface, but not the permission/ability to watch videos, play music, etc.

Is there any way to manage this;

Thank you in advance for any help.Give those directorys only permissions to
certain users or groups. Read up on chown and chmod and users and groups. I take it you
are root or administrator. Lots of reading material to google or pdf manuals to download.
Or man chmod or man chown.

---

### Post by abominable on 2010-09-05
Thanx, I'll check on these commands, but for which directories should I be looking for ?

---

### Post by garvinrick4 on 2010-09-05
> **abominable said:**
> Thanx, I'll check on these commands, but for which directories should I be looking for ? The directorys in your home.

rick@rick-laptop:~$ ls
Desktop    Downloads         Mac4Lin_v1.0  Pictures  Templates
Documents  examples.desktop  Music         Public    Videos
rick@rick-laptop:~$ 

You want to not let some users in these directorys correct.

---

### Post by abominable on 2010-09-05
Well, I don't have concerns about accesing my files (I have them locked). But what I dont want, is them to turn the server into a home cinema station. So I want to restrain them from opening mplayer/vlc etc.

I know that the best would be to talk to them, but believe me this is not an option.

---

