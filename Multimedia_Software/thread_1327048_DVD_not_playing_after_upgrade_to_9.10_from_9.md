---
title: "DVD not playing after upgrade to 9.10 from 9"
date: 2009-11-15
forum: Multimedia Software
---

### Post by dwcbrq on 2009-11-15
Help!

I upgraded to Ubuntu 9.10, and my DVD isn't playing.  When I click on whatever app to play, the DVD starts spinning, but nothing happens.

Thanks :-|

---

### Post by captain granite on 2009-11-15
> **dwcbrq said:**
> Help!

I upgraded to Ubuntu 9.10, and my DVD isn't playing.  When I click on whatever app to play, the DVD starts spinning, but nothing happens.

Thanks :-|

Hello Guys and gals,
                             This is a similar thread, I too am on 9. 10 and dvd's wont play at all, it keeps asking for a gstreamer element which I cant seem to find, can anyone suggest a work around or a dvd player that works, all I want to do is watch a dvd, I am lazy I suppose and used to things working straight out of the box, anyone had a similar experience or am I doing something wrong..............
                                            Thanks 
                                            Captain

---

### Post by geopteryx on 2009-11-15
After an upgrade from 9.04 to 9.10, I used to have the same problem. I've solved it by installing all gstreamer plugins (base, good, bad, ugly). Try this:
```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```
Install ffmpeg too:
```
sudo apt-get install gstreamer0.10-ffmpeg
```
Cheers

---

### Post by dwcbrq on 2009-11-16
> **geopteryx said:**
> After an upgrade from 9.04 to 9.10, I used to have the same problem. I've solved it by installing all gstreamer plugins (base, good, bad, ugly). Try this:
```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```Install ffmpeg too:
```
sudo apt-get install gstreamer0.10-ffmpeg
```Cheers

Those were already installed.

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly set to manually installed.

...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-ffmpeg is already the newest version.



Why would it work on 9.04 and not on 9.10?

---

### Post by gwm on 2009-12-16
Hi,
same problem
fixed it on another box last night.
found your thread while searching for the fix so i can apply it to this box too
it involved installing 5 plugins, of which 3 were already installed.
looks like you also have the 3.
will return with solution once i've found it again

---

### Post by gwm on 2009-12-16
```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg gstreamer0.10-pitfdll
```
found the above code in this link
[http://ubuntuforums.org/showthread.php?t=1322371](http://ubuntuforums.org/showthread.php?t=1322371)
mc4man has us install 6 plugins in this case
my box couldn't find pitfdll but the dvd seems to be playing fine anyhow

---

