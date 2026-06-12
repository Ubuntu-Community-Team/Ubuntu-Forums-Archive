---
title: "Problem with Audacious 3.2.1 on Ubuntu 12.04"
date: 2012-04-27
forum: Multimedia Software
---

### Post by stegod on 2012-04-27
I installed Audacious 3.2.1 on Ubuntu 12.04 with the software center and everything is fine, but as soon as i try to import my music from the NTFS hard drive it imports it and then shuts itself down as soon as it finishes how can i fix the problem?

---

### Post by stegod on 2012-04-27
I started it in the Terminal and this is what came out after the crash!

WARNING: Audacious seems to be already running but is not responding.
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Unknown tuple field name "encoder".
Floating point exception (core dumped)

---

### Post by stegod on 2012-04-27
FIX:

Delete the old version.
Update to the new one.

Enable the repository:
# sudo add-apt-repository ppa:nilarimogard/webupd8
Update the package index:
# sudo apt-get update
Install audacious deb package:
# sudo apt-get install audacious

Gives some errors but works ;}

---

### Post by crazyjust on 2012-06-01
[LEFT]Thank you [stegod]("http://ubuntuforums.org/member.php?u=812737"). I also had this problem, and your instruction worked great. I would like to add this for anyone else having these problems with audacious and ubuntu 12.04. After you add the repository, update, and install, go to update manager. Install the updates, as this installs the plugins.
[/LEFT]

---

