---
title: "audiocd woes"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by MrE on 2007-04-04
Hi,

I've got this really frustrating problem with audio CDs.

I'm running Feisty beta, although I had exactly the same problem on Edgy.
My PC has got two optical drives, one CD-RW (/dev/hdc) and one DVD+RW (/dev/hdd).
At first the problems was that whenever I tried to access an audio CD in either drive in Konqueror via audiocd:/, I would get an error message saying 'Device doesn't have read permissions for this account.  Check the read permissions on the device.'

I checked the permissions of /dev/hdc, /dev/hdd/, /dev/cdrom, /dev/cdrw, /dev/dvd, /media/cdrom, /media/cdrom0 and /media/cdrom1 but all permissions were correct.

Strangely enough, accessing the CD in Konqueror via media:hdc/ or media:/hdd would work, but KcCD would not see the disc at all and Kaffeine was happy regardless of what device I specified in the settings.

In the end I managed to get audiocd:/ to work by explicitly specifying /dev/hdc in KControl -> Sound & Multimedia -> Audio CDs -> General -> Specify CD device
The problem with this is however that I can now only use the CD drive to play/rip audio; when I insert an audio CD in the DVD drive and enter audiocd:/ in Konqueror, I don't get an error and it does show me the virtual folders however all of them are empty. This makes senses (well, kinda, why do I not get an error?) as the Audio CD is now defined as /dev/hdc, although I can see all files and use the CD when entering media:/hdd

But there's more :-(, when I try to eject the CD by right clicking on its mounted desktop icon and selecting eject, I get the message 'audiocd:/ cannot be found' regardless of whether the CD is in /dev/hdc (the specified drive) or /dev/hdd

It's driving me nuts as I can't seem to find out what's wrong, and everything was working just fine in Dapper. I'd read something about there a problem with the audiocd:/ protocol due to a bug in kdemultimedia-kio-plugins, so I had hoped that moving to Feisty (even though it's beta) would solve the problems (it has solved a few other problems for me already). There seem to be quite a few people having problems with audiocd:/ but no real answers...

It is probably worth mentioning that running ```
cdparanoia -vQ
``` showed that /dev/cdrom is pointing to /dev/hdd, so I checked all the dev symlinks for my CD/DVD drives and to my surprise noticed that *all* of them point to /dev/hdd!
I then removed /dev/cdrom and /dev/cdrw and created new symlinks of the same name that point to /dev/hdc, leaving /dev/dvd to point to /dev/hdd
This resulted in cdparanoia now correctly finding my Audio CD in the CD-RW drive however I still got the same error when attempting to eject the CD as described above. But moreover, after a reboot those newly created symlinks point at /dev/hdd again!

Can anyone shed a light on what's going on here? It's driving me mad ](*,)

Many thanks

---

### Post by lisati on 2007-09-26
This is an old thread which I found while looking for an answer to the "phantom audio CD" problem which I'm sure I read about somewhere.......has it been solved?

---

