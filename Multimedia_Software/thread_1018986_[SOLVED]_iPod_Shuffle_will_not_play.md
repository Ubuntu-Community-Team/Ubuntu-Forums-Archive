---
title: "[SOLVED] iPod Shuffle will not play"
date: 2008-12-22
forum: Multimedia Software
---

### Post by SneakPeak on 2008-12-22
Hi,

I can transfer music files to my iPod shuffle with Amarok but when I press play on the shuffle I get the blinking light error which indicates there is no music on the iPod.  Using Dolphin I can see the music on the iPod it is located in the folder:

iPod_Control/Music/f?? where ?? is a number. For example 06.  

I can also play the music from the iPod on the PC. Amarok indicates that is is playing a song from /media/IPOD/iPod_Control/Music/f06 (for example)

I bought the iPod this week in South Africa.  On the box it says model A1204 and Serial No. 6V843AMG437.

Any ideas on how I can get songs to play on the iPod???

Cheers

Sneaks:confused:

I have used Sound Juicer to rip the CD's and I have ripped them to AAC m4a files.  Initially Amarok didn't want to play the m4a files but I managed to get that working.

---

### Post by shane8002 on 2008-12-22
Try this program called songbird and there is a .deb file for it. It has the best i pod support.

---

### Post by SneakPeak on 2008-12-22
> **shane8002 said:**
> Try this program called songbird and there is a .deb file for it. It has the best i pod support.

Had a quick look at the songbird webpage.  It looks good but still looks very developmental.  Amarok seems to be well established.  Anyone know how I can solve my problem with Amarok?

Any recommendations for and against songbird?

---

### Post by Farmer of Bricks on 2008-12-22
Your problem may be that the songs have not been entered into the shuffle's internal song list. 
One way to do this is take the [rebuild_db python program]("http://http://shuffle-db.sourceforge.net/") found [here]("http://sourceforge.net/project/showfiles.php?group_id=136446&package_id=149925&release_id=413094"), place it in the root directory of the shuffle, and run it. It needs Python to run, so if it doesn't run, go into your package manager , search for Python, and install it.

To unzip the program file, just right-click and open it with Ark.

---

### Post by SneakPeak on 2008-12-23
Ok, so I tried Songbird.  It has a very nice iPod interface that looks a lot like i-Tunes but unfortunately I have exactly the same problem.  The songs are on the iPod but I can't play them.  I haven't tried the other solution but it looks a bit tricky to me.  

By the way the playback sound quality on Songbird is terrible.

Anyone know how to get the iPod working with bog standard Amarok?

---

### Post by SneakPeak on 2008-12-23
Still no luck.

I have tried gtkpod but that doesn't work.  I have followed this advice (from [http://amarok.kde.org/wiki/Media_Device:IPod#My_iPod_does_not_show_any_music](http://amarok.kde.org/wiki/Media_Device:IPod#My_iPod_does_not_show_any_music))

 "My iPod does not show any music

Starting from the iPod classic and Touch era, the iPods use a method to check the consistency of the database with an algorithm called SHA1. To either prevent 3rd party apps to manipulate your iPod or to have a reliable database, the iPod checks the data of the db and could not show the tracks you have synced. If you can add tracks with iTunes but not with gtkpod, this may be happening.

Upgrading to at least libgpod 0.6.0 may solve your problems. Otherwise, have a look at the Gtkpod wiki or follow these steps:

   1. Mount your iPod.
   2. Open a terminal and type in: "sudo lsusb -v | grep -i Serial" without the quotes. Then you will see a 16-character-long hash. Copy it to the clipboard.
   3. Fire up a text editor, like Kate, Kwrite, vi, nano.
   4. Type in: FirewireGuid: 0x...
   5. ... and paste that hash of step 2 (do not omit the 0x).
   6. Save the file with the name SysInfo in the iPod_Control/Device folder under your iPod mount point. 

For example, a /media/ipod/iPod_control/Device/SysInfo file can look like

ModelNumStr: xB029
FirewireGuid: 0x000A27001301221F

If you can't sync files yet, grab the latest libgpod from SVN or get libgpod 0.6.0 and compile it, install it and finally compile Amarok against it."

Any help would be appreciated!

Sneaks:(

---

### Post by SneakPeak on 2008-12-23
I tried the rebuild-db python program.  It ran successfully but still no songs playing on the ipod.  The songs are there because I can see them in various file browsers.  The ipod just does not recognize them.

I looked at replacing the firmware with rockbox but rockbox doesn't work for shuffles.

Any help please......:(

---

### Post by ajgreeny on 2008-12-23
I don't have an iPod of any kind, but I remember reading at some time in the past that to use some, if not all the linux applications that can work with them, it is necessary to first use the iPod with iTunes to initialise it in some way.  I have no idea if that is true or not, but if you know someone with a windows machine that you can "borrow" for a while just to get started it may be an answer.

---

### Post by SneakPeak on 2008-12-23
> **ajgreeny said:**
> I don't have an iPod of any kind, but I remember reading at some time in the past that to use some, if not all the linux applications that can work with them, it is necessary to first use the iPod with iTunes to initialise it in some way.  I have no idea if that is true or not, but if you know someone with a windows machine that you can "borrow" for a while just to get started it may be an answer.

Thanks for the idea.  My wife has a Windows Vista laptop. I added some songs from her laptop. They played no problem but when I added songs from Amarok none of them played!!!  They appear to be exactly the same as the Windows added file.  Same directory structure everything but they just don't play.  It is like the shuffle doesn't see them at all.

---

### Post by SneakPeak on 2008-12-23
On about the 20th attempt of following the advice below it worked.  Honestly I have no idea what I did differently on the 20th attempt to the other attempts.  I was trying with Sunbird and Amarok alternately.  Eventually it worked on Amarok after I had used Sunbird to "Restore Factory Settings" which basically just wiped the iPod completely clean!  I had to recreate the directory structure.  Amarok did it for me automatically.  After that following the advice below worked!!!

> **SneakPeak said:**
> Still no luck.

I have followed this advice (from [http://amarok.kde.org/wiki/Media_Device:IPod#My_iPod_does_not_show_any_music](http://amarok.kde.org/wiki/Media_Device:IPod#My_iPod_does_not_show_any_music))

 "My iPod does not show any music

Starting from the iPod classic and Touch era, the iPods use a method to check the consistency of the database with an algorithm called SHA1. To either prevent 3rd party apps to manipulate your iPod or to have a reliable database, the iPod checks the data of the db and could not show the tracks you have synced. If you can add tracks with iTunes but not with gtkpod, this may be happening.

Upgrading to at least libgpod 0.6.0 may solve your problems. Otherwise, have a look at the Gtkpod wiki or follow these steps:

   1. Mount your iPod.
   2. Open a terminal and type in: "sudo lsusb -v | grep -i Serial" without the quotes. Then you will see a 16-character-long hash. Copy it to the clipboard.
   3. Fire up a text editor, like Kate, Kwrite, vi, nano.
   4. Type in: FirewireGuid: 0x...
   5. ... and paste that hash of step 2 (do not omit the 0x).
   6. Save the file with the name SysInfo in the iPod_Control/Device folder under your iPod mount point. 

For example, a /media/ipod/iPod_control/Device/SysInfo file can look like

ModelNumStr: xB029
FirewireGuid: 0x000A27001301221F

If you can't sync files yet, grab the latest libgpod from SVN or get libgpod 0.6.0 and compile it, install it and finally compile Amarok against it."

(

---

### Post by SneakPeak on 2008-12-23
Some additional information:

Solution only works for mp3 files.  None of the AAC files created using Sound Juicer work.

I mount the ipod from a terminal before clicking connect in Amarok.
I unmount the ipod from a terminal before unplugging it.

Sneaks

---

### Post by ricardisimo on 2009-02-14
For whatever it's worth, I couldn't even get my wife's Mac to sync with my Shuffle, the exact same model (A1204) for about the first six months we had it. Neither gtkpod nor Rhythmbox would work either (I'm on Ubuntu). It sat alone and forgotten in a corner of the kitchen most of that time, until about a month ago I decided to try it again.

Rhythmbox suddenly worked fine, gtkpod also worked, but seemed rather persnickety about the model number, which it does not have in its catalog. The Mac also worked perfectly. The box, you might notice, says "Special Edition", and although unlikely, it's possible that it was just a tad too "special", and lacked full support across the board.

What I'd like to know is what model number most resembles A1204, so that I can get by with gtkpod, my preferred application. Could anyone venture a guess on this? This is a 1G reddish/pinkish Shuffle.

---

### Post by Gramps on 2009-02-14
I use Banshee and when I plugged my 2nd gen shuffle in and it was mounted by the file system Banshee came up and said that it need to re-do the database as it was not in the correct format. This Shuffle had been connected to iTunes before this. I let it re-do the database and all was fine. It also said that it was not a good idea to use both iTunes and Banshee so I guess Banshee uses and older db format. I had the latest iTunes installed on the XP machine.

All I do is drag the files I want on the Shuffle to the Shuffle icon in Banshee all work well. It will also do an automatic sync but I have mine set to manual.

Haven't tried my nano yet.

---

### Post by ricardisimo on 2009-02-15
There's a slight complication for me, because so many of my songs are ogg, and [LIST=1]
[*]no one has ever responded to any of my requests for getting gtkpod's ogg-to-mp3 script working; and
[*]Rhythmbox does on-the-fly converting to mp3 quite nicely, but screws up a really high percentage of the songs, putting two copies of the same song onto the iPod.
[/LIST]
If gtkpod has the correct iPod model number, it can catch rhythmbox's errors and I can correct them. Since gtkpod doesn't know what A1204 is, it will load songs, but doesn't know when the Shuffle is full, and won't check for rhythmbox's errors. Not a huge mess, but big enough.

---

