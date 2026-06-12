---
title: "Ubuntu 22.04 - Double commander - write NTFS partition permissions"
date: 2022-04-24
forum: Multimedia Software
---

### Post by macu on 2022-04-24
Hi, after upgrading to Ubuntu 22.04 I have problem with Double commander. If i want to copy/move any file to NTFS (local partition mounted by fstab, external HDD or flash disk) i can do that, but in the end of copying file to NTFS partition it writes that double commander needs additional permissions to finish it...if i give these permission (admin passwd) I can finish copy correctly, same if I deny this dialog....I tried to copy files by Nautilus or gnome commander, everything was og without root permissions. So is there any problem with doublecmd, that it needs permissions for copying to ntfs partitions?

---

### Post by macu on 2022-04-24
I guess problem is about doublecmd and copying atributes, if i disable copy with date,ownership or read atribute that double commander copy files correctly...but why, if it worked for many years before, idk...

---

### Post by Jacdeb6009 on 2022-08-30
@macu, not related to your issue, but a double commander issue.  Newly installed Ubuntu 22.04 and Double Commander and none of the file associations work, that is, double click on a file (any file) and nothing happens.  I have installed double commander via synaptic, but also directly from the home page - no difference.  On my 18.04 install it worked perfectly "out of the box".  Have you found a similar issue?

---

### Post by echotech2 on 2022-08-31
Also a Double Commander (About shows 1.0.5 beta, revision 1004, commit co2347051) user on Ubuntu 22.04.01.  I just tried an .mp3, a .txt and a .jpg. all opened in my chosen apps.

---

### Post by Jacdeb6009 on 2022-08-31
@echotech2, thanks!  I will give it a try again.  I like DC and I find a double pane file manager more than just useful.  Will post back here on how it goes.


*** *** Update *** ***
Purged the install, did an autoremove to get rid of the orphaned files, delete the configuration files in my home folder (somehow purge did not remove these), and then reinstalled - same version, revision and commit  as per your information above.  No luck.  Not a single file will open if you double click on it.  Not .txt, .odt, .ods, .pdf, .jpg, not anything.  This would mean having to set up all associations by hand... life is too short.

Thanks nonetheless!

---

### Post by TheFu on 2022-08-31
> **macu said:**
> I guess problem is about doublecmd and copying atributes, if i disable copy with date,ownership or read atribute that double commander copy files correctly...but why, if it worked for many years before, idk...

I doubt that any end-user program has anything to do with this issue. I know zero about doublecmd. Nothing.

Without seeing the source and target directory and file permissions, we cannot help.
Also, we need to see the fstab entries for the NTFS mounts - source and target.

With non-native file systems, Linux fakes real permissions, owners, and groups through the mount options. This is key reason to avoid using non-native file systems on Linux, unless the data storage must be physically connected to a MS-Windows system.  NTFS doesn't support chown, chmod, chgrp commands, so there are always issues.  Only at mount time are those things set.

Now, if the program is distributed as a snap package, then there are specific snap package constraints that Canonical has forced onto every snap package which makes it unable to access all storage. This is a "feature" of snaps, though many people find it a pain.

---

