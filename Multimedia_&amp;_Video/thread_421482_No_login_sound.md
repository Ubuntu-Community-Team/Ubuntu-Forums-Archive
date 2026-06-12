---
title: "No login sound"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by dbott67 on 2007-04-24
After upgrading through Edgy & Feisty, I noticed that I was having some weird sound problems:

1. At the GDM login screen I would hear the "drum roll" sound.
2. After logging in, I would not hear the **startup.wav** file, although I could hear it if I played it in "Beep" or other music program.
3. In **SYSTEM > PREFERENCES > SOUND > SOUND tab**, the sounds would **not** play.
4. In **SYSTEM > PREFERENCES > SOUND > DEVICES tab**, the **TEST SOUND** worked.
5. Most applications with sound worked (Beep, Totem, Flash video, etc.)
6. No sound in the games "Cube" or "Sauerbraten".
7. All applications worked previously.

After fiddling with the sound settings trying various suggestions in the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") thread, I totally buggered up my sound.  Oh well, a fresh install of Feisty never hurt anyone and I had my **/home** directory on a separate partition.

After the new install, I still had the 7 symptoms described above.

Thinking that it might be some sort of **.config** file remnant, I created a new user and everythng worked properly.  A-HA!  Comparing the user home directories, I noticed the presence of a **.asoundrc** file and another similarly named file.  After doing some research here about [what the file is for]("http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php") (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

Just figured I'd let people know in case they were suffering from a similar situation.

-Dave

---

### Post by achusonline on 2008-06-26
thanks, that worked perfectly. I had exactly the symptoms you described and after deleting .asoundrc file, the sounds were back up and running again at login. Thanks again

---

