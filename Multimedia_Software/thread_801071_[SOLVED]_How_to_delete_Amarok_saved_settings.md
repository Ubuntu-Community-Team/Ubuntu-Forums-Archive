---
title: "[SOLVED] How to delete Amarok saved settings?"
date: 2008-05-20
forum: Multimedia Software
---

### Post by djdarrin91 on 2008-05-20
I run Ubuntu 8.04.And i use Amarok for my music needs.I don't know what happened but Amarok was working fine and all the sudden started being super slow and freezing.so i uninstalled it and reinstalled it but no good because amarok saves the settings etc :(how do i delete these settings and start fresh with Amarok:confused: Thanks in advance for any help:)

---

### Post by xc3RnbFO8P on 2008-05-20
/home/your folder/**.kde**/share/amarok
delete amarok folder

---

### Post by djdarrin91 on 2008-05-20
I went to /home/your folder/but there is no .kde file there. would it be somewhere else? And thanks for the quick response,i really like this program.

---

### Post by xc3RnbFO8P on 2008-05-20
Its a hidden folder.
Open home folder, in View > show hidden files

---

### Post by djdarrin91 on 2008-05-20
That Worked! Perfect! Thank you very much!

---

### Post by ben2talk on 2009-04-28
Actually - maybe a later modification - you should go to ~/ (home)
~/home/***username*****/.kde/share

then you'll find an APPS folder - similar to applications settings in winblows. 

I'd recommend taking care here, actually go into the Amarok folder and selectiveley delete stuff - at least don't delete folders like 'album covers' which take a long time to repair after reloading Amarok.

I cleared the scripts folder (because it was a pidgin script that killed mine) and then the text files - and it was like new again.

---

