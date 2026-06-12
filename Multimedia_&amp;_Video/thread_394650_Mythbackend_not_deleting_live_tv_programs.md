---
title: "Mythbackend not deleting live tv programs"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by williammanda on 2007-03-27
I recently replaced a slave backend with another new slave backend and I have two issues:
1. I see in the console for the master backend that it is trying to delete the live tv programs for the slave that has been removed. It can't, but it continues to do this daily. The master backend also shows these programs under the manage recordings - delete recordings with 0 bytes. How can I correct this issue?

2. In the system status, there is still a listing for the removed backend slave's tuner. How can I get rid of that?

Thanks

---

### Post by barney_1 on 2007-03-27
I haven't encountered these issues before.  You might find more help at the unofficial mythtv forum:

[http://www.mythtvtalk.com/forum/](http://www.mythtvtalk.com/forum/)

---

### Post by newlinux on 2007-03-27
1. I've had this before. To fix it, I created a dummy file that has the same name as the recording (touch <filename> in the recordings directory). Then it finally had something delete.

2. You should be able to delete capture card in mythtv-setup. Did that not work? Since it is from the old slave backend, you may have to delete all the cards on the slave backend (or all the cards on all backends) and then re-add the one you want. But you should try deleting the individual card (I would try running mythtv-setup on the slave backend, selecting the card, and pressing d).

---

### Post by williammanda on 2007-03-27
newlinux 
2. You should be able to delete capture card in mythtv-setup. Did that not work? Since it is from the old slave backend, you may have to delete all the cards on the slave backend (or all the cards on all backends) and then re-add the one you want. But you should try deleting the individual card (I would try running mythtv-setup on the slave backend, selecting the card, and pressing d).

The entry for the tuner for the removed slave backend is there (on the master backend under system status - tuners) but the slave backend, no longer exists, so I can't delete it.
Thanks

---

### Post by newlinux on 2007-03-27
Is the tuner listed in mythtv-setup?

---

### Post by williammanda on 2007-03-27
The only place the tuner is listed is infomation center - system status - tuners. 
Thanks

---

### Post by williammanda on 2007-03-30
Does anyone know how to change / edit the database to fix the two problem I have?

---

### Post by majoridiot on 2007-03-30
phpadmin is a browser-based interface that will let you inspect, edit and fix databases.

install instructions can be found in the "what next" section of our ubuntu mythtv guides: [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by williammanda on 2007-04-10
Thanks to all for the advise! 
I ended up re-installing mythtv. It seemed the lesser of two evils. I don't want to be on the slippery slope, editing the database blindly. The install times are not bad now anyway.

The moral to the story is don't remove a slave backend without deleting the tuner and programs first.
Thanks

---

