---
title: "Can't see any videos in video manager or media library"
date: 2010-02-20
forum: Mythbuntu
---

### Post by BigWoop on 2010-02-20
[SOLVED]

I'm trying to watch video that I've ripped from my DVDs and produced myself (they do work as I play them on Windows all the time), but cannot get them to show up. In the media library under videos I just see "no files found", as I do under video manager.

I've been searching and the only advice I could find are these examples:

[http://ubuntuforums.org/showpost.php?p=3515686&postcount=3](http://ubuntuforums.org/showpost.php?p=3515686&postcount=3)

> Is this a standalone, backend and frontend on one box? Mine's this way, and if I wanna add videos like movies in the "Videos" section, I don't use the backend at all. you can specify the directory your videos are in the frontend by going to "Setup > Video Settings > General Settings". Then go back to the main menu, "Videos > Video Manager" and it will scan them and add them for you.

[http://www.mythtvtalk.com/forum/installation-issues/4512-how-do-i-play-videos-mythbox-mounted-share.html#post17757](http://www.mythtvtalk.com/forum/installation-issues/4512-how-do-i-play-videos-mythbox-mounted-share.html#post17757)

[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8755692&postcount=3](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8755692&postcount=3)

> First off, it's nice to be able to help as opposed to asking for help  If you are having the same issue I was - not being able to scan for new videos from the 'video manager' like was possible in every other version of mythtv I've used, as long as your paths are correct, try this. Open 'Video Manager' and press the 'm' key. It brings up a menu that shows all sorts of options - one being 'Scan for Changes.' All of the sudden, all my videos from local sources, smb shares and nfs mounts showed up! MAGIC! Why it's like this - I'm not sure. I'm going to try and see how I can get this to automate when 'Video Manager' is opened. I'll post back if I find it.

Best 'o Luck.

II

Needless to say these have not helped.

I have a seperate partition (/movies) with the files on it, I thought maybe that was the issue so I copied them into my /home/"user name"/Videos dir, and still no luck. Obviously I changed the directory as per the examples above to reflect the different dirs on my PC, before going into video manager and just seeing "no files found".

I'm trying files of various types, .avi, .flv, .mkv, .mpg, .mp4, .rm, none of them are showing.

I've double checked to make sure I typed the dirs in right.

I selected a combined front/backend system when I installed.

Using Mythbuntu 9.10.

Not sure what other info if any is required to help me?

EDIT: I had tried restarting and then trying again before, but I've just installed the nvidia-glx-96 drivers for my card, then after that went into video manager, pressed "m" and asked it to rescan and my vids showed up.

---

