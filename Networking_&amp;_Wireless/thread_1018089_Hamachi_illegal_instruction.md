---
title: "Hamachi illegal instruction"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by kd5gje on 2008-12-21
I have been following through a few threads and can't find this one.  I installed Hamachi and ran the make file and made sure tuncfg was running.  I then adjusted the group settings according to KingOfNowhere's How to:

[http://ubuntuforums.org/showthread.php?t=135036]("http://ubuntuforums.org/showthread.php?t=135036")

When I try to run hamachi-init or hamachi start, I get:

Illegal instruction

Anyone have an idea about this?

---

### Post by yokazuma0 on 2008-12-24
no, because really... this forum sucks. no one will answer my hamachi questions either. and i posted it a week ago...

---

### Post by eeliottheking on 2008-12-24
> **yokazuma0 said:**
> no, because really... this forum sucks. no one will answer my hamachi questions either. and i posted it a week ago...

dude, think about how many people probably come here for help.  there is a very good chance they just missed it due to how many people need help all the time.  Giv these guys a break.  They provide a free OS and give free tech support ;)

---

### Post by fredsea on 2009-01-16
Look, I am totally NOT an expert in Ubuntu, or anything else, but I have three computers running Ubuntu (the fourth runs vanilla Debian 4.0) and they all get nicely on hamachi - after a few glitches, of course :)

Could you be more specific? What I did was

a) untar/zip the hamachi download for Linux
b) run sudo make install
c) here's the glitch: I had to download, separately, upx, and, after switching to /usr/bin, upx -d hamachi. The problem is that the file comes compressed, so it has to be freed up. so to say... I have no clue why this is not explained plainly on the hamachi site, but it is explained elsewhere around the web.
d) proceed as instructed (you know, hamachi-init, ad so on, as it says in the README file).

Quite frankly, the result is fabulous (at least, as long as the 5.x.x.x address space stays available... that's for a different thread). Since I am running a low-ball LAN accessing the Internet through a cable provider, it makes accessing the computers at home from anywhere else trivial... There are other ways, not too difficult either, but, as soon as you manage to get hamachi running, it sure is pretty simple (and cross-platform, if you are unlucky enough to have non-Linux computers)

---

