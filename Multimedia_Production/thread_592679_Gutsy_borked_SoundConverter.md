---
title: "Gutsy borked SoundConverter?"
date: 2007-10-26
forum: Multimedia Production
---

### Post by whiskyprajer on 2007-10-26
I upgraded from Feisty to Gutsy. Smooth sailing mostly, but I am no longer able to use Sound Converter to rip OGG files to MP3. When I try the progress bar at the bottom reads, "file xxxx of yyyy (333 minutes remaining)". SC gets the file folders ready, but there is no conversion happening. Is there a setting I need to change?

I tried removing/reinstalling SC, as well as all the gstreamer uglies, but still no success.

---

### Post by Stochastic on 2007-10-26
All I can say is that the "upgrade" process always tends to break things in my experience.  I find that copying my /home folder into a new install and then reinstalling programs works great for keeping preferences, bookmarks, etc... without breaking things.

---

### Post by whiskyprajer on 2007-10-28
I'll give that a try and post the results. Thanks.

---

### Post by GTvulse on 2007-10-29
> **whiskyprajer said:**
> I upgraded from Feisty to Gutsy. Smooth sailing mostly, but I am no longer able to use Sound Converter to rip OGG files to MP3. When I try the progress bar at the bottom reads, "file xxxx of yyyy (333 minutes remaining)". SC gets the file folders ready, but there is no conversion happening. Is there a setting I need to change?

I tried removing/reinstalling SC, as well as all the gstreamer uglies, but still no success.

SoundConverter won't do MP3 unless you install the gstreamer lame encoder. That's in gstreamer0.10-plugins-ugly-multiverse, which you have to install explicitly.

---

### Post by Stochastic on 2007-10-29
if he was doing an upgrade wouldn't gstreamer0.10-plugins-ugly-multiverse have been upgraded along with everything?

---

### Post by Creative2 on 2007-10-29
I have made this:  

LINUX video and audio and photo and text converter ...enjoy

[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

---

### Post by GTvulse on 2007-10-29
In principle, yeah. But dist-upgrades are the weirdest things. If that plugin was tagged as an automatic install it could've been remove automagically without manual intervention.

BTW, another thing to look for is corruption of the $HOME/.gstreamer-0.10/registry.i486.xml database. It has happened to me more times I care to remember that a problem with gstreamer was solved by deleting that file. It will be automatically recreated the next time you run an application that uses gstreamer as backend.

---

### Post by mr_niceguy on 2007-10-31
> **dradul said:**
> SoundConverter won't do MP3 unless you install the gstreamer lame encoder. That's in gstreamer0.10-plugins-ugly-multiverse, which you have to install explicitly.

What he said.

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by whiskyprajer on 2007-10-31
I haven't yet bothered with a Gutsy reinstall (too lazy) but I opened a terminal and gave the "ugly multiverse" suggestion a try.  Here's the response:

```
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
The following packages were automatically installed and are no longer required:
  libxvidcore4 libdvdcss2 libmp4v2-0 libpostproc0d libavformat0d libavcodec0d
  libfaac0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I gave SoundConverter a quick try, and got the same "333 minutes remaining" message.

---

### Post by GTvulse on 2007-10-31
Then you have a problem with corrupt gconf settings, Delete ~HOME/.gconf/apps/SoundConverter logout, login and try again. BTW, the loose libraries indicate that you deinstalled gstreame0.10-plugins-ffmpeg and gstreamer0.10-plugins-bad-multiverse

---

### Post by whiskyprajer on 2007-11-06
I gave each of these suggestions a try, and turned up a variety of problems. I finally got serious about a fresh install, and that seems to have done the trick. Lesson learned: ALWAYS DO A FRESH INSTALL!!

Thanks to everyone for their patience.

---

### Post by GTvulse on 2007-11-07
Dont think twice about it. That's the beauty of fit. I've got a certifiably b0rked Debian on another partition. Debian Sid, it breaks yet toyz....

---

### Post by Ravenna on 2007-11-11
Thanks so much for that!  I just ran into the problem myself, and your tips were really helpful!

---

### Post by Billy_McBong on 2007-11-11
i have the same problem except i did a fresh install. but the suggestions here didn't solve it

anyone got any other ideas?

---

### Post by Bazirker on 2007-11-18
I also have this same problem on a fresh install and have tried all the suggestions in this thread with no luck.  Any other ideas?

---

### Post by Bazirker on 2007-11-18
Hey I think I figured it out!

I went searching through the bug reports on the Sound Converter website's product page ([http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)) and saw an option to run ```
soundconvert --debug
``` and looked at the output.  Well when I told it to convert some files for me, it spit out: ```
gobject.GError: no element "Files"
```

So I thought about this and noticed that my output path was "/home/username/Misc Files".  I tried a different output folder and it worked fine, so I think that "Files" part of the path is the trouble.  It looks like the software may not stick a "/" on the end of your output path so if you try to write to a directory that has multiple words in the title, it screws up.  The obvious fix is to ouput your files to a directory with a one-word title and copy the files where you want them to go.

---

### Post by Damiel on 2007-12-06
Thanks Bazirker, that did the trick.

---

### Post by Flyingjester on 2007-12-07
Barziker I Love you, was seriously scratching my head over this problem.

---

### Post by iKonaK on 2007-12-14
[CENTER][B][COLOR="Sienna"]had the same problem...
thanks for the solution, i use a single word folder name ..and works :)[/COLOR][/B][/CENTER]

---

### Post by twisted_steel on 2007-12-21
Thanks Bazirker.  The app is a lot happier with the modified folder name :)

---

