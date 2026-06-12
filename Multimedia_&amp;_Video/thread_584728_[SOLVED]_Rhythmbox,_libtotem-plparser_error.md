---
title: "[SOLVED] Rhythmbox, libtotem-plparser error"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by mts-fi on 2007-10-21
Switching to gutsy killed my Rhythmbox

When starting Rhythmbox in terminal I get this message:
rhythmbox: error while loading shared libraries: libtotem-plparser.so.1: cannot open shared object file: No such file or directory

I have reinstalled both rythmbox and totem, neither helped.

Any suggestions?

---

### Post by mroven on 2007-10-23
I am having the same problem.  Looking for the answer now, Ill let you know what I find...

---

### Post by mts-fi on 2007-10-23
I've done some researsh... haven't found anything.

Done some testing too... I can start Rhythmbox from Applications-Debian-Programs-Sound, but NOT from Applications-Soud & Video or terminal (hope I got those right, I'm usin Finnish Ubuntu).

I can't fix it but I hope this helps you to find the answer... and please, do let me know if you find one.

---

### Post by mroven on 2007-10-23
I found an older version of rhythmbox installed in my PATH.  Run the following in a terminal window:

$ which rhythmbox

I got back "/user/local/bin/rhythmbox"

Then I ran:

$ sudo rm /usr/local/bin/rhythmbox*

Note: The "*" gets rid of both rhythmbox and rhythmbox-client

I had previously un-installed rhythmbox using Synaptic, so I had to reinstall it at this point.  But, that should do the trick.  Hope this helps.

---

### Post by oniichan on 2007-11-03
I had the same problem. Removed rhythmbox complety with thee package manager and then deleted every rhythmbox directory in my user account. After re-installation, Rhythmbox worked fine. I'm sure you could even find the setting in the user xml config files it uses, but this seemed an easier route for me.

---

### Post by mts-fi on 2007-11-05
Thank you oniichan that worked for me too.

---

