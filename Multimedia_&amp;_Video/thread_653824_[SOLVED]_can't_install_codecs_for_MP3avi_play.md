---
title: "[SOLVED] can't install codecs for MP3/avi play"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by Irishpolyglot on 2007-12-30
Hi guys, I've searched through the forum and this guy [http://ubuntuforums.org/showthread.php?t=532613](http://ubuntuforums.org/showthread.php?t=532613) had the same problem as me, but the solution provided doesn't work for me.
Basically I installed distro 7.10, but I didn't have any internet connection during the installation. A warning message came up to say that I can't install security updates, but I figured I'd just get them when online. Now when I try to play an mp3, or an avi I get the message to download the codecs, confirm and I get this errror
> Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.
In Synaptic gstreamer0.10-plugins-ugly is not ticked, so I mark for installation, but get this error:
> gstreamer0.10-plugins-ugly:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable
libid3tag0 and libmad0 don't come up in the search. I tried the solution offered in the above thread of > sudo rm /var/lib/apt/lists/partial/* 
sudo apt-get update

and then refreshing Synaptic but that doesn't do anything...
Any solutions (other than reinstalling the distro with a connection) greatly appreciated! :)

---

### Post by taurus on 2007-12-30
Do you have all the repos available in synaptic?  Look in Settings -> Repositories and make sure there is a check mark for all except the last one, Sources code.  Then, Close that window and hit th Refresh button on synaptic to refresh it.  Now, see if you can install it again.

---

### Post by Irishpolyglot on 2007-12-30
Very intuitive answer!! Here was me expecting hours of coding lol - solution was right under my nose!! You have now officially taken away my last reason for needing to boot into Windows EVER. Cheers :)

---

