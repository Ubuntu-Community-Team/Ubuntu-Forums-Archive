---
title: "Mythfrontend auto-restart in case of crash. How?"
date: 2008-01-09
forum: Mythbuntu
---

### Post by Nikas on 2008-01-09
I usually don't get any answer to my posts here but i will give it a try once again. ;)

How can i make mythfrontend to autostart in case of a frontend crash?

Thank you!

/Niklas

---

### Post by psybert on 2008-01-09
I'm not how sure it can be done via software, and I take it that would need to depend on what type of crash. 

I know this isn't the answer you're looking for, but you can use a UPS with a watchdog type software to perform an auto-restart on system lockups. I use that kind of setup for some of my remotely networked machines.

---

### Post by Nikas on 2008-01-09
On my backend i use this script in a cron-job every min:
[http://www.thornsoft.com/Misc/babysit_backend.sh](http://www.thornsoft.com/Misc/babysit_backend.sh)

Something like that maybe?
I have modified that script and it works but i dont know wich command to use to make the fronend start on the right screen.. eh. I'm a linux noob.
I can call the modified script from the terminal (if i run the terminal directly from the desktop) and that works.

I've activated mythwelcome now so from there i can start a crashed frontend with the remote.

---

### Post by djkmyth on 2008-01-12
You might be interested in a solution like is outlined over at mythtv.org to keep a backend up.  You could simplify the script to control your frontend...

[http://www.mythtv.org/wiki/index.php/Using_pcsk_to_Supervise_mythbackend](http://www.mythtv.org/wiki/index.php/Using_pcsk_to_Supervise_mythbackend)

---

