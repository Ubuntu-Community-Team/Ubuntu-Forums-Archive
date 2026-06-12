---
title: "Normal boot, xserver error, then promted to login...a little help please"
date: 2006-10-15
forum: Multimedia &amp; Video
---

### Post by imaiden22 on 2006-10-15
Hey everyone, this is not the most dire of problems, but it'd help me understand how the xserver and gdm work together a little better.

Basically everything between my xserver and gdm config was working fine, until I tried installing xgl + compiz a few times, not succeeding once. Every time I was trying something new and I continually screwed up my xorg.conf and even my gdm.conf on a few occassions. 

Long story short, I've given up on xgl + compiz and just want things to proceed normally.

So when I boot everything loads fine and then I'm prompted to login, then after about 10 seconds I get a blue screen telling my that my xserver failed and it asks if i'd like to see the output or not, then after i choose, it goes back to the login and I have a fully working desktop upon successfully logging in.

Here's the output when I choose to see it before logging in:

GDM: Xserver not found: /usr/local/bin/Xgl :1 :0 -fullscreen -ac -accel xv -accel glx: pbuffer -auth /var/lib/gdm/:1.Xauth vt8
Error: Command could not be executed!
Please install the xserver or correct GDM configuration and restart gdm.


it doesn't really affect my system to my knowledge, but a) i'd like to understand how these things work a bit more, and b) i'd like to get rid of a small annoyance.

---

### Post by Dr. Nick on 2006-10-15
Im not on ubuntu now so this may be vague, someone may be a bit more specific

I would look at the guides that you used and work in reverse, I think thier is a gdm.conf file  or something that you can edit what all sessions are avaible, The message above looks like you removed xgl but gdm is trying to load it. In one of the xgl guides it probably tells you to add some text to a config file, eitheir deleting the text or restoring a backup should work

---

### Post by imaiden22 on 2006-10-15
yeah im begining to think its a gdm.conf problem because i ran sudo dpkg-reconfigure xserver-xorg and did that 3 times, trying different drivers each time (vesa, vga, and nv) and all three times i had the same situation at startup. thanks but if someone could tell me what to look for in my gdm.conf that'd help even more, because gdm.conf is a bit more complex than xorg.conf, thanks a lot for the advice though!

oh and on the backup issue, i have so many backups in my X11 folder i wouldn't know where to start, haha, but i'll check some of the guides that mention gdm.

---

