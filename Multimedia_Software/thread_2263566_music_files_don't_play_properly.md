---
title: "music files don't play properly"
date: 2015-02-01
forum: Multimedia Software
---

### Post by kris35 on 2015-02-01
Hi all, 

Suddenly after years of Ubuntu goodness my music files have stoopped playing properly.
The time count is erratic and much faster than the actual length of the song. this results in the time running out before the song finishes. After this point the songs start playing in 'fast forward' and controls become sluggish. pausing and restarting and/or changing songs results in the cycle repeating.

I have tried several different media players, all behave the same.
video files in the same directories, both internal and external, do not seem to be affected even using the same players as the crashing music files.
reinstalling players has no effect.

when booted to windows there is no problem playing the same files from the same external hard drive.
any insight will be greatly appreciated.
Cheers
Kris

---

### Post by Yellow Pasque on 2015-02-02
My first instinct would be to try resetting user's pulseaudio config:
```
rm -r ~/.config/pulse*
pulseaudio -k
```

---

### Post by kris35 on 2015-02-03
Hey Temujin, 
Thanks for taking the time to help out. I copied and pasted your commmand into the terminal and got back 'rm: cannot remove &#8216;/home/-----/.config/pulse*&#8217;: No such file or directory'  Needless to say I don't spend much time in the terminal, however, since you mentioned pulseaudio I went to software center and uninstalled all the pulseaudio I had, and... everything went back to the way it should be. The savage beast is soothed once more.
Cheers my friend,
kris
[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=327594")

---

### Post by Rob Sayer on 2015-02-04
You shouldn't actually purge pulseaudio.  It has too many dependencies, and this will probably cause problems at some time.

There are lots of blogs etc recommending removing it, but there are a lot of crap blogs.

What I's do is reinstall pulseaudio and do step 2 from this, which is from a decent blog by a canonical dev:

[http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)

---

### Post by kris35 on 2015-02-11
Cool, thanks for all the good info, and for taking the time.
Cheers!

---

