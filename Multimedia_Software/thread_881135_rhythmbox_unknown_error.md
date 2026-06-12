---
title: "rhythmbox unknown error"
date: 2008-08-05
forum: Multimedia Software
---

### Post by cooltd825 on 2008-08-05
whenever I try to play a music file, I get an unknown playback error.  it's not my media, because I can navigate to my folder (on a Windows partition) and manually select songs to play and they will play.  this problem is not only with Rhythmbox either.  I can replicate the same error on Amarok and (my favorite) Banshee.  this is unfortunate, because now I can only listen to my music and videos through Vista.

---

### Post by Sarastro on 2008-10-14
I am currently experiencing the same frustrating problem.  Most of my music files from my server play normally but there are a few albums that just do not play on any Ubuntu machine (I have one 8.4 and one 8.10), a few are not visible in the play index.  I suspect a problem with Gstreamer but have not yet been able to isolate the problem.

Even correcting some problems with the Metadata has not fixed the situation.  Interestingly, the Rhythmbox library, while displaying the bulk of my files, shows a somewhat different listing when I switch the server connection from a direct Samba connection to a mt-daapd connection and neither list all available files.

This will take time and patience.

---

### Post by Sarastro on 2008-10-17
One way to eliminate "unknown playback errors" is to rebuild your rhythmdb.xml file.

1.  Use the search function to delete the file (found here):  /home/<user>/.gnome2/rhythmbox/rhythmdb.xml

2.  Let Rhythmbox rebuild the file


I received the "unkown playback errors" after shuffling my music files a bit for better organization.  Rebuilding the data base corrected the problem.

Unfortunately, there is no way to rebuild the index without deleting it and starting over which can take some time on a Samba share.

---

### Post by EliteBlack on 2009-02-24
When i searched for that in the directories it can't be found.

---

### Post by asuastrophysics on 2009-04-08
i already did this last night and now it's doing it again. am i gonna have to delete this file every time i launch rb???

---

### Post by uriel1998 on 2010-12-08
> **EliteBlack said:**
> When i searched for that in the directories it can't be found.

```
/home/USER/.local/share/rhythmbox/
```

---

