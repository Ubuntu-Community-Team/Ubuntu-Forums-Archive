---
title: "mounting windows network share:  &quot;connection timed out&quot;"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by thor_bjorn on 2011-01-05
I'm trying to mount a windows share network drive (on a university's server) using Ubuntu 10.04.  I'd like to make it a permanent mount, so I've added to etc/fstab, but am having problems with the following error:

```
mount error(110): Connection timed out
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Here's what I've done so far:
My /etc/fstab has:

```
//files.school.edu/shared    /mnt/shared   cifs   noauto,user,username=username,uid=user,gid=group,mode=700,filemode=600   0 0
```

I have smbfs installed.  I've created mnt/shared.  Then from

```
sudo mount /mnt/shared
```

I type in my password, wait awhile, then get the "Connection timed out" error message above.

I've solved a couple of problems already to get here, but my ignorance has kept me from getting further.  Any ideas?  I'll be more than happy to post some output - let me know what I should be looking at.  Thanks.

---

### Post by dandnsmith on 2011-01-05
Have you tried whether you can access the resource by using the Places item on the taskbar, and then follow the dialog for 'connect to server' under network?
If you can get that to work, then it's just down to detail. Otherwise there is a permissions problem to sort out (probably at the server end)

---

### Post by thor_bjorn on 2011-01-06
dandnsmith - thanks.

After doing what I describe above, I rebooted my computer, and the share still did not mount.  However, I started it up this morning, and everything worked.  Great!

If you're looking to do something like this, try what I've done above.  It worked for me!

bjorn

---

### Post by dandnsmith on 2011-01-06
Glad to hear it works now.
A couple of quick comments:
- you don't need (I believe) the full samba stuff if you are not creating shares for Windows machines to access (the default stuff installed with ubuntu is enough to allow you network access to external shares).
- it's surprising how often re-booting and waiting will 'solve' a problem (especially if anywhere it involves Windows servers). I've seen it so many times that I tell people  'just wait, and try again' if it ought to work, but doesn't. There can also be questions concerning the number of network connections (and length of life) on Windows sharing.

---

