---
title: "New Mythbuntu 16.04 install, many issues"
date: 2017-01-15
forum: Multimedia Software
---

### Post by jabeez2 on 2017-01-15
Hi all, about losing my mind here, have spent hours trying to get a fresh install after getting new PC for my backend. First I tried to use KDE-Neon, installed MythTV packages, wrestled with getting old database restored, and after getting it restored and mostly working, I couldn't get live TV working in Kodi (got "Channel Unavailable" on every channel), even though it was connected to the backend and could view recorded programs and even schedule new ones. So I fought with that for hours and hours, eventually leading to backend not being able to start at all.

So, I finally surrendered and decided to just install the latest Mythbuntu, which is what I was running on old backend. It went well for the most part, got my database restored fairly easily, but unfortunately ran into same issues as before: no LiveTV in Kodi, no remote frontends able to connect, and mythweb not working either. I searched and searched, and found some possible fixes, which I tried, after making backups of any edited files, and am back to the backend not starting at all, and now mysql not starting. These are the things I tried, and have since restored them to their original state, yet system is completely hosed still, which makes zero sense to me:


/etc/mythtv/config.xml had "localhost" in host field, I tried changing it to the ip of the backend machine, and have since changed it back to local host, as after changing this the backend immediately wouldn't start, and even after changing it back, still wouldn't start?????
/
Found suggestion on myth wiki that I needed to add my ip to the bind address in /etc/mysql/my.conf and/or mythtv.conf, which I tried one at a time to no success, and have since changed both back to original, but now mysql won't even start, getting error = Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl -xe" for details.


Unbelievable, I'm at wits end here, I'm not exactly a linux newb, but this stuff is just making absolutely no sense to me. How can it break by changing config files and then changing them right back?????? HELP!!!

---

### Post by mörgæs on 2017-01-16
Hi, welcome to the fora.

Let's begin with the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by deadflowr on 2017-01-16
Your original main problem sounds a lot like the known issue of systemd causing your backend to start too early, before the tuners get a chance to initialize.
(Or that's a base idea I've seen here and there)
Perhaps read through this:
[https://www.mythtv.org/wiki/Systemd_mythbackend_Configuration]("https://www.mythtv.org/wiki/Systemd_mythbackend_Configuration")

The mysql issue is most likely the outcome of going down a bad rabbit hole...

---

### Post by jabeez2 on 2017-01-16
Thank you both for the replies, finally got it working last night, in Kodi as well! Wish I could tell you how, I actually had to fix it twice as I had it all working, except for Mythweb, saw there were a bunch of updates (and reading about bug that updates supposedly fixed), so after hesitating for a bit, installed the updates, and it broke again!!! Messed with it for another hour or two and finally got it back up and running, all seems fine now except for Mythweb still, which is really strange, getting "[COLOR=#000000][FONT=&quot]Access denied for user 'mythtv'@'192.168.1.5' (using password: YES)" error, just like I was before when having issues with backend not starting. Ugh, just have to keep digging I guess, but down a bad rabbit hole indeed!!![/FONT][/COLOR]

---

### Post by jabeez2 on 2017-01-17
Wow, so was trying to get Mythweb working, couldn't get it working but backend/frontend/Kodi were all working fine, and then saw there were more updates, and like a moron, decided to try them since Mythweb was one of the updates. Lo and behold, it broke everything again!!! Something very strange though, can't start the backend (Mythbackend settings/Mythfrontend both go to select Country/Language, so not connecting to database), but go into Kodi, and it connects to backend, I watched some live TV, saw recordings, etc.!?!?!? I'm just about done with 16.04, thinking I might just go back to 14.04, but before I do, any thoughts on a last ditch effort/things to try or look at? Thanks!

---

