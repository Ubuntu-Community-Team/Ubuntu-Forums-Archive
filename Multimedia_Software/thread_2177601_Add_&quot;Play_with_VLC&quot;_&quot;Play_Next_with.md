---
title: "Add &quot;Play with VLC&quot; &quot;Play Next with VLC&quot; and &quot;Play Last with VLC&quot; options to Nautilus"
date: 2013-09-29
forum: Multimedia Software
---

### Post by bmass on 2013-09-29
I migrated over from Windows a little over a year ago and one thing I really miss is having these three options in my right-click context menu for files and folders.

This is somewhat of a quide/question as I've got this partially working.

From what I gather, the best way to accomplish this is with the Nautilus Actions Configuration tool (installed in terminal with 'sudo apt-get install nautilus-actions')

So we need to open that up and define 3 new actions.

#1. Play with VLC:

Action Tab > Nautilus item > Context label > Play with VLC

Command Tab > Profile > Label > Play with VLC

Command Tab > Command > Path > vlc
Command Tab > Command > Parameters > %b
Command Tab > Command > Working directory > %d


WORKS!


#2. Play Last with VLC: (this is tantamount to adding to VLC's playlist or enqueing in VLC; I found two guides but have not been able to get this to work properly)

guide 1: [http://ubuntuforums.org/showthread.php?t=1100766](http://ubuntuforums.org/showthread.php?t=1100766)
guide 2: [http://ubuntuforums.org/showthread.php?t=850053](http://ubuntuforums.org/showthread.php?t=850053)


Action Tab > Nautilus item > Context label > Play Last with VLC

Command Tab > Profile > Label > Play Last with VLC

Command Tab > Command > Path > ?
Command Tab > Command > Parameters > ?
Command Tab > Command > Working directory > %d

Basenames Tab > Basename filter > *.wav
Basenames Tab > Basename filter > *.ogg
Basenames Tab > Basename filter > *.mp4
Basenames Tab > Basename filter > *.mp3
Basenames Tab > Basename filter > *.mov
Basenames Tab > Basename filter > *.flv
Basenames Tab > Basename filter > *.flac
Basenames Tab > Basename filter > *.avi
Basenames Tab > Basename filter > *


Now as far as this path is concerned, I get the same result whether I use:

'vlc --playlist-enqueue --one-instance --one-instance-when-started-from-file -Z -L'

or

'vlc --started-from-file --playlist-enqueue'


And for the parameters if I use %m or %M I get an error in VLC when I use the action. 

If I use %b then the action will work ONLY if I used the 'Play Last with VLC' option to open the latest instance of VLC. So if I have TV Show, Episodes 1-10 for example, and I double-click Episode 1 and it opens in VLC, then I right-click Episode 2 and select 'Play Last with VLC' a new instance of VLC will open with Episode 2 playing. Now every file I right-click and select 'Play Last with VLC' will be added to the playlist.

How should I change the path or parameters to set it up to add the file to the playlist of the most recently open instance of VLC?

P.S. I know there are workarounds involving only one allowed instance of VLC but the purpose is to be able to open multiple instances and have this action add a file to the end of the most recent playlist (or most recently opened or active VLC instance).


#3. Play Next with VLC

I have no idea how I would go about making this action. It is far less useful than the Play Last option but it was there in Windows and I did use it from time to time. I imagine the path or parameters would be very similar to the previous action but instead of adding the file at the end of the playlist, the file would be added right after the currently playing file.


If anyone can help me out on these two actions it would be greatly appreciated. I know a lot of people are missing this functionality but there hasn't been much discussion on how to set up these actions in the last couple years with changes having been made to Ubuntu, Nautilus, VLC and Nautilus Actions Configurator. Thanks.

---

