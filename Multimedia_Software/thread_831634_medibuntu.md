---
title: "medibuntu"
date: 2008-06-17
forum: Multimedia Software
---

### Post by meatlegs on 2008-06-17
Hello all,
I'm having trouble with my video playback such as freezing and deinterlacing, so I was trying to install the medibuntu packages through the terminal and I'm getting this weird error:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release)  Unable to find expected entry  rsudo/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

I've looked into a couple threads and one is suggesting I do this:

Remove duplicate sources.
Press Alt+F2 and type this:
gksu gedit /etc/apt/sources.list
It will open sources.list file in Gedit with root privileges.
Delete all contents and add these sources :
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse


Does this make sense to anyone?
I'm not sure and I don't want to break anything.

Thanks!

---

### Post by meatlegs on 2008-06-17
Never mind, i think I fixed it with this thread: :)
[http://ohioloco.ubuntuforums.org/showthread.php?t=812653](http://ohioloco.ubuntuforums.org/showthread.php?t=812653)

---

