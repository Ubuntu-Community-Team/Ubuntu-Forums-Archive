---
title: "Weird CIFS behavior"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by captkirk on 2008-12-20
Ok, it took me a while to get here.  I was having problems, and someone was helping me (about 10 months ago!).  Time took me away, then I had a crash on the network drive, I updated the firmware in my myworldbook and upgraded to 8.10.  I am still having odd behavior mounting mybookworld from western digital.  None of the upgrades helped my problem.

Basically, the drive seems to only let the user who mounts the drive write to it.  The sequence is over on _[http://ubuntuforums.org/showthread.php?t=710653]("http://ubuntuforums.org/showthread.php?t=710653")_

I am trying to follow the last suggested step, which identifies my problem, and I think the possible solution:
> 
If the users having trouble writing are in fact part of the "users" group, and if the shared directory is actually owned by group "users" as seen earlier, then ls -ld output for *only* the owner username having r/w permission would look like this:
Code:

ls -ld
drwxr-xr-x 25 n users 0 2008-02-23 23:11 /SHARE

Note that the second perms triplet here does *not* have the "w", and instead only shows a "-" in its place.

It is possible for directories created *within* the share to have no write permission for group members, depnding on something called your umask, which defines your username's default creation permissions. If ls -ld on the share directory itself shows group write, but sub-directories do not, that's fixable by changing the mode -- using the chmod command. Let me know if that's your trouble and we'll go from there.

I am sort of stuck here.  Can someone help me out of this quagmire?

---

