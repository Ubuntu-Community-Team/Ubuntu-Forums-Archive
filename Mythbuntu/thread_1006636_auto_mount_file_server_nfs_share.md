---
title: "auto mount file server nfs share"
date: 2008-12-09
forum: Mythbuntu
---

### Post by xyzacct on 2008-12-09
I have movies on a file server that I would like Mythbuntu to automount on startup, how do I do that? I added a line to fstab but it's not auto mounting. If I manually mount the nfs share it works fine.

---

### Post by nrune on 2008-12-09
A little search...

[http://ubuntuforums.org/showthread.php?t=940344&highlight=automount+windows+share](http://ubuntuforums.org/showthread.php?t=940344&highlight=automount+windows+share)

Pretty easy.

There is another how to in the forums, but I could not find it right off the bat.

enjoy

---

### Post by xyzacct on 2008-12-09
that's how I have my fstab setup...(I have several other linux boxen in my house that are setup for automounting of the fileserver's shares) but for some reason the mythbox isn't working.

---

### Post by xyzacct on 2008-12-09
Fixed:
I had
servername:/share /local/mountpoint nfs some-options 0 0
which didn't work. I changed it to
servername:/share /local/mountpoint nfs auto 0 0
and now it works.

---

