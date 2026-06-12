---
title: "What is mplayer executable (in smplayer)"
date: 2011-07-21
forum: Multimedia Software
---

### Post by mrjayuk on 2011-07-21
I stupidly was messing arround with the setting in smplayer and now am unable to play anything as i cant find a mplayer executable, what is this? where is it? and how do i get it back. I have unistalled smplayer reinstalled it and problem persitst. also if and when i get this working again is there anyway to stop the screen freezin when i play a vid in full screen?

---

### Post by mc4man on 2011-07-21
typically it would be entered just as 
mplayer
or if using the the default installed mplayer you could enter 
/usr/bin/mplayer

If you wish to reset smplayer's config then open home folder > view - show hidden files
Browse to .config/smplayer and delete smplayer.ini

---

### Post by lkjoel on 2011-07-21
Open up a Terminal window, and type in it:
```
sudo apt-get purge smplayer
sudo apt-get install smplayer
```
This will remove the configuration files completely.

---

### Post by .... on 2011-07-22
For reference, the which command is helpful for things like this:
```
$ which mplayer
/usr/bin/mplayer
```
Also note that some people use /usr/bin/mplayer2 for multithreaded mplayer.

---

### Post by mrjayuk on 2011-07-22
thanks guys will try that all now, any chance you would know why when smplayer was working it would freeze in full screen? the video would still play but i could not do anything else?

---

