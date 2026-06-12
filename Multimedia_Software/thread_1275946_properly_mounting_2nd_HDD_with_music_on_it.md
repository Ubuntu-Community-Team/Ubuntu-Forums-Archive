---
title: "properly mounting 2nd HDD with music on it"
date: 2009-09-26
forum: Multimedia Software
---

### Post by v1nsai on 2009-09-26
I've been having a lot of problems with music players lately, most of them have had to do with deleting, moving or renaming songs.  I think I've pinpointed the problem to the fact that I keep all of my music on a separate HDD, which I then mount and use.  I'm thinking maybe it isn't getting mounted properly, I was hoping someone could suggest a different way to mount it that will give me better control over it.

The drive is NTFS formatted and is 80GB, I have it mounted as such:
```
/dev/sdb1 on /media/dos type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
```

Much thanks, this is a problem I've been having for a long time.  Could anyone recommend a good tag editing program too?  My tags are majorly screwed up from all the different programs I've used to listen and organize my music.

---

### Post by doas777 on 2009-09-26
well if you want to mount it only on use, then fuse is the way to go. 

if you want it mounted perpetually however, I would suggest that you add it to your fstab, so that it mounts at boot.
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by v1nsai on 2009-09-26
I do have it in my fstab, forgot to post that haha

```
UUID=631964596312CBD4 /media/dos   ntfs auto,users,rw,exec,noatime,uid=v1nsai 0 2
```

---

### Post by edouardp on 2009-09-26
Could you be more specific with the problems you are having ? (like what software do you use and so on ...)

As for a good tag editing program, I'm using Songbird (complete media player, not just tag editing) but this is the only software I found to be able to edit embedded album covers in MP3s. You can find a deb on getdeb.net :)

---

### Post by v1nsai on 2009-09-26
I have issues with random songs not being seen at all in Banshee (like more than half of my library actually), Listen music player (god I wish I could get this one to work) doesn't recognize the tags in a lot of my songs, they're just displayed as 'file:///media/path/to/music', and 0.6.3 the latest one crashes at random times.  Rhythmbox is unable to move songs to trash, I have to delete them manually, and it seems to forget the names I give to songs, and the tags revert to what they were called before I changed them.  I've also tried using easytag before to change the tags, but I didn't really notice a difference after an hour of processing name changes.

These issues all seem to point to either similar bugs in the programs or something on my setup keeping me from naming songs.  I've still got easytag but I'd like to make sure I've mounted the drive with the best access before I change them, I've changed these things too many times already -_-

---

### Post by v1nsai on 2009-09-30
Anyone see a problem with how I've mounted my drive?  I wanna try moving my music folder over and see if that fixes my problems but I haven't made the space yet.  I've been trying to solve this for a while now, help greatly appreciated.

---

### Post by v1nsai on 2009-10-07
bump, I still have problems with writing song names, can anyone confirm that I'm mounting the drive properly so I can try to find the problem somewhere else?

I still think something is off, I have everything named like I want in rhythmbox, but when I look at it from Listen, the song names are the same wrong names that I saw before I changed them in Rhythmbox.  Are there other types of metadata tags besides ID3?

---

