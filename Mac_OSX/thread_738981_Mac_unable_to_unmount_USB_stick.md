---
title: "Mac unable to unmount USB stick"
date: 2008-03-29
forum: Mac OSX
---

### Post by r76 on 2008-03-29
Any of you good Mac users able to help me, I have a USB stick that refuses to unmount from a Mac (I think Apple G4 running a fairly recent OSX).  All I try and do is put a few jpeg files on it then drag it to the eject button on the dock but I get an error saying the drive is busy, try quitting applications (nothing except finder is running).  I'm not being impatient or anything - it doesn't matter how long I leave it, it's never safe to eject.  I always have to shut down the computer.  The USB stick is FAT32 formatted SanDisk cruzer and ejects fine from xubuntu/xp/2000 just not the Mac.

I don't have administrative rights on the machine (no-one is sure what the password is) and it's attached to a piece of equipment at work from which I regularly need to retrieve files.

---

### Post by Alfa989 on 2008-03-29
Try doing some maintenance... :) (Repair permissions, etc...)

---

### Post by r76 on 2008-03-29
Thanks, but maintenance on what - the computer or the stick?  And what sort of maintenance?

---

### Post by Alfa989 on 2008-03-29
> **r76 said:**
> Thanks, but maintenance on what - the computer or the stick?  And what sort of maintenance?
Repairing permissions*... Of the computer's HD, obviously... :P

*Disk Utility>Select Drive>Repair Permissions

---

### Post by scramasax on 2008-04-01
> **r76 said:**
> Any of you good Mac users able to help me, I have a USB stick that refuses to unmount from a Mac (I think Apple G4 running a fairly recent OSX).  All I try and do is put a few jpeg files on it then drag it to the eject button on the dock but I get an error saying the drive is busy, try quitting applications (nothing except finder is running).  I'm not being impatient or anything - it doesn't matter how long I leave it, it's never safe to eject.  I always have to shut down the computer.  The USB stick is FAT32 formatted SanDisk cruzer and ejects fine from xubuntu/xp/2000 just not the Mac.

So something on the Mac won't let it go.  Maybe some background process -- say, Spotlight trying to index a corrupted file.  It'd do that even if it was in the trash (when you wouldn't see it).

I guess you could investigate what process is causing the problem.  But why not just apply a brute force and ignorance method?  Put the drive into the Linux machine.  Enable viewing of hidden files in Nautilus.  Now delete *everything*, including the trash directory for the device.  That will show as [COLOR="Green"].Trashes[/COLOR].  (BTW, the Ubuntu trash folder for the device will show as [COLOR="Green"].Trash-your-user-name[/COLOR].)

If that doesn't work, install gparted on the Linux machine and use it to re-format the drive.

I don't mean to put down the other poster, who is only trying to help you, but the "Repair Permissions" feature in OS X has nothing to do with "maintenance".  All it does is re-set the read/write/execute, etc. permissions on various directories and files to the factory defaults.  There seems no reason to believe that changed permissions on any particular file could cause the behaviour you're seeing.  If someone could tell you what change in which permissions on which system file could cause what you're seeing, then you'd have a reason to seek a solution in manipulating permissions (not that you could do so, if you were not an admin user).  But if someone can't, then how's that going to help?

---

### Post by Alfa989 on 2008-04-01
> **scramasax said:**
> I don't mean to put down the other poster, who is only trying to help you, but the "Repair Permissions" feature in OS X has nothing to do with "maintenance".  All it does is re-set the read/write/execute, etc. permissions on various directories and files to the factory defaults.  There seems no reason to believe that changed permissions on any particular file could cause the behaviour you're seeing.  If someone could tell you what change in which permissions on which system file could cause what you're seeing, then you'd have a reason to seek a solution in manipulating permissions (not that you could do so, if you were not an admin user).  But if someone can't, then how's that going to help?

A file with the wrong type of permissions can cause a lot of weird problems (specially if it's a system file)... Making sure that stay as it's supposed to be is one way to try to fix the problem... And it works on Most of the problems you can experience with OS X... :)

---

### Post by scramasax on 2008-04-01
> **Alfa989 said:**
> A file with the wrong type of permissions can cause a lot of weird problems (specially if it's a system file)... Making sure that stay as it's supposed to be is one way to try to fix the problem... And it works on Most of the problems you can experience with OS X... :)

And if I were to consult a witch-doctor he might say that evil spirits "cause a lot of weird problems" and that sacrificing a black cockerel at midnight is "one way to try to fix the problem" and moreover that "it works on Most of the problems you can experience with OS X".

He'd be quite wrong, of course, which is why one doesn't ask such people for advice.

Science not witchcraft.

[http://en.wikipedia.org/wiki/Lsof](http://en.wikipedia.org/wiki/Lsof)

---

### Post by r76 on 2008-04-01
Thanks for trying to help, both of you. I'll give the suggestions a try next time I'm at work (fortunately next Tuesday!).
> **scramasax said:**
> sacrificing a black cockerel at midnight is "one way to try to fix the problem" and moreover that "it works on Most of the problems you can experience with OS X"

Yeah, I'm going to start with that one :twisted::lolflag::p

---

### Post by the.dark.lord on 2008-04-02
> **r76 said:**
> 
Yeah, I'm going to start with that one :twisted::lolflag::p

Be on the lookout for witch-hunters and animal rights activists. :)

---

### Post by tgalati4 on 2008-04-02
If you have finder open with a directory on the USB flash drive, then the drive is "in use" and OS X won't dismount it.  Be sure to point finder to a different directory (perhaps your local home directory) and try eject again.

If you still have problems, use the following command in terminal, immediately after an eject:

>dmesg | tail -25

That will give you the last 25 lines of your kernel message log and that may give you a clue.

---

### Post by r76 on 2008-04-02
> **tgalati4 said:**
> If you have finder open with a directory on the USB flash drive, then the drive is "in use" and OS X won't dismount it.  Be sure to point finder to a different directory (perhaps your local home directory) and try eject again.

If you still have problems, use the following command in terminal, immediately after an eject:

>dmesg | tail -25

That will give you the last 25 lines of your kernel message log and that may give you a clue.

I don't have any Finder windows open but I appreciate the help.  Not going to try this until next tues as I am now officially on holiday! Yay. Just passing through Newcastle - I will be in sunny Scotland soon.  Woohoo!

---

### Post by scramasax on 2008-04-07
> **tgalati4 said:**
> If you have finder open with a directory on the USB flash drive, then the drive is "in use" and OS X won't dismount it.  Be sure to point finder to a different directory (perhaps your local home directory) and try eject again.

Where d'you get that one?  It sounds reasonable enough, but so far as I know simply having Finder point to the directory makes no difference.  In fact, I just tried it, and it didn't.

---

### Post by scramasax on 2008-04-07
> **r76 said:**
> Thanks for trying to help, both of you. I'll give the suggestions a try next time I'm at work (fortunately next Tuesday!).


Yeah, I'm going to start with that one :twisted::lolflag::p

I shouldn't have said that, and I'd like to apologize to other forum members for having done so -- although it's a bit late now.

However, anyone who does run OS X should be aware that some Mac users do keep recommending "repairing permissions" as a form of "maintenance" and even a kind of panacea.  If resetting permissions across the whole disk to the factory defaults could solve just about any problem on Unix-based systems, then Canonical would hire programmers to write a similar tool for Ubuntu and dispense with all these forums.  They don't, because it can't.

Moreover, it's not clear that the idea of such a tool, combined with what permissions are on some binaries in OS X isn't a flawed concept and a security hazard.  This came up in MoAB 15 and MoAB 5:

> At this point, we have observed the use of flawed permissions and the deployment of a tool (diskutil) by Apple which opens OS X to the most simple privilege escalation issues. It's repair permissions functionality is not only flawed by design but also commonly referred as a 'solution' (normally recommended by Apple's tech support) to almost every 'non text book' problem reported by end-users. 

[http://projects.info-pull.com/moab/MOAB-15-01-2007.html](http://projects.info-pull.com/moab/MOAB-15-01-2007.html)

According to MoAB, the hole mentioned in MoAB 5 *was* being "actively exploited in-the-wild".

---

