---
title: "cinelerra freezes but runs under root"
date: 2008-04-20
forum: Multimedia Production
---

### Post by alsehendo34 on 2008-04-20
when I run cinelerra as a regular user it freezes after load but runs fine under root.  Weird thin is you can scroll through tips but nothing else you can't even close the application with the x in the corner.

Everything works fine starting it in terminal as root user!

I tried changing /usr/bin/cinelerra  executable to meuser megroup and permissions 777 and it still freezes.

Note:
Installed in hardy via their instructions 

sudo wget [http://repository.akirad.net/dists/hardy.list](http://repository.akirad.net/dists/hardy.list) -O /etc/apt/sources.list.d/akirad.list
wget -q [http://repository.akirad.net/dists/akirad.key](http://repository.akirad.net/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update

Now you can install:
cinelerra (x86 and x86_64 without opengl 2.0 video card)*

Also did this as sugested
If cinelerra crashes after first install type on terminal:
chown -R YOURUSER:YOURGROUP ~/.bcast 
did not help.

Anyone else having this problem?

---

### Post by cotcot on 2008-04-20
I do not know your problem.
Maybe you could compile cinelerra yourself. It is not so difficult. In post 12 of [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=666911&page=2")  thread I have explained how I did it. You can use it for hardy as well, however the revision number of the package dependencies could be different.
The ./configure command gives a very good output about the dependencies. If you do not get a dependency OK check if you have installed the -dev package of the dependency as well.

Further I recommend to install Cinelerra with OpenGL. It is faster in rendering and preview in the compositor. (the compositor renders while you play it)

---

### Post by KoenW on 2008-04-28
A little dirty tweak I found: disable GDM. See [http://ubuntuforums.org/showthread.php?p=4825111#post4825111]("http://ubuntuforums.org/showthread.php?p=4825111#post4825111") for more.

Koen W.

---

### Post by dierre on 2008-04-29
> **alsehendo34 said:**
> 
Anyone else having this problem?

I have *exactly* the same problem as you.

---

### Post by MetalMusicAddict on 2008-04-29
This is only a work around and not a fix. Cinelerra works as normal here on Hardy. I wouldn't have filed that bug on Cinelerra's tracker either. Was really premature considering you don't know the real cause.

---

### Post by tagawa on 2008-04-30
I'm having the same no-response problem as well after upgrading Xubuntu from Gutsy to Hardy.  Cinelerra was re-installed from the akirad repos and both cinelerra and cinelerra-generic are the same.  I found this comment which may be relevant:

[http://kevb.net/lurker/message/20080319.194750.d538410d.en.html](http://kevb.net/lurker/message/20080319.194750.d538410d.en.html)

I'm at work so can't compile from source now but it looks as though the result would be the same.  Will keep looking...

---

