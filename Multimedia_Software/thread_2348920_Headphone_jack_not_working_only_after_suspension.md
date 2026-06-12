---
title: "Headphone jack not working only after suspension"
date: 2017-01-09
forum: Multimedia Software
---

### Post by divad.mi on 2017-01-09
Hello, this is my alsa information script: [http://www.alsa-project.org/db/?f=7e3af92641e1feb3827b27af26b38a267e643466](http://www.alsa-project.org/db/?f=7e3af92641e1feb3827b27af26b38a267e643466)

My problem is that both my speakers and headphones work completely fine on startup, but after I wake up my laptop from suspension, the headphone jack stops producing sound. Shutting down completely and starting it up again resolves it, but the problem persists every time my laptop is suspended. I've never used a unix-based system before, and am fairly new to using the shell in general (even with windows / mac) so I'm pretty clueless right now as in what to do. Any help is really appreciated.

[B]more info:
[/B]To initially solve the suspension problem, I made a "09alsa" text file under /etc/pm/sleep.d/09alsa
and this is my code in that file:
------------------------------------------------------------------------
#!/bin/sh
case "$1" in
        hibernate|suspend)
                # Stopping is not required
                ;;
        thaw|resume)
                /sbin/alsa force-reload > /dev/null
                sleep 1
                /usr/sbin/alsactl restore 
                ;;
        *) exit $NA
                ;;
esac
-------------------------------------------------------------------------

I got that from here: [https://ubuntuforums.org/showthread.php?t=1475616&page=2](https://ubuntuforums.org/showthread.php?t=1475616&page=2)

There was initially no alsa file there for me, which is why I had to make one. The code did work to fix the sound once, but now every time my laptop goes under suspension I have to completely shut it down for the headphones to work again; simply re-starting doesn't work. Or even force reloading alsa.

The following two links is what I've found of similar code to help with this problem:
[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit#heading=h.jp1hspvoc96e](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit#heading=h.jp1hspvoc96e)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) -- where it says "Getting ALSA to work after suspend / hibernate", which I also tried but had the same issues.

I was wondering if the naming of the file matters, as they all do it differently, and what I'm missing to get it to work.

---

### Post by soodvarun78 on 2017-01-11
Please send alsa-info.sh log when audio is not coming after wakeup from suspension

---

### Post by divad.mi on 2017-01-11
When it works:
[http://www.alsa-project.org/db/?f=af2352ea94db8a4bd93c890ac1428aff67f701e9](http://www.alsa-project.org/db/?f=af2352ea94db8a4bd93c890ac1428aff67f701e9)

When it doesn't work after suspension:
[http://www.alsa-project.org/db/?f=4e24ed42f5511af11346c401150ae7f2fdd5b74b](http://www.alsa-project.org/db/?f=4e24ed42f5511af11346c401150ae7f2fdd5b74b)

Also, I'm still very much a noob; none of the code I posted before would work because the commands, like force-reload etc, don't fix the problem when run after suspension in the first place. So making that file to automate it is pointless. The problem is somewhere else, which I don't know where :confused:

---

