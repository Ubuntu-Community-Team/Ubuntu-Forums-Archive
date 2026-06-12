---
title: "Syncing iPod Nano 8G"
date: 2008-12-21
forum: Multimedia Software
---

### Post by sp00ner on 2008-12-21
I have searched and read many threads concerning syncing the NANO 4th gen with Ubuntu. I have tried Amarok, Rhythmbox, Banshee, and GTKpod. None of them seem to work. They all see the device and "appear" to transfer the songs. The songs do get transferred to the IPOD_Control\Music folder, but when I eject the device and goto Music it always shows 0 songs. Can anybody help me? I really dont want to resort to using Itunes on my Windows machine.

---

### Post by sputnikkk on 2008-12-25
Christmas Day and daughters new nano = No Joy.

Jobs and his crew seem to have the ipod nano's formatted for Mac out of the box?

I suspect I need to sync the little beastie with a windows install of iTunes, then try to connect it to a linux ubuntu install and see where we go.

problem is ... this new nano requires iTunes 8.0 on windoze - guess what ...iTunes 8 only for Win Xp or Vista.  Only win machines are win 2k around here in this house.

I'll go Ubuntu before Visat/XP ...

Now what?

---

### Post by doktaru on 2008-12-25
> **sp00ner said:**
> I have tried Amarok, Rhythmbox, Banshee, and GTKpod. None of them seem to work. They all see the device and "appear" to transfer the songs.

Songbird ([http://getsongbird.com/](http://getsongbird.com/)) lists compatibility with 4th gen iPod nanos, though I have not tried it yet.

---

### Post by bttb on 2008-12-25
4G Nano works with gtkpod/libgtkpod from SVN. If your Nano is formatted for Mac you could hook it up to a Win32 box up and change it to Windows format (you could also get a firmware update while you're at it, latest is 1.0.3). You'd need iTunes 8.x for the iPod Nano 4G.

---

### Post by Matt 6:27 on 2008-12-26
I've the same device and the same issue (including a joyless daughter).  If I find a solution, I'll be sure to post.

---

### Post by jfd5xte on 2008-12-26
The gtkpod and libgpod from svn **DO WORK** with the 4th generation iPod Nano. (New gift in my house as well).

FYI... the steps I used for this are:
[LIST=1]
[*]Uninstall rhythmbox
[*]Download SVN of gtkpod & libgpod. The command for this is: ```
svn co https://gtkpod.svn.sourceforge.net/svnroot/gtkpod gtkpod
```
[*]Used synaptic to install several development tools which are not pre-installed in Ibex-- started w/ autotools. Configure error messages helped along the way.
[*]With the SVN version of gtkpod & libgpod: ```
./autogen.sh ; make ; make install
```
[*]Then downloaded source for rhythmbox, synaptic installed **many more** development libraries, and recompiled rhythmbox to enable the latest version of libgpod.
[/LIST]

Now, I have a (98%) working rhythmbox. Plays music, rips CD's, and I can transfer music & pictures to the new iPod Nano.

My only remaining problem-- and this should hopefully be a really easy fix-- is getting the cover art plugin back. For some reason, the plugin is not listed under "Edit -> Plugins..."

---

### Post by jjvenkit@uwaterloo.ca on 2008-12-28
> **doktaru said:**
> Songbird ([http://getsongbird.com/](http://getsongbird.com/)) lists compatibility with 4th gen iPod nanos, though I have not tried it yet.

I just tried songbird with a brand new 16GB iPod nano fourth gen and it worked without any issues.  The iPod was already plugged-in and mounted when I started songbird.  It found the iPod and when I dragged mp3 files to it, the files were transferred and would play.

Now the iPod seems to be initialized and both Rhytmbox and songbird will work.

jason.

---

### Post by ezsurfer on 2008-12-29
My 16GB new iPod Nano is also working fine, but there is no sync I can find.  I will admit, my first light off with the Nano was on a Windows machine, after that, no issues at all.

Drag and drop files from just about anywhere into the Music Listing. Once I had that edited to everything I wanted, I just did a selection of the entire Music Listing, and dropped it onto the iPod.  

iPod screen says "syncing" and when complete, all the mp3s are there.

I'll be ripping and then trying out that tonight.

The album cover art works for each album for me, which is a great feature. (now if it was only large enough to read...

---

### Post by Dorkess on 2008-12-29
> **doktaru said:**
> Songbird ([http://getsongbird.com/](http://getsongbird.com/)) lists compatibility with 4th gen iPod nanos, though I have not tried it yet.

I tried songbird, but it won't recognize my ipod. Rhythmbox recognizes it, but it only works for half the songs and the other half it doesn't work. I found and used a converter to make them .ogg files, which works, but songbird still does not recognize the ipod itself, at all.

---

### Post by charding on 2009-01-06
> **jfd5xte said:**
> 
My only remaining problem-- and this should hopefully be a really easy fix-- is getting the cover art plugin back. For some reason, the plugin is not listed under "Edit -> Plugins..."


Seems like you might need to install libsgutils and it's dev package and reconfigure, compile libgpod.. Have a look at this thread:

[https://sourceforge.net/mailarchive/message.php?msg_id=BAY119-W108E5482135DC4E7CD71EAB7FB0%40phx.gbl](https://sourceforge.net/mailarchive/message.php?msg_id=BAY119-W108E5482135DC4E7CD71EAB7FB0%40phx.gbl)

---

### Post by Chris_Hookey on 2009-01-07
i have a 4th gen 16gb and had the best luck with amarock. i set the model to a 3rd gen green

---

