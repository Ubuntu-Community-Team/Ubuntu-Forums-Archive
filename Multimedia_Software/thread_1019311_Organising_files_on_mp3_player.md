---
title: "Organising files on mp3 player"
date: 2008-12-23
forum: Multimedia Software
---

### Post by Rodney9 on 2008-12-23
Hello, I'm after software to use with my mp3 player (Cowan D2), it is seen as a usb drive and I can copy/delete etc to it manually.
I want to auto copy and sync podcasts to it, plus have it auto cleanup/delete played or old podcasts on it, just like itunes used to do on my old ipod, it would just keep the latest 2 or 3 podcasts.

Is there anything for Linux that can do this ?

I can find plenty of clients, but nothing for organising files on the player.

Merry Christmas
Rodney

---

### Post by jpkotta on 2008-12-24
Keep a mirror of your player on the computer's hard drive.  Then you can use rsync to synchronize them.  Here is a script that makes it easier.  There are also tools like Unison and GUI frontends to rsync

```

#!/bin/bash

PS3="Pick a number: "
cmd="rsync --archive --update --verbose --delete"

if [ -z "$2" ] ; then
    echo "Usage: $0 <source> <destination>"
    echo "Uses rsync to synchronize destination with source."
    echo "Shows you what will happen before doing anything."
    exit 1
fi

$cmd --dry-run "$@"
select resp in yes no ; do 
    if [[ "$resp" = yes ]] ; then
        $cmd "$@"
        break
    elif [[ "$resp" = no ]] ; then
	break
    fi
done  

```

I think the fact that Cowon players look just like a USB drive and impose no specific structure or database is a feature.  *I* decide how to organize things.  But I like to control things.

---

### Post by Rodney9 on 2008-12-26
Thank You, but isn't there a easy software for this.

---

### Post by Rodney9 on 2008-12-26
What is out there seems to be just for music like Songbird, Banshee, Amarok, and Rhythmbox, but none of these have any preferences for auto deleting old or played podcasts, they have hardly any podcasts preferences at all.

Surely there is some software for using, coping deleting podcasts, but I can not find any.

---

### Post by Rodney9 on 2008-12-27
Any suggestions for auto syncing software for podcasts that will auto remove old and played podcasts from the player.

---

### Post by jpkotta on 2008-12-28
It's easy enough to delete old files using the method I described.  This will delete any .mp3 file in the directory ~/podcasts that is more than a week old.  You could add it to the script I posted previously, so that it runs before the synchronization part.

```
find ~/podcasts -iname "*.mp3" -mtime +7 -exec rm -i '{}' ';'
```

There is no way to delete played files automatically unless the player somehow keeps track of played files, and the computer has access to that information.

---

### Post by Rodney9 on 2008-12-28
> **jpkotta said:**
> It's easy enough to delete old files using the method I described.  This will delete any .mp3 file in the directory ~/podcasts that is more than a week old.  You could add it to the script I posted previously, so that it runs before the synchronization part.

```
find ~/podcasts -iname "*.mp3" -mtime +7 -exec rm -i '{}' ';'
```

There is no way to delete played files automatically unless the player somehow keeps track of played files, and the computer has access to that information.

Thankyou, this looks very good, how do I automate it so I do not have to answer for each mp3 ?

Also if some are ogg's would it be like this -

```
find ~/podcasts -iname "*.mp3 *.ogg" -mtime +7 -exec rm -i '{}' ';'
```

---

### Post by jpkotta on 2008-12-28
To let it automatically delete, remove the '-i' from the rm command.  Better safe than sorry, I say.

Add another -iname option to look for .ogg files, and separate with an '-o' (OR).
```
... -iname "*.mp3" -o -iname "*.ogg" ...
```

---

### Post by Rodney9 on 2010-06-09
Well 2 years on is their any new or easier ways of auto clean-up / delete played and / or old podcasts on my mp3 player.

---

