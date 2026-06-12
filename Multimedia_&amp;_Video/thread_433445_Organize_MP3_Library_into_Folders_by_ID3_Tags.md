---
title: "Organize MP3 Library into Folders by ID3 Tags"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by rmx.dave on 2007-05-05
Hey everyone,

I've done a bit of searching and couldn't find the app I was looking for. Does anyone know of an application that can take my huge folder of MP3 files and organize them into a nice Artist>Album>Song structure by looking at the ID3 tags? You know, create folders with the artist name, and then folders with the album titles below that? I have like 3000 songs that aren't organized in any sort of way. 

Thanks,
rmx.dave

---

### Post by Soarer on 2007-05-05
Yes - EasyTag will do it - it's in the repos. It took me a while to get my head around the interface (essentially you do all the changes, if any, then save the files which is when it does the move to your defined structure) but it does what you want.

---

### Post by goodtimetribe on 2007-05-05
> **Soarer said:**
> Yes - EasyTag will do it - it's in the repos. It took me a while to get my head around the interface (essentially you do all the changes, if any, then save the files which is when it does the move to your defined structure) but it does what you want.

```

sudo apt-get install easytag

```

worked for me.

thanks for the tip.
now to see how it compares to some windows ones... anyone know if mp3tag.de works under wine?

---

### Post by goodtimetribe on 2007-05-05
be forwarned... it ignores my wma files. i need something that does wma. anyone have any suggestions?

---

### Post by goodtimetribe on 2007-05-05
mp3tag.de successfully installed, prompting to install the necessary components of wma9, executing the install of wma9, completing the install successfully of wma9, finished the setup of mp3tag.de, but it *still* doesn't open my wma files.

reminds me to check to see if i can even open wma9 files in any native linux app.

yup, no problem in mplayer... is there something else i should be checking/looking that i might be missing?

---

### Post by jfinkels on 2007-05-05
Ex Falso is an excellent tag editor. I think it is able to rename your files.

It looks like, according to this site [http://www.sacredchao.net/quodlibet/wiki/Guide/Renaming](http://www.sacredchao.net/quodlibet/wiki/Guide/Renaming) , Quod Libet, (another excellent app; the sister to Ex Falso which actually plays the music :D) is able to rename files according your specifications.

It's worth a look.

---

### Post by goodtimetribe on 2007-05-05
> **jfinkels said:**
> Ex Falso is an excellent tag editor. I think it is able to rename your files.

It looks like, according to this site [http://www.sacredchao.net/quodlibet/wiki/Guide/Renaming](http://www.sacredchao.net/quodlibet/wiki/Guide/Renaming) , Quod Libet, (another excellent app; the sister to Ex Falso which actually plays the music :D) is able to rename files according your specifications.

It's worth a look.
It didn't work with my wma9. :(

---

### Post by hugmenot on 2007-05-06
Try these newer packages for WMA.
[http://ubuntuforums.org/showpost.php?p=2596985&postcount=201](http://ubuntuforums.org/showpost.php?p=2596985&postcount=201)

---

### Post by markp1989 on 2007-10-20
i have installed easytag, but i dont know how to use it, all of my files have id3tags, but i want to rename the files/folders to match the tags so that they are set up ~/music/artist/album/song.mp3

how do i do this using this program?

---

### Post by Soarer on 2007-10-21
It's works in several stages.

First, select the files you want to move. If the tags are correctly written, then do: Scanner>>.Rename File(s) & Directory.

You need to use tokens to describe how you want the files to be renamed.

For example, to put them as  ~/music/artist/album/song.mp3 you would use:

/home/yourusername/music/%a/%b/%t in the file name' section.

It will show you underneath what the resulting filenames will be. Check they are OK.

Then hit the green icon at the top to the right of the "Scanner: Rename Files and Dir" box

That will NOT rename the files - they won't be saved until you hit the 'diskette' icon on the main screen (not the scanner screen).

Once you do that, it will save the files to the new filenames & directories.

You can do this to lots of files at once, once yo have tried it on a few to make sure it does what you want.

It's a bit cumbersome, but soon becomes routine, and for me has worked well.

---

### Post by BradwJensen on 2007-11-11
It's not free but it's definitely THE BEST audio tag editor for windows (imho) - [Tag & Rename]("http://www.softpointer.com/tr.htm").

I've honestly tried tons of apps and that is by FAR the best app..  It tags practically every kind of audio file type.  Batch or song by song. I'm here right now cause i've been looking for a replacement on Linux. :-(

Hopefully i'll find a good/decent one :-)
Thanks for the suggestions everyone!

---

### Post by Suparious on 2008-04-12
following the below instructions for EasyTag, I was able to have the same level of ease. The only exception would be that you have two steps (scan / rename),

> **Soarer said:**
> It's works in several stages.

First, select the files you want to move. If the tags are correctly written, then do: Scanner>>.Rename File(s) & Directory.

You need to use tokens to describe how you want the files to be renamed.

For example, to put them as  ~/music/artist/album/song.mp3 you would use:

/home/yourusername/music/%a/%b/%t in the file name' section.

It will show you underneath what the resulting filenames will be. Check they are OK.

Then hit the green icon at the top to the right of the "Scanner: Rename Files and Dir" box

That will NOT rename the files - they won't be saved until you hit the 'diskette' icon on the main screen (not the scanner screen).

Once you do that, it will save the files to the new filenames & directories.

You can do this to lots of files at once, once yo have tried it on a few to make sure it does what you want.

It's a bit cumbersome, but soon becomes routine, and for me has worked well.

The search string that I configured was: '/srv/downloads/new/audio/%a/%b/%a - %t', and it was straighforward to figure out the macro legend (click 'show legend' within the search window)

---

