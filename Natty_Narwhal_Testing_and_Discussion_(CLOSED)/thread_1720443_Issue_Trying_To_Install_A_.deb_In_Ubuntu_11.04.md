---
title: "Issue Trying To Install A .deb In Ubuntu 11.04"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by TheMixtureMedia on 2011-04-03
I am trying to install a game that worked with Ubuntu 10.10 and now Ubuntu 11.04 comes up with this issue. Does anyone know what might be wrong with this issue so I can try to fix it.

The package is of bad quality

The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath.


Lintian check results for /media/Another Drive/Games That I Own/RevengeOfTheTitans-HIB-amd64-3.deb:
E: revenge-of-the-titans: control-file-has-bad-owner md5sums 0/0 != root/root
W: revenge-of-the-titans: extended-description-line-too-long
md5sum: /opt/revengeofthetitans/RevengeOfTheTitans.jar: No such file or directory
md5sum: /opt/revengeofthetitans/common.jar: No such file or directory
md5sum: /opt/revengeofthetitans/gamecommerce.jar: No such file or directory
md5sum: /opt/revengeofthetitans/gfx.jar: No such file or directory
md5sum: /opt/revengeofthetitans/jinput.jar: No such file or directory
md5sum: /opt/revengeofthetitans/jorbis.jar: No such file or directory
md5sum: /opt/revengeofthetitans/libjinput-linux64.so: No such file or directory
md5sum: /opt/revengeofthetitans/liblwjgl64.so: No such file or directory
md5sum: /opt/revengeofthetitans/libopenal64.so: No such file or directory
md5sum: /opt/revengeofthetitans/lwjgl.jar: No such file or directory
md5sum: /opt/revengeofthetitans/lwjgl_util.jar: No such file or directory
md5sum: /opt/revengeofthetitans/revenge.png: No such file or directory
md5sum: /opt/revengeofthetitans/revenge.sh: No such file or directory
md5sum: /opt/revengeofthetitans/sound.jar: No such file or directory
md5sum: /opt/revengeofthetitans/spgl-lite.jar: No such file or directory
md5sum: /usr/share/applications/revenge.desktop: No such file or directory
md5sum: /usr/share/menu/revenge: No such file or directory
internal error: command failed with error code 123
W: revenge-of-the-titans: maintainer-not-full-name Puppygames
W: revenge-of-the-titans: package-relation-with-self provides: revenge-of-the-titans
W: revenge-of-the-titans: package-relation-with-self replaces: revenge-of-the-titans
E: revenge-of-the-titans: tar-errors-from-data Removing leading `/' from member names
E: revenge-of-the-titans: tar-errors-from-data Removing leading `/' from member names
E: revenge-of-the-titans: no-copyright-file
warning: collect info md5sums about package revenge-of-the-titans failed
warning: skipping check of binary package revenge-of-the-titans
/bin/rm: cannot remove `/tmp/Vx4fi6izUg/binary/revenge-of-the-titans': Directory not empty
warning: cannot remove lab directory /tmp/Vx4fi6izUg (please remove it yourself)
warning: cannot remove lab directory /tmp/Vx4fi6izUg (please remove it yourself)

---

### Post by andrewthomas on 2011-04-03
Get the source from where you got that package and build it against 11.04 yourself.  

You cannot expect every package built for 10.10 to work in 11.04.

---

### Post by PCaddicted on 2011-04-03
You'd better downgrade to Ubuntu 10.10(Maverick Meerkat).The Natty Narwhal is beta.It will pass the beta phase by the end of this month,than you can safely upgrade to Natty.

---

### Post by clhsharky on 2011-04-03
TheMixtureMedia


Most of the Natty testers on this fourum hang at
Development & Programming>Natty Narwhal Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)
Try asking there.

Sharky

---

### Post by TheMixtureMedia on 2011-04-03
How would I downgrade to 10.10?

---

### Post by TheMixtureMedia on 2011-04-03
I am trying to install a game that worked with Ubuntu 10.10 and now Ubuntu 11.04 comes up with this issue. Does anyone know what might be wrong with this issue so I can try to fix it.

The package is of bad quality

The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath.


Lintian check results for /media/Another Drive/Games That I Own/RevengeOfTheTitans-HIB-amd64-3.deb:
E: revenge-of-the-titans: control-file-has-bad-owner md5sums 0/0 != root/root
W: revenge-of-the-titans: extended-description-line-too-long
md5sum: /opt/revengeofthetitans/RevengeOfTheTitans.jar: No such file or directory
md5sum: /opt/revengeofthetitans/common.jar: No such file or directory
md5sum: /opt/revengeofthetitans/gamecommerce.jar: No such file or directory
md5sum: /opt/revengeofthetitans/gfx.jar: No such file or directory
md5sum: /opt/revengeofthetitans/jinput.jar: No such file or directory
md5sum: /opt/revengeofthetitans/jorbis.jar: No such file or directory
md5sum: /opt/revengeofthetitans/libjinput-linux64.so: No such file or directory
md5sum: /opt/revengeofthetitans/liblwjgl64.so: No such file or directory
md5sum: /opt/revengeofthetitans/libopenal64.so: No such file or directory
md5sum: /opt/revengeofthetitans/lwjgl.jar: No such file or directory
md5sum: /opt/revengeofthetitans/lwjgl_util.jar: No such file or directory
md5sum: /opt/revengeofthetitans/revenge.png: No such file or directory
md5sum: /opt/revengeofthetitans/revenge.sh: No such file or directory
md5sum: /opt/revengeofthetitans/sound.jar: No such file or directory
md5sum: /opt/revengeofthetitans/spgl-lite.jar: No such file or directory
md5sum: /usr/share/applications/revenge.desktop: No such file or directory
md5sum: /usr/share/menu/revenge: No such file or directory
internal error: command failed with error code 123
W: revenge-of-the-titans: maintainer-not-full-name Puppygames
W: revenge-of-the-titans: package-relation-with-self provides: revenge-of-the-titans
W: revenge-of-the-titans: package-relation-with-self replaces: revenge-of-the-titans
E: revenge-of-the-titans: tar-errors-from-data Removing leading `/' from member names
E: revenge-of-the-titans: tar-errors-from-data Removing leading `/' from member names
E: revenge-of-the-titans: no-copyright-file
warning: collect info md5sums about package revenge-of-the-titans failed
warning: skipping check of binary package revenge-of-the-titans
/bin/rm: cannot remove `/tmp/Vx4fi6izUg/binary/revenge-of-the-titans': Directory not empty
warning: cannot remove lab directory /tmp/Vx4fi6izUg (please remove it yourself)
warning: cannot remove lab directory /tmp/Vx4fi6izUg (please remove it yourself)

---

### Post by dino99 on 2011-04-03
looks like a fake

---

### Post by Frogs Hair on 2011-04-03
> **TheMixtureMedia said:**
> How would I downgrade to 10.10?

It is not possible to downgrade  a new installation of 10.10 would be required.

---

### Post by TheMixtureMedia on 2011-04-03
yeah but it worked with 10.10

---

### Post by david stevenson on 2011-04-03
I think "they" have turned on some more quality checking.
If you know the package is OK you can still install in from the command line with sudo dpkg -i.
I have just had to do this with qlc.
David

---

### Post by sdemmitt on 2011-04-03
I uninstalled the debian package checker in synaptic

Lintian

after that, package installs with software center work fine

or just use dpkg like the post above

---

### Post by CoolJohnB on 2011-04-03
I had the same problem with Skype, Chrome and Googleearth solved it by installing gdebi which installs everything just fine, will also try sdemmitt suggestions

---

### Post by FEGuy on 2011-04-03
There's actually a bug in the install process that kills installations for 'errors' that really ought to be ignored. Open a terminal and try like "sudo dpkg -i /path/to/my/installer/RevengeOfTheTitans-HIB-amd64-3.deb", or install GDebi, then navigate to the game installer, right-click it, and choose to install with GDebi Package installer. I haven't gotten around to re-installing Revenge of the Titans yet, but I'll go check now to make sure that's actually what the problem is.

EDIT: Installed just fine via GDebi, shouldn't be a problem for you to do the same.
EDIT2: That's the Humble Bundle version, right? I don't know when you downloaded that version, but if you have access to your Humble Bundle page, a new build was just released a couple days ago. The new version still refused to install via normal means, so try GDebi or the terminal command anyways.

---

### Post by TheMixtureMedia on 2011-04-04
Hi there I used GDebi and was able to install it. I hope they fix this issue for the 28th. Thank you everyone for your help.

---

### Post by TheMixtureMedia on 2011-04-04
Oh yes this is a humble bundle I will try the new verion that is out. This is solved thanks guys of your help.

---

### Post by TheMixtureMedia on 2011-04-04
Hi there I was able to get it to work thank you all for your help I installed GDebi and it works. Solved

---

### Post by howefield on 2011-04-04
Duplicate threads merged.

---

### Post by juancarlospaco on 2011-04-04
Solution:

GDebi
sudo dpkg -i

---

