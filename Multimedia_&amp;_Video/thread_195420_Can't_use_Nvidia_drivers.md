---
title: "Can't use Nvidia drivers"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by exuberance on 2006-06-12
I recently decided to try ubuntu again and I'm having trouble getting the nvidia drivers to work.  I've tried installing them using several different guides, but each time when I try to start ubuntu when it gets to the login screen my monitor says that there is no signal.

If I revert my xorg.conf back to how it was originally everything works fine, but without any 3d acceleration.  I'm sure the problem is something simple, but I have no idea what it could be, and this is really a dealbreaker for me.  If anyone has a suggestion or would like more information I'd greatly appreciate it.

EDIT: Commenting out the Load "extmod" line in the xorg.conf seems to have solved the problem.

---

