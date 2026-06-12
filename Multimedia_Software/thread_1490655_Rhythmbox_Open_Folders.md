---
title: "Rhythmbox: Open Folders"
date: 2010-05-22
forum: Multimedia Software
---

### Post by Xnyper on 2010-05-22
I have been trying to do something very simple, and I just can't seem to make it work. I'm probably overlooking something dumb, hopefully you can point it out to me.

I'm going to this rave/concert/festival thing and I want to get to know the music better, so I downloaded several compilations, discographies, etc...  Each compilation is contained in a single folder. The music contained therein doesn't have an ID3 tag in common, so I can't just search for an artist, or a genre, in my rhythmbox library.

**All I want to do is play them all together**, as in, one playlist to play them all, one playlist to find them....  If that means opening multiple folders into the play queue, ok.  If that means making a playlist with everything in it, ok.

Once imported, I can't find a way to get Rhythmbox to recognize file structure, so I can't search by folder names.  I used to be able to select them all in the "recently imported" section, but I failed to save a playlist then, and now that they've been in my library too long there's not so "recent"

So, I thought I'd create a playlist.

I can list all of the files with the following command:

```
ls Introduc* Kaska* Kraddy* Pendulum* Rusko* Various\ tr* The\ Glitch DJ* Deadmau* Electro-House* -1R | grep .mp3$

```

so I figure with something like " > list.M3u" I could have a playlist, which I can open in Rhythmbox.  Trouble is, that M3u file has to have the paths, not just the names, of the files, and I can't get ls to output the full paths.

It was suggested I use "find", which outputs full paths, to make my playlist, but while I can come up with a string/strings to match my folders, I cant do the same to match every file within those folders.  Also, I don't think you can tell "find" to locate directories of some format and then list their contents.

My solution so far has been to highlight all of the folders in question in Nautilus, make symbolic links of all of them, put those links in a folder, re-import that folder, and then create my playlist from "recently added"  What a terrible solution eh?  I have all these duplicate entries in my music collection. 

Any ideas?

---

### Post by ajgreeny on 2010-05-22
You can try manually making a playlist with the pls file type.

Here is a print out of the first five tracks from one of mine, showing the format needed.
```
[playlist]
X-GNOME-Title=Joni_Mitchell
NumberOfEntries=25
File1=file:///home/andrew/Music/Joni_Mitchell/00.%20Both%20Sides%20Now.mp3
File2=file:///home/andrew/Music/Joni_Mitchell/00.%20Jericho.mp3
File3=file:///home/andrew/Music/Joni_Mitchell/00.%20Off%20Night%20Backstreet.mp3
File4=file:///home/andrew/Music/Joni_Mitchell/00.%20Overture-Cotton%20Avenue.mp3
File5=file:///home/andrew/Music/Joni_Mitchell/02.%20Talk%20To%20Me.mp3
File6=file:///home/andrew/Music/Joni_Mitchell/04.%20Paprika%20Plains.mp3
```The **.%** in the file names is the way a space is shown in the playlist, so you will need to do that to get the files recognised.  Maybe there is a simpler way to do it with another player, after opening the folder with that player, but if so, I can't find it at the moment.

EDIT:
Found it!
Use gnome-mplayer set to only allow one instance open at any time (or you end up with each track in a different gnome-mplayer window).  Use nautilus to highlight all the files in the folder and right click to open with gnome-mplayer.  Now using the preferences of gnome-mplayer to show the playlist in the window, you can save as a .pls those files currently playing.

---

### Post by Xnyper on 2010-05-25
Thanks for the reply!

I appreciate the .pls info, I'll definitely use that next time I need to make such a play list.

mplayer will indeed let you open multiple files (as will vlc, which I've been using).  Thing is, my goal is to open the contents of multiple folders.  If you select multiple folders and right click 'em you can't "open contents of all subfolders in ..."

I can merge all of these folders for easy playlist creation, but then I have to un-organize my collection or deal with duplicates.

I got it done via my clunky symbolic link method, so at this point the problem remains purely academic--I no longer need to find it, but there ought to exist an elegant solution to this problem (like a plugin to add "directory" to the fields that Rhythmbox searches).

EDIT: You had it after all.  In nautilus you can view the contents of multiple folders at once with those little drop-down triangles.  I can modify the above command to "touch" all of those folders instead of "ls" them.  Then in nautilus I can sort by date modified, expand the folders, use click-shift-click to select the lot of them and then open that in vlc (or mplayer).  Save playlist, and voila!

THANKS!!

---

