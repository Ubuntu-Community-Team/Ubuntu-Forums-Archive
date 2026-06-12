---
title: "VLC question"
date: 2009-08-05
forum: Multimedia Software
---

### Post by jonboy99 on 2009-08-05
FIXED

Is there any way in ubuntu jaunty to have the video controls (slide bar, play pause button etc) to be in the same window as the video itself?  At the moment they are in a separate window and with many windows open at once it is difficult to tell which control bar correlates with which video?

cheers
Jon

---

### Post by susenj on 2009-08-05
I am using Jaunty updated a month ago, and have seen the same problem with VLC.
I didn't find any solution regarding this. Even i am not able to find any cause for this.:confused::confused::confused:Please help!
 
> **jonboy99 said:**
> Is there any way in ubuntu jaunty to have the video controls (slide bar, play pause button etc) to be in the same window as the video itself?  At the moment they are in a separate window and with many windows open at once it is difficult to tell which control bar correlates with which video?

cheers
Jon

---

### Post by scorp123 on 2009-08-05
You have to use a newer version of VLC than what is in the official repos. In other words: You have to enable a third-party repository and tell the package manager to go and grab the VLC version from there.

There is a thread you might be interested in:
[http://ubuntuforums.org/showthread.php?p=7138708](http://ubuntuforums.org/showthread.php?p=7138708)

The same instructions as up there, just quite a bit shorter:

[LIST]
[*]Temporarily become the superuser "root" and create the file **/etc/apt/sources.list.d/vlc-ppa.list** ... e.g. type this into a terminal:
```
gksudo gedit /etc/apt/sources.list.d/vlc-ppa.list
```
[*]If you are a KDE user (e.g. you installed Kubuntu) then the command would be slightly different:
```
kdesu kate /etc/apt/sources.list.d/vlc-ppa.list
```
[*]Copy and paste this stuff here and put into the editor:
```
# [http://ubuntuforums.org/showthread.php?p=7138708](http://ubuntuforums.org/showthread.php?p=7138708)
#
# [https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)
#
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DD4676FD8F10A7A7B9D8B1F60E494DBB2F021AC1
# 
deb [http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) jaunty main
```
[*]What the lines do: The first 6 lines are just comments, they do nothing. Why comments? I always like to know where the heck I got the information for a repository from, just in case I need to re-install something again. And I also like to put the key infos there ... Error messages about missing keys are a pain. Only the two last lines really do something: They will tell your package manager where it will find a newer version of VLC.
[*]Once you're perfectly sure that your file is 100% identical to those lines above: save & close the file.
[*]To authenticate that repository you have to get its crypto keys. Do as the last comment line above says and execute this command:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DD4676FD8F10A7A7B9D8B1F60E494DBB2F021AC1
```
[*]Once this is done you have to refresh your software information:
```
sudo apt-get update
```
[/LIST]

Voila, done. Just copy & paste the stuff above. Once you got this far the udpate pop-up should inform you about there being an update for VLC. And just in case it doesn't: Simply install "vlc" again, either the GUI way via the "Synaptic" package manager or via the shell:
```
sudo apt-get install vlc
```

Voila ... new VLC, all in one window, in less than 10 minutes. :)

---

### Post by binbash on 2009-08-05
[http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html](http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html)

---

### Post by jonboy99 on 2009-08-06
Sorted - thanks folks.  Took less than 3 minutes.  :D

---

