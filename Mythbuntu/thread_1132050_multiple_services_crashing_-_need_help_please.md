---
title: "multiple services crashing - need help please"
date: 2009-04-21
forum: Mythbuntu
---

### Post by tkleen on 2009-04-21
Hi all, 

I'm running a mythbuntu 8.10 box that i've had live for about a month now. I left town for a few days and when I returned two days ago I've come back to major problems. This is way beyond my knowledge and could definitely use some help.

Every time I boot the machine and it has been running for about ten minutes, an event of some kind happens that causes many services to crash at once. For example: 

- I run samba, and the samba server is no longer accessible from my Windows machine. This is sporadic, however.

- Myth backend crashes, and the tuner no longer works. I get an error message in myth frontend that says "Could not connect to the master backend server -- is it running? Is the IP address set for it in the setup program correct?" However, if samba has not crashed I can still watch videos through myth frontend.

-rtorrent also crashes depending on if samba crashes.

-Many of the basic commands on the terminal stop working and I get Input/output errors as in:

          ted@mythserver:~$ sudo shutdown -r now
          -bash: /usr/bin/sudo: Input/output error

This is true for many basic commands(cat, sudo su, etc.), but not all (ls, for example, will still work)

However ssh is rock solid, so I'm able to log in remotely but once I'm in I can't do much.

Any ideas? My best guess is that it's a corrupted hard drive, but it is purely a guess...

I would really appreciate ideas on logs to post and where i can find them in the file structure.

Thank you.

Ted

---

### Post by SiHa on 2009-04-21
Sounds like flaky memory. Try booting from a LiveCD and running Memtest. Although beware, I think Memtest on the 8.04 disks didn't work.
Or, if you have more than one stick of RAM try swapping them out to isolate the dodgy one. Could be just a bad contact and removing and reseating will be enough to fix it.
One other thought, it happens after about 10 mins, so it could be heat-related. Is your processor fan working?
Mine died at the weekend, and I came home to fine the machine power-cycling - not nice. Seems to have survived though.

---

### Post by nickrout on 2009-04-22
hard drive full?

---

