---
title: "gnormalize converts m4a to mp3 but cant normalize volume"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by sdowney717 on 2007-07-07
I installed a lot of what it needed including normalize which is run using 'normalize-audio' in terminal. I only had to use synaptic for all the missing codecs etc....

[http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/)
is the website for gnormalize. 

the program error is 'Can't find "normalize" in executable path. The wav files can't be normalized.'

What I assume is gnormalize is looking for 'normalize' when what is available in the system path is 'normalize-audio'

---

### Post by Theimon on 2007-07-11
Gnormalize looks for normalize ( [http://normalize.nongnu.org/](http://normalize.nongnu.org/) ) which isn't the same as normalize-audio. Download links at the mentioned site are dead though.....not surprising since there hasn't been development since 2005...
Maybe you can normalize your audio through mp3gain or similar.

---

### Post by sdowney717 on 2007-07-11
from the gnormalize site says you can apt-get, which apparently I already have. 
I like the program have you tried it?
Is there another one like gnormalize?

root@scott-desktop:~# apt-get install normalize-audio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
normalize-audio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
root@scott-desktop:~#

---

### Post by Theimon on 2007-07-11
I use it myself for converting audio to mp3. I don't use the normalize function though. 
I know the site says you can apt-get for normalize but I think the info is outdated. The website hasn't been updated for a while (nov. 2006) and the current version has been the same for quite some time now.
I don't know if the developer is still working on gnormalize but I have a strong feeling he stopped a while ago. Anyway, it's a great program but like I said, maybe you can take a look at mp3gain for volume normalizing.
I'm not aware of any alternative to gnormalize itself (other then playing around on the command line...)

---

