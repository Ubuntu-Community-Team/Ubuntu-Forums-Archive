---
title: "Rockbox"
date: 2008-05-10
forum: Multimedia Software
---

### Post by xdarkgokux on 2008-05-10
Hey guys i decided to install Rockbox on my Ipod...so i tried the automated install thing, but it says no ipods found when i click install.. I even restored my ipod to factory defaults, using Itunes on my Windows Comp..but it still won't work..Can someone plz help me?

---

### Post by jbaerbock on 2008-05-28
Well here is what I found the problem to be. For some reason rockbox needs sudo privelages in order to see the ipod correctly (odd I know). Personaly I did the manuall install because of that but if you are dead set on using the automatic install start rockbox utility in super user state. So do an alt+f2 and in the run dialogue type gksu nautilus. This will open a root version of nautilus. Then just go to where rockbox utility is and open her up and it should work.

---

### Post by jbaerbock on 2008-06-05
One thing I noted about RockBox is that it about halves my IPods battery life (from 8-9 hrs down to 3-4). Once RockBox improves a bit more I'll use it but untill then I just use GPodder for syncin podcasts with ipod factory software, rythmbox for music.

---

### Post by vikrant82 on 2008-06-05
You can tweak rockbox a bit, to get more battery life, 

If you browse music by database, keep database in RAM, Turn off auto update of database, You should manually update the database only when you have updated your music. Anything that touches HD in rockbox, takes up lot of battery juice. Reduce brightness, turn off audio presets and other sound processing plugins. Try to create playlists as much as possible. Use lighter themes with less scrolling effects so that maximum RAM is available for caching music. 

Basically it all boils down to how frequent are your hard disk accesses.  Once you are fully optimized, you can easily do 7 hours consistently on rockbox. On apple firmware I get 8-9 hours. So its getting near. I have read Rockbox does better than Apple firmare in terms of battery life on older ipods.

---

### Post by jbaerbock on 2008-06-05
I'm guessing my playing Doom didn't help it much either lol? I'll try those optimizations this weekend and see what I get, thanks for the advice.

---

### Post by Sirhanz on 2008-06-23
I am having the same problem with a IPOD MINI SILVER, I can install the rockbox base, game packs, themes, etc. But when I try to install the bootloader I get error message saying Ipods not found. I have attempted the previous post to no avail. Generally I was getting X errors while trying gksu nautilus, such as X server can not be reached or something like that. On an added note I am using Kubuntu not gnome, perhaps I'll try that yet. If anyone else is having similar problems or has a solution please let me know.

---

