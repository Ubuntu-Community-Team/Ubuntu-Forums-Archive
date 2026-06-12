---
title: "Tagging flac files help"
date: 2013-10-13
forum: Multimedia Software
---

### Post by humanracer on 2013-10-13
Hi
I can split one big flac files into smaller flac files but cannot seem to tag them.

I am following the guide here

[http://www.webupd8.org/2009/04/split-ape-and-flac-files-in-ubuntu-and.html](http://www.webupd8.org/2009/04/split-ape-and-flac-files-in-ubuntu-and.html)

splitting the files:
cuebreakpoints *.cue | shnsplit -o flac *.flac ;

fine this works then I use 

cuetag *.cue split-track*.flac ;

but nothing happens. the files are still split-track01.flac etc

any ideas as this is driving me crazy. I tried using flactag but it says there is no cue sheet for each file

---

### Post by shantiq on 2013-10-14
i have never managed it either
i think the cuesheet needs to be a specific type and it almost never is   ::]]]

my solution always is to use easytag or puddletag after the event


or way better to use flacon [all tags kept]

> sudo apt-get install flacon mac
include mac if you split from ape too otherwise do not


[ATTACH=CONFIG]246937[/ATTACH]

---

