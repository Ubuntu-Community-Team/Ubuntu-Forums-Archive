---
title: "gtkpos and xmms2"
date: 2009-10-07
forum: Multimedia Software
---

### Post by oboedad55 on 2009-10-07
Has anyone figured out how to play ipod songs with gtkpod? I've installed xmms2 as it seems to need it but no love getting it configured. Any help would be greatly appreciated.

---

### Post by supernal on 2009-12-12
My solution for this was to write a very small script, and use it to play songs with xmms2 from gtkpod.

Create a bash script, i named mine "gtkpod_PlayNow.sh", and set this file "executable"

Put into this file:

```
#! /bin/bash
#xmessage --center $1 "= VAR passed into script" & >/dev/null 2>&1
xmms2 stop;xmms2 add "$1";xmms2 play;xmms2 clear
```In gtkpod, click 
Edit > Preferences
Click on the "Music" tab
Click on the "commands" button.

In the "Command for Play Now" box, i entered in 
/dir/to/script/./gtkpod_PlayNow.sh %s

and in the "Command for Enqueue" box, i entered in 
xmms2 add %s


So now, when i right click a song in gtkpod, and select "Play Now"
the script stops the player from what it is playing now (if anything), adds the song you clicked to the xmms2's playlist, starts playing the song, and then deletes the song from the play list.

If at any point you want to queue up the next song, and are willing to wait for the one you are listening to to finish, you can right click on select "Enqueue" 

The only bad part of this is the only way to stop playback is to go to the command line and type
xmms2 stop

Or i suppose you could just enter that into the "Enqueue" section so you can right click and stop the music.

Hope this helps  =)

as a disclaimer, this is a very basic script with no error control.
It does get the job done however  ; )

---

### Post by Flames on 2011-05-18
Thanks for that. I was going crazy trying to get xmms working.... dependencies and what not. I found another solution was simply to put "totem %s" as the gtkpod command.
 This opens a window, but then you can stop the playback easily.

---

