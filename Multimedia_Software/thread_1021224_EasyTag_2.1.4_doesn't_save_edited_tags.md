---
title: "EasyTag 2.1.4 doesn't save edited tags"
date: 2008-12-25
forum: Multimedia Software
---

### Post by Nico-dk on 2008-12-25
I recently moved all my mp3s from xp to ubuntu. Originally they were tagged with Tag&Rename, then sorted according to genre into to different dirs (eg. dirs for 60s, 80s etc.)

When I opened the same files with EasyTag most genres were changed. 60s became Top40 (a genre I've never used), 80s became Folk etc. Now when I try to retag them the changes aren't saved.

Here's what I've tried:

Open the 60s dir
select all files
write 60s in genre
click scan and choose to update G.
Files are still tagged Top40.

Select all files
set genre to 60s
mark the radio button to the right of genre (I can see all tags are changed)
Click save

Changes seem to be updated, but if I change dir and return to the 60s dir, they're once again tagged with Top40.

Settings:
Under ID3 Tag:
Strip tags ...
Auto convert ...
Version ID3v2.3

Scanner:
Overwrite fields when scanning tag

Can anyone tell me what I'm doing wrong here?
Thanks :)

---

### Post by obsrv on 2008-12-25
Check the owner of those files and permissions, maybe they are wrong, maybe you can only read these files. Are they FLAC or MP3 or else?

---

### Post by Nico-dk on 2008-12-25
All permissions are enabled, and they're all mp3s. Ripped them to 224kb/s myself with AudioGrabber on XP.

Example from ls -l query:
```
rwxrwxrwx 1 nico nico  4324626 2008-12-25 13:18 A Hard Days Night - The Beatles.mp3
```

For now I'm using Audio Tag Tool, but it lacks some functionality (like copying v1 tags to v2 and vice versa)

---

### Post by obsrv on 2008-12-25
Maybe tags are corrupted. Try ripping with Linux if possible.

---

### Post by kostkon on 2008-12-25
Do you know which version of ID3 was used in *Tag&Rename* to tag these files?

---

### Post by Nico-dk on 2008-12-25
That's definitely a possibility. Tag Tool complained about a few tags.
I can't rerip with linux, because I sold off all my cds, but maybe removing all tags, and then creating new from scratch will do the trick.

---

### Post by Nico-dk on 2008-12-25
Sorry kostkon, missed your reply the first time around.
Just checked the files on my desktop, and as it turns out they're all v1. Guess, I'm getting old, because I was sure I did v2.3 for all of them.

---

### Post by kostkon on 2008-12-28
> **Nico-dk said:**
> Sorry kostkon, missed your reply the first time around.
Just checked the files on my desktop, and as it turns out they're all v1. Guess, I'm getting old, because I was sure I did v2.3 for all of them.
Hmmm, ID3v1... Actually, I had the same problem sometimes when tried to change the tags of some mp3s with ID3v1.

When saving them, EasyTag saved the changes in a new ID3v2.3 tag (or 2.4, I don't really remember) without changing the ID3v1 one that these files already had. Even stranger was the fact that the various applications (in my case Rhythmbox) continued to only see the unchanged ID3v1 tags, I don't really know why! Do the various music applications read only ID3v1 tags? Don't think so! Anyway, maybe some bug in EasyTag? A solution could have been to disable the saving of ID3v1 tags in EasyTag. This is by default enabled, and the thing it does is that when you save a tag, EasyTag saves an additional ID3v1 tag for backward compatibility reasons.

My solution instead was to remove all the tags, save the changes and then re-tag them. This made EasyTag to produce new ID3v1 tags. Also, it also solved the problem with the reading of the tags from the various music players.

You try to disable the saving of ID3v1 I mentioned above before trying to re-tag them and check if that will make any difference. Or just delete all the tags and start from the beginning.

---

