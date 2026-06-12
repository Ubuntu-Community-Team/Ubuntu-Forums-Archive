---
title: "vlc and media player stopped playing movie files - jaunty"
date: 2009-08-03
forum: Multimedia Software
---

### Post by subdural on 2009-08-03
All - I'd be really grateful if you could help me out.

very recently - circa 3 weeks ago - vlc stopped playing movie files.  it just opens up the file, looks like it is going to play the file, and then closes down.  the same happens with movie player.  it can be .avi or .wmv, it doesn't matter.

nothing else happens - jaunty doesn't crash.

grateful if you could help me out, and apologies already if my request is too general.

cheers

Sub

---

### Post by pmlxuser on 2009-08-03
try completly uninstalling it $sudo apt-get purge vlc and then reinstalling it $ sudo apt-get install vlc

as it looks i think some configuration file got messed up (but difficult to guess which one so purging will remove everything and if you reinstall it might solve your problem)

---

### Post by pmlxuser on 2009-08-03
try completly uninstalling it $sudo apt-get purge vlc and then reinstalling it $ sudo apt-get install vlc

as it looks i think some configuration file got messed up (but difficult to guess which one so purging will remove everything and if you reinstall it might solve your problem)

---

### Post by subdural on 2009-08-03
many thanks for your speedy help.  Here's what I get when i try the purge:
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

cheers
Sub

---

### Post by bikerman2299 on 2009-08-03
I am just trying to get vlc installed on my machine. This is what I get when I run this command: 

 sudo apt-get install vlc

It returns this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: libqt4-core (>= 4.3.4) but it is not installable
       Depends: libqt4-gui (>= 4.3.4) but it is not installable
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: vlc-nox (= 0.9.9a-1~ppa1~hardy2) but it is not going to be installed
E: Broken packages


I am still learning and would really appreciate some help. Thanks in advance!

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

---

### Post by subdural on 2009-08-25
Hmmm, now vlc has all of a sudden started working perfectly.  I didn't do anything.  Maybe it was swept up in another update e.g. system update or other update?

thanks to all who tried to help.

Sub

---

### Post by philipMac on 2009-08-28
just another note, Totem stopped working for me also, I did a purge remove and re-install, nothing.  Jaunty, 64bit.  It was working perfectly with wmv previously and never ran again after the Jaunty update. 

I have just given up using Totem (again), and switched to VLC.

---

### Post by An85Zk9tc8rfjV8i on 2009-10-23
> **subdural said:**
> vlc stopped playing movie files.  it just opens up the file, looks like it is going to play the file, and then closes down.  the same happens with movie player.  it can be .avi or .wmv, it doesn't matter.

> **pmlxuser said:**
> i think some configuration file got messed up (but difficult to guess which one so purging will remove everything and if you reinstall it might solve your problem)

> **philipMac said:**
> Totem stopped working for me also, I did a purge remove and re-install, nothing.  Jaunty, 64bit.

uninstall + reinstall does not effect config files

need to HIDE (delete or rename) the appropriate config files

Totem config file is in ~/.config/totem

VLC config files are in ~/.config/vlc

VLC + Totem should rebuild the config files when restarted

---

