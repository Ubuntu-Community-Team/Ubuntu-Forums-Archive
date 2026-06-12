---
title: "Amarok 2 will not search my music folder."
date: 2009-10-23
forum: Multimedia Software
---

### Post by RichardUK on 2009-10-23
Amarok will not find the mp3's in my music folder. It will play an mp3 if I open the file manually but the collection part just will not find anything when I tell it to search the folder.

The folder is a mounted network drive using smbfs.

---

### Post by vinutux on 2009-10-23
Try other players like songbird or banshee....

---

### Post by wii552 on 2009-10-23
not really sure, but the fact that the folder is a network drive might be something. Shouldn't be, though

---

### Post by meho_r on 2009-10-23
> **RichardUK said:**
> Amarok will not find the mp3's in my music folder. It will play an mp3 if I open the file manually but the collection part just will not find anything when I tell it to search the folder.

The folder is a mounted network drive using smbfs.

Amarok 2.1 or 2.2?

Try some local folder too. Maybe it's smbfs+Amarok issue.

---

### Post by RichardUK on 2009-10-23
It's version 2.0.2

Other players can search the folder fine but i'll like to try Amarok first as it seems to get good reviews and I'm not 100% happy with the way the others display my music lib, all 6189 tracks of it.

---

### Post by RichardUK on 2009-10-23
> **wii552 said:**
> not really sure, but the fact that the folder is a network drive might be something. Shouldn't be, though

Yes that is my thought, I should copy some folders over to the local drive and see if that works ok first.

---

### Post by meho_r on 2009-10-23
You may try upgrading Amarok to version 2.2 (but first I'll advise to go to #amarok at irc.freenode.net and ask if there's any issue with smbfs). Amarok 2.1 had totally messed up everything regarding managing collections, but in 2.2 things are sorted out.

BTW, if you're searching for a real power, you may give [gmusicbrowser](http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html) a try. It may look a little bit complicated at first sight, but after setting a layout and playing with it a little, you get the most powerful audio player ever ;) Scanning, managing and navigating through extensive audio collection (over 10,000) is where it beats any music player you can think of.

---

### Post by RichardUK on 2009-10-24
> **meho_r said:**
> You may try upgrading Amarok to version 2.2 (but first I'll advise to go to #amarok at irc.freenode.net and ask if there's any issue with smbfs). Amarok 2.1 had totally messed up everything regarding managing collections, but in 2.2 things are sorted out.

BTW, if you're searching for a real power, you may give [gmusicbrowser]("http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html") a try. It may look a little bit complicated at first sight, but after setting a layout and playing with it a little, you get the most powerful audio player ever ;) Scanning, managing and navigating through extensive audio collection (over 10,000) is where it beats any music player you can think of.

Thanks for the tip, I'll go check it out. :)

Seems may not be an issue when used with an smbfs share as a local folder does not work either. Odd thing the files now show up in the "files" pain, were not before. But the collection still fails to do anything so may be some dependency I'm missing.

Thanks for your help.

---

### Post by meho_r on 2009-10-24
> **RichardUK said:**
> Thanks for the tip, I'll go check it out. :)

Seems may not be an issue when used with an smbfs share as a local folder does not work either. Odd thing the files now show up in the "files" pain, were not before. But the collection still fails to do anything so may be some dependency I'm missing.

Thanks for your help.

There was a huge discussion and bug-hunting regarding behaviour of collection manager in Amarok 2.1 (you may take a look [here](http://forum.kde.org/viewtopic.php?f=115&t=74657)). After extensive testing and reporting results, one of Amarok's developer noticed a problem with mysql and the bug was corrected in 2.2. It is possible that Amarok 2.0 suffered the same.

---

### Post by RichardUK on 2009-10-24
I'm liking Exaile, got version 0.2.14 from the repository. Works a treat. :) I think I'll stick with that for now.

Many thanks for your help guys.

---

### Post by vinutux on 2009-10-25
> **RichardUK said:**
> I'm liking Exaile, got version 0.2.14 from the repository. Works a treat. :) I think I'll stick with that for now.

Many thanks for your help guys.

I like that app too... its light weight.... and simple.....:)

---

