---
title: "Help Sync'ing non-Ipod music player"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by bvmou on 2007-01-20
I am looking for pointers as to how best to sync an mp3 player.  It has 1 GB of flash formatted FAT32, with one necessary piece of internal software.  My idea is to create an alias something like 

syncpcasts = "cp  **-(last 24 hours)** /home/podcasts /media/usbdisk/podcasts , then,  rm **-(older than 24 hours)** /media/usbdisk/podcasts/*.*"
syncjams = something similar for a folder I'll periodically rearrange with music

Is this possible/advisable, and what are the arguments for the stuff in bold, if they exist?  If this is proving my ignorance of a powerful and simple tool, I'm conveying what I need to convey.  Any help would be much appreciated.

--Also, is there some way to forcibly copy over an entire directory, so the alias would work without a "do you really want to do this prompt", like: cp! /my podcast directory /usb's podcast directory, and I could just make that always the more recent podcasts?

---

### Post by hal10000 on 2007-01-20
you may write a shell script to do such things. With find and cp/rm commands you may be able to get it work.
Please post how familiar you are in writing shell scripts, maybe we can do it here together.

---

### Post by bvmou on 2007-01-20
--corrected below

---

### Post by bvmou on 2007-01-20
--corrected below

---

### Post by hal10000 on 2007-01-20
Let's say you want to remove all (mp3) files from you player which are older than 24 hours (the exact definition would be here: files you changed 24 hours or longer ago)
You might then use this command:
[COLOR="Red"]find /media/usbdisk/podcasts -name "*.mp3" -mtime +1 -delete[/COLOR]

If you want to copy all (mp3) files newer than 24 hours from the player to your harddisk, then this command may help:
[COLOR="Red"]find /media/usbdisk/podcasts -name "*.mp3" -mtime -1 -exec cp {} /home/yourname/music \;
[/COLOR]
Would such commands fit your needs?

EDIT: > mv /podcasts-still-on-harddisk-just-uploaded /oldpodcast-folder-on-harddisk
Yes you can do that.

---

### Post by bvmou on 2007-01-20
--corrected below

---

### Post by bvmou on 2007-01-21
I was trying to sync podcasts on a t.sonic 610 (Transcend) using Rhythmbox as the client; the .is_music_player made it recognized, but copying smoothly was not quite possible.  I'm am absolutely green, doublecheck manual pages if you want to try something similar.  Here is what worked for me and hope it's useful to others:

First I made an alias to add podcasts to the player:

```
alias podupdate='cp -ruf ~/local-podcast-folder /media/usbdisk
```

Second was a script to remove old podcasts and add new ones:

```

#!/bin/bash

#update podcast folder on usbdisk, move old episodes to archive

echo -n "Keep podcasts less than ____ days old on the player: "
read -e keepnewerthan
find /home/user/music/podcasts -mindepth 2 -mtime +$keepnewerthan -exec mv {} /home/user/music/old-podcasts \;
find /media/usbdisk/podcasts -type f -mtime +$keepnewerthan -delete
rm -R /media/usbdisk/.Trash-user
#t.sonic players put deleted files in a separate trash bin with the local user's name
cp -rf /home/user/music/podcasts /media/usbdisk


```

To make the script usable I input in terminal:

```
chmod 777 ~/script-containing-folder/script-as-above.txt 
```

and for ease of use:

```
alias fullpodupdate='~/script-containing-folder/**./**script-as-above.txt'
```

Thanks again hal10000

---

