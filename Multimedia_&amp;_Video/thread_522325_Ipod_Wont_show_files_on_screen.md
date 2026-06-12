---
title: "Ipod Wont show files on screen"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by IceReaver75 on 2007-08-10
My sister added some files to her ipod through Rhythmbox.  Rhythmbox detected the ipod and all songs on it.  She transfered the songs she wanted on there to the ipod and it said transfer complete.  Ejected the ipod and it said safe to remove media.  After she ejected the ipod all the files on the ipod screen don't show up.   It like there is nothing on there at all.  If you redock it Rhythmbox shows the ipod but no music files show being shown in the libary.   But if you explore it while docked off the desktop icon all the music on there is showing that it is there but it wont show on the ipod screen.   Anybody know why that is.

---

### Post by kostkon on 2007-08-10
I happened to me when I got my iPod. When I tried to transfer songs to my iPod for the first time ever I used *Rhythmbox* and nothing happened. Then when I explored my iPod's contents I saw that *Rhythmbox* had put the songs inside their own folders and not inside the *iPod_Control* folder where they were supposed to be put. Also, it did not update the *iTunesDB* file.

I have read that you have to initialise iPod in *iTunes* first in order to make it work with other programs. I did not have *iTunes* available so I used *gtkpod*. After putting some songs to the iPod with *gtkpod* I tried also with *Rhythbox* and everything worked just fine.

I don't know if your case is the same, I mean if your sister has used iTunes.

Anyway, you can try with *gtkpod* to see if the transfer will work. Another option is *Amarok*, which is a very good media player. You can install all these programs from *Synaptic*.

Finally, another good option and the one I use, a very good replacement for *iTunes* is [Floola]("http://www.floola.com/") which you can download from its site.

---

### Post by IceReaver75 on 2007-08-10
Yeah the ipod was used on i-tunes first.   Thats how all the other songs where put on there.  I tried using gtkpod but it keeps saying there is no ipod availble even though it is docked to ubuntu according to the desktop at least.   All the other songs that were on the ipod already are showing up on the ipod if you explore it by double clicking the ipod icon on the desktop but wont show up on the ipod screen itself like they aren't there. Is there some trick to getting gtkpod to show the ipod as being there.  Sorry but I'm kind of new to Ubuntu and still don't know how to do everything yet.  Thanks for the help.

---

### Post by kostkon on 2007-08-10
In normal circumstances, the song files are supposed to be somewhere inside the *iPod_Control* folder. Thus, you have to just delete all the mp3s that are outside this folder. Rhythmbox, by mistake, has put the files in the wrong place.

I think you get an error in *gtkpod* because the mount point for iPod has changed in Ubuntu from **/media/ipod** (I think) to **/media/IPOD**. So, just open *gtkpod* and go to **Edit -> Edit Repository/iPod Options**.  There, from the drop down menu, on the upper left side, select **iPod**. Then just change the **iPod mountpoint** selection from **/media/ipod** (I assume) to **/media/IPOD**. Press OK, do a **Load iPod** and then it will be recognised. If you get the same error just close *gtkpod* and restart it, in case that the change did not take effect immediately.

I hope it will work. I recommend you to give also [Floola]("http://www.floola.com/") a try, if you don't care that it is a closed source application.

---

