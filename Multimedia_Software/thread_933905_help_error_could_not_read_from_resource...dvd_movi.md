---
title: "help error: could not read from resource...dvd movies"
date: 2008-09-29
forum: Multimedia Software
---

### Post by Unlearned on 2008-09-29
i just bought a new computer a dell xps m1530
it has a blu ray/dvd/cd drive and it reads the disks i put in, but when trying to play the movie dvds get a message:
         An error occurred
         could not read from resource

what can i do to fix this

---

### Post by mc4man on 2008-09-30
Unless there's something specific to that drive (being bluray, ect) then it's usually very straightforward to enable dvd playback (standard def)

First thing to get out of the way is to ck. if a region has been set.

```
sudo apt-get install regionset
```
With a *dvd in the drive* run from terminal```
 regionset
``` 
If  around line 4 you see 'set' then answer no and exit.
If it doesn't say set (also you'll see 5 **user** changes) then set it to your region and exit. ( A drive only has to be set **once**,
R 1- n america
R 2 - europe, ect.(look up the rest if not these

once your good there go here and follow from the top

[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

(whether you want vlc or not install it - it fills in a lot of needed libs, can always be removed later (excellent player
totem-xine is much better than totem

If you use vlc read at bottom about *changing the launch command*

If any problems specific to the drive and or dell see here

[http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

---

