---
title: "Use the new notification system to display mpd song names"
date: 2009-07-12
forum: Multimedia Software
---

### Post by xqyz on 2009-07-12
MPD is my media "player" of choice on my system. It's really amazing. I'm not too keen on most clients however. I just have a bunch of launchers in the top panel for previous song, next song, toggle playback (all via mpc) and a launcher for ncmpc for song selection. This works really good and I love it. I also used to have a launcher which called gdialog to display the currently playing song (gdialog --msgbox "`mpc | head -n 1`"), but no more:
I now use the new notification system on Ubuntu to display songs and also managed to get them to show up once the song changes automatically. It's really great.

(I've put all files in a .bin folder in ~, you can adjust it of course):

[B].bin/notify.py
[/B]```
#!/usr/bin/python
import sys
import pynotify

if not pynotify.init("Patrick's Notify"):
    sys.exit(-1)

title = "Title"
message = "Message"
try:
   title = sys.argv[1]
   message = sys.argv[2]
except IndexError:
   pass
n = pynotify.Notification(title, message, "")
n.show()
```

[B].bin/updatestatus
[/B]```
#!/bin/bash
for (( ; ; ))
do
    old="`mpc | head -n 1`"
    sleep 5
    new="`mpc | head -n 1`"
    if [ "`echo ${new} | grep volume | grep repeat | grep random`" != "" ] ; then
        if [ "$old" != "$new" ] ; then
            ~/.bin/notify.py "MPD Playback stopped" "`date +'%I:%M %p'`"
        fi
        old="$new"
    fi
    if [ "$old" != "$new" ] ; then
        /home/patrick/.bin/name_song
    fi
done
```

[B].bin/name_song
[/B]```
#!/bin/bash
#gdialog --msgbox "`mpc | head -n 1`"
~/.bin/notify.py "`mpc --format '%title%' | head -n 1`" "`mpc --format '%artist%' | head -n 1`"
```

run the updatestatus script (eg at login) and be happy ;)

---

### Post by jpeddicord on 2009-07-13
Since this is an mpd status script and not really a tutorial, I'm going to move it to Multimedia & Video. :)

Jacob

---

### Post by hoooootz82 on 2010-05-02
I made some improvements to your script, such as added cover art, and multiple lines, and various other things:

**notify.py:**
```
#!/usr/bin/python
import sys
import pynotify
import os

if not pynotify.init("Patrick's Notify"):
    sys.exit(-1)

title = "Title"
message = "Message"
try:
   title = sys.argv[1]
   message = sys.argv[2]
   print "picture name: " + sys.argv[3] #debugging purposes
   uri = "file://" + sys.argv[3]
except IndexError:
   pass
n = pynotify.Notification(title, message, uri)
n.show()
```

**updatestatus:**(not much has changed)
```
#!/bin/bash
for (( ; ; ))
do
    old="`mpc | head -n 1`"
    sleep 2
    new="`mpc | head -n 1`"
    if [ "`echo ${new} | grep volume | grep repeat | grep random`" != "" ] ; then
        if [ "$old" != "$new" ] ; then
            ~/.mpd/notify/notify.py "MPD Playback stopped" "`date +'%I:%M %p'`"
        fi
        old="$new"
    fi
    if [ "$old" != "$new" ] ; then
        ~/.mpd/notify/name_song
    fi
done
```

**name_song:** (added new script for getting the cover art)
```
#!/bin/bash
cover=$(~/.mpd/notify/mpdcover.sh)
title="`mpc --format '%title%' | head -n 1 | cut -c -28`"
info="`mpc --format '%album%' | head -n 1 | cut -c -30`
`mpc --format '%artist%' | head -n 1 | cut -c -30`"
~/.mpd/notify/notify.py "$title" "$info" "$cover"
```

The new script finds the closest album art match for the current song (if it doesnt find one for the album, it will get one for the artist, if there is no album art for the artist, then a default icon is displayed)

**mpdcover.sh**
```
#!/bin/bash
covers="$HOME/.covers/" #path to directory with covers
default="$HOME/.mpd/notify/music-icon.png" #default icon if no cover is found

a=$(ls ~/.covers | grep "`mpc --format '%artist%' | head -n 1`-`mpc --format '%album%' | head -n 1`" | head -n 1)
if [[ -z $a ]]
then
	a=$(ls ~/.covers | grep "`mpc --format '%artist%' | head -n 1`" | head -n 1) #gets cover art of first cover from artist if available
	if [[ -z $a ]]
	then
		a="$default" #generic music icon, so something is displayed
	else
		a="$cover$a"
	fi
else
	a="$cover$a"
fi
echo $a
```

I hope you find this useful. I personally used [_ario_]("http://ario-player.sourceforge.net/") to download the album covers. It stores them in "~/.config/ario/covers". 
It downloads a small version of the cover as well, so it would be best if you executed: ```
cd ~/.config/ario/covers
rm SMALL*
```

Thanks for the great script, hope I made some changes that you find helpful, I'm kind of new to bash scripting, so I'm sure I made some rookie mistakes.

I have also attatched two screenshots, one with a generic icon, and one with an icon that was found.

---

