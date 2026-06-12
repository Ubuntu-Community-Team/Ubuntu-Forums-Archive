---
title: "m3u files are run as scripts?"
date: 2011-04-22
forum: Multimedia Software
---

### Post by Zevaka on 2011-04-22
Hello, i have a weird problem in my ubuntu 10.10
i can't open .m3u file properly by double click on it.
when i double-click, menu appears (menu which is common for executable files): "run, run in terminal, show, cancel"
of course, running it won't do anything since m3u is just plain text file with list of files or paths.

Clicking "show" opens m3u in Totem (defaul VIDEO player).
But i want m3u to open in my default audio player!

in file preferences there's tickbox "allow running this file as program" that cannot be unticked. Really, even with root priviledges, i untick it  but it becomes checked again within seconds.

whatever audio player i set as default for .m3u files, the problem remains

oh and yes, any other ways to open m3u work perfectly: rmc-open in, or via audio player's "open file" menu, or by drag-n-dropping m3u onto audio player interface. everything work except the most natural thing: double clicking on it (or it's equivalent, hitting enter button)

---

### Post by nomko on 2011-04-22
What you need to do is right click on such file and select properties in the pop-up menu. Then when the properties menu appears, select tab "Open with". There you should see some programs which are capable of opening a m3u file like Totem or Vlc or Smplayer. If not, click on the button calles "Select program" (or such like, i use the Dutch version of Ubuntu). Then select the required program in the menu which has appeared. Then click on Ok and again on Ok.
 
What you can also do is remove the other programs visible in the "Open with" tab which cannot handle./open a m3u file.
 
Now it should work!

---

### Post by Zevaka on 2011-04-22
yeah, i tried that in first place. didn't change anything

---

### Post by Zevaka on 2011-04-27
solution for those who's searching
1) this happens only to m3u's that are stored on ntfs and usual chmod commands do not work in ntfs filesystem. 
2) what i had to do is to go to nautilus preferences, and uncheck option that in english should be something like "run text files as scripts". Yes, there is such option there and yes, m3u files are basically text files

nothing to add.

---

