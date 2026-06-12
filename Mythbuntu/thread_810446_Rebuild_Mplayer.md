---
title: "Rebuild Mplayer?"
date: 2008-05-28
forum: Mythbuntu
---

### Post by wusl.au on 2008-05-28
Hi,  I want to recompile Mplayer in my 8.04 Mythbuntu box.

What I want is to rebuild it exactly the same as it is in the installed distribution, but with one extra switch in the configuration --enable-vstream

I've tried just doing an apt-get source mplayer, compiling the vstream-client library and then doing ./configure --enable-vstream --prefix=/somewhere-harmless and I get an mplayer that will successfully play tivo streams.  Sadly, it seems to have lost support for other media types, like XviD etc.

I'm assuming that I need a certain environment and configuration to build an mplayer just like the supplied one.  If that's really the case, where do I find details?

If it's not the case, and I'm doing something dumb, can someone please put me out of my misery and point out my error.

thanks,
Wusl

---

### Post by superm1 on 2008-05-28
> **wusl.au said:**
> Hi,  I want to recompile Mplayer in my 8.04 Mythbuntu box.

What I want is to rebuild it exactly the same as it is in the installed distribution, but with one extra switch in the configuration --enable-vstream

I've tried just doing an apt-get source mplayer, compiling the vstream-client library and then doing ./configure --enable-vstream --prefix=/somewhere-harmless and I get an mplayer that will successfully play tivo streams.  Sadly, it seems to have lost support for other media types, like XviD etc.

I'm assuming that I need a certain environment and configuration to build an mplayer just like the supplied one.  If that's really the case, where do I find details?

If it's not the case, and I'm doing something dumb, can someone please put me out of my misery and point out my error.

thanks,
Wusl

Try this process:

1) 
```
apt-get source mplayer
apt-get build-dep mplayer
apt-get install devscripts fakeroot
```

2) Determine whether this library of yours is in hardy (go to launchpad.net/ubuntu).  
a>If it is, then grab it's -dev package from apt.
b>If it isn't, file a bug so it can get put into Intrepid.  
    Build your extra library

3) edit debian/rules to add in your  configuration switch in the appropriate place

4) 
```
dch -i
```
This will bump the changelog.  Make sure the version number is identical to the original, but add on a **+local1** or similar

5)
```
debuild
```

6) Install the resultant binary package(s)

7) File a bug against mplayer so this can be done in Intrepid automatically by the media teams.

---

### Post by wusl.au on 2008-06-08
Thanks for the concise instructions Superm1.  I'll give it a go soon.

Unfortunately, I was so encouraged that I decided to lash out and construct a purpose-built system for mMyth.  As a consequence, playing Tivo files is the least of my current worries.... :KS

Wusl.

---

