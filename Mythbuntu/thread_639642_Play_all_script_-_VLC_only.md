---
title: "Play all script - VLC only"
date: 2007-12-13
forum: Mythbuntu
---

### Post by shad0w_walker on 2007-12-13
At long last I got around to creating a solution to having a play all function in MythVideo. This script will only work with VLC but the basic idea could be used for other players (Haven't checked but I imagine something similar could work)

Features:
[list]
Play all files in a given folder.
Start playback from selected file.
Movie folder check to play only the movie you select.
Extra commands can be passed to VLC at startup with small modification to the script.
Kills existing instances of VLC to deal with lockups, focus stealing, etc
[/list]

If anyone has any suggestions, bug fixes, ideas on building a version of alternative players (Mplayer, xine, etc) please reply to the thread and let me know.

[SIZE="5"]Note:[/SIZE] This script has only been tested on Mythbuntu 7.10

Now at last, the script
```

#!/bin/bash

#Check to see if file is in a definable movie folder
if [[ `echo "$1" | grep "/Movies/"` != ""  ]]
 then
	vlc "$1" vlc:quit
 else

	#Get playlist number of given filename
	#Change	to root dir to get full video path
	cd /
	#Extract folder name for playlist generation		
	basedir=`dirname "$1"`
	#Extract filename for playlist number and switch to video folder
	basename=`basename "$1"`
	cd "$basedir"
	#Generate file list (Numbered) and isolate the number of the file
	startitem=`ls | grep -n ^ | grep "$basename" | cut -d ':' -f 1`
	#Offset playlist number (File listing starts at 1 and VLC playlist starts at 0)
	let startitem=$startitem-1

	#Destroy any existing VLC processes (Incase of hangups, etc)
	killall vlc

	#Generate command file (To send to RC interface when running)
	echo "goto $startitem" > /dev/shm/vlc-rc.send
	echo "enqueue vlc:quit" >> /dev/shm/vlc-rc.send
	
	#Run VLC
	vlc --rc-fake-tty --extraintf rc --rc-host localhost:12345 "$basedir" &
	#Give short time for VLC to load, generate playlist, etc
	sleep 0.25s
	#Send commands to RC interface
	netcat localhost 12345 -q 1 < /dev/shm/vlc-rc.send
	
fi

exit 0

```

---

