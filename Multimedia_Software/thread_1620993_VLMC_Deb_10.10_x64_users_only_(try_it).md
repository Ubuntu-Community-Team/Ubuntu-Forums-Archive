---
title: "VLMC Deb 10.10 x64 users only (try it)"
date: 2010-11-13
forum: Multimedia Software
---

### Post by slooksterpsv on 2010-11-13
All,

I compiled VLMC - VLC Movie Creator (I think is what it's called). And I wanted to see if others are able to install it just from the DEB I created:

SYSTEM REQUIREMENTS:
Ubuntu 10.10 64-bit
VLC Installed

I didn't make a 32-bit version or a 10.04 version, 10.04 you'd have to install the Maverick VLC components.

It's pretty neat, let me know if it works:
[http://dl.dropbox.com/u/10077776/vlmc.deb](http://dl.dropbox.com/u/10077776/vlmc.deb)

EDIT:
Ahhh before you can install run this: sudo mkdir /usr/share/doc/vlmc/

this is all from a git source

EDIT 2:
I made modifications to the control file to where it shouldn't crash. So after it's done uploading I'll post the new link (about 3 min.)

EDIT 3:
Fixed file: [http://dl.dropbox.com/u/10077776/vlmc.deb](http://dl.dropbox.com/u/10077776/vlmc.deb)

---

### Post by mc4man on 2010-11-14
doesn't install  - how did you edit the control?
> $ sudo dpkg -i '/home/doug/Desktop/vlmc.deb' 
[sudo] password for doug: 
Selecting previously deselected package vlmc.
(Reading database ... 183917 files and directories currently installed.)
Unpacking vlmc (from /home/doug/Desktop/vlmc.deb) ...
dpkg: error processing /home/doug/Desktop/vlmc.deb (--install):
 unable to create `/usr/share/doc/vlmc/COPYING.dpkg-new' (while processing `./usr/share/doc/vlmc/COPYING'): No such file or directory
Errors were encountered while processing:
 /home/doug/Desktop/vlmc.deb

Edit - see you say to first create the doc folder - shouldn't have to do that

Went ahead and did a build using the cpack - it makes a mistake with the version in the control file, shouldn't be using a _
(also don't see where the install deps are correct or complete

So simply edited the control and the .deb installed fine (no need to create the doc folder first
> sudo dpkg -i /home/doug/vlmc-0.2.0_git68bcb78-Linux-x86_64.deb 
Selecting previously deselected package vlmc.
(Reading database ... 183917 files and directories currently installed.)
Unpacking vlmc (from .../vlmc-0.2.0_git68bcb78-Linux-x86_64.deb) ...
Setting up vlmc (0.2.0+git68bcb78) ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...


---

### Post by slooksterpsv on 2010-11-15
> **mc4man said:**
> doesn't install  - how did you edit the control?

Edit - see you say to first create the doc folder - shouldn't have to do that

Went ahead and did a build using the cpack - it makes a mistake with the version in the control file, shouldn't be using a _
(also don't see where the install deps are correct or complete

So simply edited the control and the .deb installed fine (no need to create the doc folder first

I used ar to extract the deb and changed the control file then repackaged it with ar.

Um... so I don't understand how you fixed it to not require that folder to be created. You said you made a modification to the control file. Was it just the control file that was holding back that directory?

---

### Post by mc4man on 2010-11-15
> Was it just the control file that was holding back that directory?
No, just how the version was written. i'd think your issue is with ar. Maybe try this little script, works well ( the one in post 4 is a liitle easier.

[http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724)

Easy to use, just put in path (~/bin works well), make executable.
If in ~/bin then in terminal just scriptname /path/to/deb
gedit will open, make changes, save and when you close gedit a new .modified.deb will be created in home folder 
*can be left as named or remove the .modified - doesn't matter.

The other thing is the cmake pakage build is using the build-deps for install deps - probably should be more like this or so.
Depends:libqt4-network (>= 4:4.5.3), libqt4-svg (>= 4:4.5.3), libqt4-xml (>= 4:4.5.3), libqtcore4 (>= 4:4.7.0~beta1), libqtgui4 (>= 4:4.6.2), libstdc++6 (>= 4.1.1), libvlc5 (>= 1.1.0), libvlccore4 (>= 1.1.0), libx11-6, vlc (>= 1.1.0)

Also note that if built from a 1.1.X vlc (libvlc). then most likely will not work with a 1.2+ vlc and vice versa

---

### Post by slooksterpsv on 2010-11-15
> **mc4man said:**
> No, just how the version was written. i'd think your issue is with ar. Maybe try this little script, works well ( the one in post 4 is a liitle easier.

[http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724)

Easy to use, just put in path (~/bin works well), make executable.
If in ~/bin then in terminal just scriptname /path/to/deb
gedit will open, make changes, save and when you close gedit a new .modified.deb will be created in home folder 
*can be left as named or remove the .modified - doesn't matter.

The other thing is the cmake pakage build is using the build-deps for install deps - probably should be more like this or so.
Depends:libqt4-network (>= 4:4.5.3), libqt4-svg (>= 4:4.5.3), libqt4-xml (>= 4:4.5.3), libqtcore4 (>= 4:4.7.0~beta1), libqtgui4 (>= 4:4.6.2), libstdc++6 (>= 4.1.1), libvlc5 (>= 1.1.0), libvlccore4 (>= 1.1.0), libx11-6, vlc (>= 1.1.0)

Also note that if built from a 1.1.X vlc (libvlc). then most likely will not work with a 1.2+ vlc and vice versa

Oh no I made it with AR afterwards - when Software Center wouldn't install it - , I didn't try after AR to see if that still gave me the error about the directory.

---

