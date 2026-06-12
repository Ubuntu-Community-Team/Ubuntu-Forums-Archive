---
title: "MPD Create Databse problems"
date: 2008-06-13
forum: Multimedia Software
---

### Post by billynomates on 2008-06-13
When I use the ```
mpd --create-db
``` command, the database is created seemingly perfectly and without and error messages. However, when I go into any client, there are lots of files missing and some duplicates of albums etc.

Does anyone know if this a bug in MPD or is there something I can do to fix it? I can post my conf file if that helps.

Thanks in advance.

---

### Post by DezSP on 2008-06-13
MPD needs read access to your music directory, more often than not the problem with missing files is that the daemon can't actually see them. By default it runs as mpd.mpd I believe, but you can change this in the conf file. Not sure about the duplicated albums though, perhaps you have some symlinks floating around?

---

### Post by billynomates on 2008-06-15
> **DezSP said:**
> MPD needs read access to your music directory, more often than not the problem with missing files is that the daemon can't actually see them. By default it runs as mpd.mpd I believe, but you can change this in the conf file. Not sure about the duplicated albums though, perhaps you have some symlinks floating around?

Hmm, still can't seem to figure this out. It's definitely not a problem with the client software I'm using though, because the mpd.db file does have duplicate entries. I've never used symlinks before. Would they be obvious if they were in the directories?

When I first installed MPD, I stripped by conf file down to this:
```
bind_to_address         "localhost"
music_directory         "~/Multimedia/Music"
playlist_directory      "~/.mpd/playlists"
db_file                 "~/.mpd/mpd.db"
log_file                "~/.mpd/mpd.log"
error_file              "~/.mpd/mpd.error"
pid_file                "/home/mike/.mpd/mpdpid"
user                    "mike"

```

Could that be the problem? Can you see if there is there anything missing?

---

### Post by vanadium on 2008-06-15
You should probably try deleting the db_file and then recreate it with "mpd --create-db". I once had problems, and I could fix it this way.

---

### Post by billynomates on 2008-06-16
> **vanadium said:**
> You should probably try deleting the db_file and then recreate it with "mpd --create-db". I once had problems, and I could fix it this way.

Yeah, I tried that. It's better, but there are still lots of missing/duplicate files - just different ones now!

---

### Post by DezSP on 2008-06-17
Try using absolute paths (i.e. /home/mike instead of ~), I had problems with sudo messing those up sometimes. Is there any pattern in the duplicated/missing files? Like special characters, all tracks beginning with X, anything? If you can find out what the pattern is it might lead us to the solution.

---

### Post by vanadium on 2008-06-18
~  is an absolute path so there will not be the problem. If you say 1) the duplicates are now different, 2) you never used symlinks before, then links indeed likely won't be the issue. Perhaps you could run a recursive directory listing and compare that with the db to confirm it is not an issue with the filing.

 ls -rC1 ~/Multimedia/Music/*

---

### Post by DezSP on 2008-06-18
Capital R, not lowercase. ;)

---

### Post by billynomates on 2008-06-20
Haha, it seems that there were actually some duplicate files in my directory, but no where near the amount that Ario was showing. Ario was showing at least ten of the same album, whereas I only had two.

NCMPC doesn't display any incorrect duplicates, but doesn't see the files that were missing. Those files, by the way, can be seen by the ls command.

Thanks you your help on this guys. Any other ideas?

---

### Post by funkydan2 on 2008-06-21
What happens if you run
sudo /etc/init.d/mpd start-create-db 
instead?

(You may need to 'sudo /etc/init.d/mpd stop' before creating the DB)

---

### Post by billynomates on 2008-06-24
Makes no difference. This is so frustrating!

Hmm, just realised that the albums from which files are missing do not play properly. They sound like they're being played really fast - like, in less than a second. I tested them in Rhythmbox and they work fine there!

---

