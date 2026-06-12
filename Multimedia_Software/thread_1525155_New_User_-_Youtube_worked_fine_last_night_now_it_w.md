---
title: "New User - Youtube worked fine last night now it wont"
date: 2010-07-06
forum: Multimedia Software
---

### Post by USFMD82 on 2010-07-06
Hello everyone, I d/l ed Xubuntu last night and I did the code
```
sudo apt-get install flashplugin-nonfree

```

and it worked fine last night, I restarted my computer today and Youtube wont load and Grooveshark wont work either (I didnt test grooveshark last night so no idea if that is related).

any help is apprecciated.

---

### Post by dabl on 2010-07-06
Follow the instructions here for Xubuntu:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by USFMD82 on 2010-07-06
So I been going throguh it, and I am stuck on the first part right now..

here is what I am getting I keep doing what it says and i get the same error

> timber@ubuntu:~$ **sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
_E: Couldn't find package gstreamer0.10-pitfdll_
timber@ubuntu:~$ **sudo rm /var/lib/apt/lists/partial/***
rm: cannot remove `/var/lib/apt/lists/partial/*': No such file or directory
timber@ubuntu:~$ **sudo apt-get update**


I dont know what I am doing wrong here..

---

### Post by USFMD82 on 2010-07-06
```
timber@ubuntu:~$ sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-plugin-vlc totem-mozilla xine-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kaffeine-mozilla is not installed, so not removed
E: Couldn't find package mozilla-helix-player
timber@ubuntu:~$ 
```


still having problems thanks in advance for the assistance

---

### Post by sinichiro on 2010-07-06
A silly question, but did you enable the recommended repositories? E: Couldn't find package ..." might mean the package can't be found in the repositories you have enabled.

"Xubuntu Users: Navigate to "Applications > System > Software Properties" and make sure the Multiverse and Universe repositories are enabled by ticking the relevant boxes. As with Ubuntu and Kubuntu, you may want to enable unsupported (backports of newer software) updates for your system, disable the CD/DVD-ROM source, and choose a local server for all your system-related downloads."

I'm new too, so not really sure if I can be of any help.

---

### Post by USFMD82 on 2010-07-06
Lol, thanks for jumping in, yes I am pretty sure I did all of that, screeshots below ( Ialso added a screenshot of my plug-ins for Firefox) when I go to yourube, it just says done at the bottom and I see the comments and te other video links to the side but that is it.

would it matter if these instructions are for 8.04 and im using a different/newer version

---

### Post by USFMD82 on 2010-07-07
Ok this is wierd, I restarted it and it all works fine, I will try it a few days before considering this as solved. Anyone know what could be going on why it would intermittenlty go in and out?

I still have the issue of being unable to instlal all those packages due to them not being found, anyone know how to fix that issue? shoudl I post that in the main page?

---

### Post by Rhemat on 2010-07-07
Copy and paste the package names into a Google search, and you should find them if they are not in the repos.  This will mean manually putting them in the proper directory(ies), but there are guides out there to do so.

---

