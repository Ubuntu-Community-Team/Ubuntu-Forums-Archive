---
title: "Instantly rip radio stream from Amarok!"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by SirKillalot on 2006-12-25
Hello, 
I love listening to webradios *(espeially ETN Progressive [http://www.shoutcast.com/sbin/shoutcast-playlist.pls?rn=7570&file=filename.pls](http://www.shoutcast.com/sbin/shoutcast-playlist.pls?rn=7570&file=filename.pls))* and I love that it is legal to rip music from them. It often happens that I listen to a stream and there is such a good track, that I want to rip it to load it onto my porable Mp3 player or show it to a friend. To do this in a minimum of time I wrote a little bash script to rip radios streams from amarok which I am often listening. 
I made a script with which you can rip the stream with one click. 
The script also makes amarok to connect to a relay server on your host to not use double traffic when ripping and streaming simultaneously.

All you need to do is:

* Install the 'streamripper' package from the Ubuntu repositories.

* You can add a little button to the gnome-panel to have fast access to the script.
Right click on the panel and chose "Add to Panel".
Then create a "Custom Application Launcher" and let it launch the script.

Here is the script:

```

#/bin/bash

# The location where your mp3 are gonna be saved
RIPTO="/media/files/ripped/refleX"

case $1 in 
        --already-ripping)
                echo ":::::::::::::::::::::::::"
                echo ":::: YOU  ARE  ALL-  ::::"
                echo "::::  READY  RIPPING ::::"
                echo "::::   THIS   RADIO  ::::"
                echo ":::::::::::::::::::::::::"
                sleep 1
                echo "3"
                sleep 1
                echo "2"
                sleep 1
                echo "1"
                sleep 1
                exit 0;
        ;;
        *)

if [ `dcop amarok player encodedURL` == "http://localhost:8000" ]; then
        echo "gleeeeich"
        x-terminal-emulator -e $0 --already-ripping 
fi

x-terminal-emulator -e streamripper `dcop amarok player encodedURL` -d $RIPTO -r -q
dcop amarok playlist playMedia http://localhost:8000
;;
esac

```

Info:
You have to make the file executable if you paste the script into a file.
To do so use 'chmod +x filename'


Heres a picture of my button (the red circle)

[IMG]http://img209.imageshack.us/img209/637/screenshotwq2.png[/IMG]

Happy ripping!

---

### Post by bruenig on 2006-12-25
How did you get firefox like that with the navigation bar beside the menus. Or more accurately, how did you get your icons small enough to make it work well. I assume a certain theme?

Edit: Nevermind, didn't realize there was a small icon mode.

---

### Post by SirKillalot on 2006-12-26
> **bruenig said:**
> How did you get firefox like that with the navigation bar beside the menus. Or more accurately, how did you get your icons small enough to make it work well. I assume a certain theme?

Edit: Nevermind, didn't realize there was a small icon mode.

you can get the navibar beside the menues by just dragging and dropping it when editing the panels in firefox.

---

