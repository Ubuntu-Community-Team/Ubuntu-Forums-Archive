---
title: "Odd Problem - Only some sub-directories in Windows 7 share are visible"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by ChimpTX on 2011-03-10
I have an odd problem.  I am able to mount a windows share in 10.04 (for XBMC) and get into the shared directory.  (The shared directory is a Movies directory with a sub-directory for each movie.)  But then I'm only able to see some of the sub-directories in the share.  For example, roughly half show up with an "ls" command.  The other sub-directories are simply not listed.

However, if I try a "cd" command for a sub-directory that should be there, but is not visible, it works.  I'm shown that I'm in the path of the sub-directory.  And I'm then able to see the files in the sub-directory.

So I can't seem to solve this mystery of some sub-directories showing up and some not.  Any suggestions?  :confused:

On the Windows 7 machine the permissions are the same for all sub-directories.  And since I can actually access all the sub-directories I'm pretty sure it's not a permissions issue.  And looking around at attributes I can't find anything that really correlates to which sub-directories are visible and which are not.

---

### Post by randumnumber on 2011-03-10
> **ChimpTX said:**
> I have an odd problem.  I am able to mount a windows share in 10.04 (for XBMC) and get into the shared directory.  (The shared directory is a Movies directory with a sub-directory for each movie.)  But then I'm only able to see some of the sub-directories in the share.  For example, roughly half show up with an "ls" command.  The other sub-directories are simply not listed.

However, if I try a "cd" command for a sub-directory that should be there, but is not visible, it works.  I'm shown that I'm in the path of the sub-directory.  And I'm then able to see the files in the sub-directory.

So I can't seem to solve this mystery of some sub-directories showing up and some not.  Any suggestions?  :confused:

On the Windows 7 machine the permissions are the same for all sub-directories.  And since I can actually access all the sub-directories I'm pretty sure it's not a permissions issue.  And looking around at attributes I can't find anything that really correlates to which sub-directories are visible and which are not.

Do any of your directories start with a period ".foldername" in linux this is a hidden file and wont be listed try the command " ls -a " this will list all files even those with a . in the front of it.

---

### Post by ChimpTX on 2011-03-11
Nope, no periods.  An "ls -al" doesn't show the missing directories. 

Both a Windows 7 and a Mac OS X machine can see all of the shared sub-directories properly. Even an iPhone with a file app can see them. Hence my puzzlement as to why the ubuntu 10.04 boxes cannot beams issue on two different boxes, both running XBMC Live 10.1.

---

### Post by ChimpTX on 2011-03-12
Bump

---

### Post by utterfanskap on 2011-03-15
I had the same problem (affected my Sonos system as well). It turns out it was caused by installing "Avast! Free 6" on my windows 7 machine. Removed Avast and now things are working fine again.

---

