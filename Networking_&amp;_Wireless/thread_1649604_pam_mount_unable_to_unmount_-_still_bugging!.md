---
title: "pam_mount unable to unmount - still bugging?!"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by steelsteel! on 2010-12-20
Hello out there!

An old annoying bug: [https://bugs.launchpad.net/pam/+bug/117736](https://bugs.launchpad.net/pam/+bug/117736)
An old thread already exists: [http://ubuntuforums.org/showthread.php?t=459462](http://ubuntuforums.org/showthread.php?t=459462)
No one cares about it: [http://sourceforge.net/tracker/?func=detail&atid=430594&aid=3116847&group_id=41452](http://sourceforge.net/tracker/?func=detail&atid=430594&aid=3116847&group_id=41452)

And still active in the combination libpam_mount + ubuntu 10.10 + ssh + su otheruser
as described in the former thread.

I managed to script an umount of an userspecific home - but i got no idea how to unmount a group directory, when the user logs out. Next user should be forced to mount this group directory with his own credentials - to enable pursue of abuse.

Al i need is a working umount when the actual user logs out.

Are there any news concerning this bug?
I understand it as a "su" problem - is that right?

No one?

---

### Post by steelsteel! on 2010-12-22
*bump*

---

### Post by dariosh on 2011-09-20
Hello

SteelSteel has right, nobody taking care of this bug!  ](*,)
All we need is a working "umount" when the actual user logs out.

Please HELP!!!!

---

### Post by nothingspecial on 2011-09-20
Hi dariosh,

Please create a new thread of your own rather than digging up an old one.

Thank you

Closed

---

