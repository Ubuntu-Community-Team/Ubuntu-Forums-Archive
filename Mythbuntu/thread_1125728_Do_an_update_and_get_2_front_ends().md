---
title: "Do an update and get 2 front ends(?)"
date: 2009-04-14
forum: Mythbuntu
---

### Post by johnelle on 2009-04-14
I had a Mythbuntu system that worked fine for 6-7 months.  Then I did an update (which I tend to do weekly or so) and when I returned to the system this AM it had 3 front ends, 3 terminals and the 2nd disk (where I store transcoded files) had some weird link that made the directory structure recursive.  

After work I just did a clean 8.10 install and everything appeared to be working fine so I did an update and guess what...two front ends, two terminals running.  Its an instant mess.

Is there some simple way to prevent this?  I really don't want to run an unpatched system--thats why I moved off of MythDora.

I kinda know my way around the system but I have no idea what fires up the front and back end and which one of the 100+ updates made it go South.

Is there some way to get a fully updated system with one back and one front (i.e. normal)?

(I tried 9 and it won't even run the Myth setup on this hardware)

---

### Post by nickrout on 2009-04-14
You are not alone by the looks of it:

[http://ubuntuforums.org/showthread.php?t=1122956](http://ubuntuforums.org/showthread.php?t=1122956)

mythbackend is a service started by /etc/init.d/mythtv-backend

mythfrontend is started when you log in to X via gdm. I would look at /etc/mythtv/session-settings. Not having a machine in front of me I can't look through the scripts right now.

Try also looking at /usr/bin/mythfrontend which is a wrapper script that starts mythfrontend.real.

---

### Post by johnelle on 2009-04-17
Thanks but nothing obvious in the scripts.  Not sure where to look next.

---

