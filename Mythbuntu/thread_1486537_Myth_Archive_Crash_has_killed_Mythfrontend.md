---
title: "Myth Archive Crash has killed Mythfrontend"
date: 2010-05-17
forum: Mythbuntu
---

### Post by jonnan on 2010-05-17
I'm at my wits end - before using Mytharchive I had a running MythTV install

I installed Myth archive, didn't work
Found some missing packages that (IMO) should have been installed, still didn't work, but got farther.
Found another package (tcrequant) that was missing, got it installed via a third package - actually got the DVD burning, then it crashed the whole frontend with the error

> 2010-05-17 00:33:17 Running growisofs to burn DVD
2010-05-17 00:43:18 ------------------------------------------------------------
2010-05-17 00:43:18 ERROR: Failed while running growisofs.
2010-05-17 00:43:18 Result 1, Command was: growisofs -dvd-compat  -Z /dev/dvd -dvd-video -V "The Buddha" /var/lib/mytharchive/temp/work/dvd
2010-05-17 00:43:18 Please check the troubleshooting section of the README for ways to fix this error
2010-05-17 00:43:18 ------------------------------------------------------------
2010-05-17 00:43:18 
2010-05-17 00:43:21 Terminated

And now mythfrontend won't start - GUI start, then dies with 

> 
2010-05-17 23:25:34.937 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-05-17 23:25:34.944 Using protocol version 56
mount: can't find /dev/sr1 in /etc/fstab or /etc/mtab
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread


I have done complete reinstalls on every myth* package in synaptic I can find. The Backend, according to MythTV-Status, is in fact working, but I can't communicate with it at all. Between this and 10.4 breaking gxine (the only thing I found that would actually run a DVD) my beautifully designed linux media center has become a rather expensive paperweight - if I hadn't bought linux-only video cards in a misplaced sense of optimism this experience might well have converted me back to Windows despite several years of enjoying Ubuntu (at least for this purpose).

As it is - I really don't want to reinstall the entire system partition and lose my database (Not to mention several months of recorded programs, but if I can't get the frontend back that's probably the next logical step.

If there's a better option available, some undocumented lock-file in a directory somewhere, I'd really like to hear it.

Thanks - Jonnan

---

### Post by dewmanstl on 2010-06-06
> **jonnan said:**
> 

As it is - I really don't want to reinstall the entire system partition and lose my database (Not to mention several months of recorded programs, but if I can't get the frontend back that's probably the next logical step.


Thanks - Jonnan

Why would you lost several months of recordings? Do you have all your recordings on the same spindle as the o/s? (yikes if you do) as far as the database, take an export and re-import if you rebuild. You can always back up your reordings to dvd and then copy them back over if they are on the same drive as the os.... 

Also best bet is to hit IRC and ask around..... =)

---

