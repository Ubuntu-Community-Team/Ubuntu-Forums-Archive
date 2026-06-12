---
title: "Problems ripping structure protected DVDs"
date: 2008-09-09
forum: Multimedia Software
---

### Post by theacoustician on 2008-09-09
I've been working to convert my entire DVD collection to file, but I've run into some discs that simply will not rip under Linux under any circumstances.  Take for instance *Curse of the Golden Flower*.  I had tried for 4 days to rip this disc.  I attempted just about every option available in the following programs:

cpdvd
vobcopy
dvdbackup
dvd::rip
ogmrip
Handbrake
k9
VLC 
MPlayer
MEncoder

Nothing worked.  Sometimes the program would finish, sometimes it would crash out at the first set of zero cells.  Sometimes it would rip out the audio, sometimes it would only get one of the two audio tracks, others wouldn't rip audio at all.  All video rips, if it completed, either exhibited glitches, frame drop, or other random errors.  So I admitted defeat and found a Windows box.  DVD Decrypter crashed out, but DVDFab HD Decrypter  worked, corrected all the errors, and did so in 5 minutes.  So, here are some questions :

1. Is there some native Linux program I missed?
2. Is there some other way to deal with DVD protection that I'm missing?
3. Is anyone aware of a project like DVDFab (ripping with correction) for Linux being developed?

---

### Post by mc4man on 2008-09-09
> 1. Is there some native Linux program I missed?
It appears not

> 2. Is there some other way to deal with DVD protection that I'm missing?
To some degree

i'd put k9 at head of list as far as dealing with sp.

> I attempted just about every option available

In regards to k9 does that include in some instances 'giving it a hand' by excluding obvious bogus titlesets and or titles? ( series of titles with exact same size, titles with large reported sizes but short running times, titles that can't be played back in a player, a duplicate entry for main title that can't be played, ect. Sometimes you need to reauthor, sometimes you need to keep orig. menus even if only backing up the main title.

Many people like to run dvdfab.... in wine

Many sp. disks can be done with vobcopy with a slight change to the source, the limiting factor would be number of unreadable sectors - my cutoff would be around 7000 - 10000 ( fast skipping blocks of 16 sectors every 2.2 secs

---

### Post by theacoustician on 2008-09-09
> **mc4man said:**
> 
In regards to k9 does that include in some instances 'giving it a hand' by excluding obvious bogus titlesets and or titles? ( series of titles with exact same size, titles with large reported sizes but short running times, titles that can't be played back in a player, a duplicate entry for main title that can't be played, ect. Sometimes you need to reauthor, sometimes you need to keep orig. menus even if only backing up the main title.
Yep, tried that.  No dice.

> **mc4man said:**
> 
Many people like to run dvdfab.... in wine

:( I was hoping to avoid that

> **mc4man said:**
> 
Many sp. disks can be done with vobcopy with a slight change to the source, the limiting factor would be number of unreadable sectors - my cutoff would be around 7000 - 10000 ( fast skipping blocks of 16 sectors every 2.2 secsInteresting.  How do you go about changing the code?

---

### Post by oswaldkelso on 2008-09-12
> **mc4man said:**
> 
Many sp. disks can be done with vobcopy with a slight change to the source, the limiting factor would be number of unreadable sectors - my cutoff would be around 7000 - 10000 ( fast skipping blocks of 16 sectors every 2.2 secs

I run linux on ppc so wine is not an option for me. If you could expand on sp vobcopy info with a few examples of the commands you enter that would be great.

Thanks

---

