---
title: "Cannot install samba on a fresh install Ubuntu 12.04.2"
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by aria2 on 2013-03-08
Hello,
New to Ubuntu, but 2 years experience with Ubuntu-based distros.

I recently installed Ubuntu 12.04.2 on one of my machines, and:
[LIST=1]
[*]When I try to share folders in Nautilus, it asks to install samba. Confirm installation, but process aborts with errors. 
[*]Went to Synaptics and tried to install samba from there. The following error message popped up: 
[/LIST]
> samba:
Depends: samba-common (=2:3.6.1-3ubuntu3) but 2:3.6.3-2ubuntu2.3 is to be installed
Depends: libwbclient0 (=2:3.6.1-3ubuntu3) but 2:3.6.3-2ubuntu2.3 is to be installed
Recommends: tdb-tools but it is not going to be installed
Same message when trying to install from a terminal.

It really seems that samba depends on older packages that are no more in the repositories (note I checked all repositories in the software sources).
Note that both files 2:3.6.3-2ubuntu2.3 it says "are to be installed" are already installed. But samba wants only 2:3.6.1-3ubuntu3, which are not found.
Also note that (as mentioned in the title), this is a fresh install of 12.04.4, so it has only the latest kernel. Or, packages asked by samba might belong to older kernels...

What should I do to get samba installed?

Thanks,
PS: Didn't have such issues with Kubuntu 12.04 (I run on another machine), where samba came installed with the distro.

---

### Post by aria2 on 2013-03-10
Solved: Changed the server, from whatever the software sources chose for best server, to the main one. No more pop-up messages and samba installed smoothly (with tdb-tools as dependencies, which previously were only recommended). Checked if working, and it does as it should.

Also huge updates/upgrades after moving to the main server: kind of post-installation ones (updates/upgrades I already made from the previous server, but seems to have been obsolete).

Will stick with the main server from now one.

PS: How do I mark this tread Solved? No such option in Thread tools, nor in Edit post...

---

