---
title: "Mythmusic+projectM"
date: 2009-04-12
forum: Mythbuntu
---

### Post by teetniin on 2009-04-12
Hello

 I've been trying to get projectM work with mythmusic, but instead i get error and it exits mythfrontend:

dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
configFile: /home/t33t/.projectM/config.inp
MAX SAMPLES:2048
Floating point exception

I'm using 64bit mythbuntu(9.04 beta)
projectM 1.0.1

Tried earlier with 8.10, same problem.

Also a year ago tried on gentoo, same problem!

It is not mythbuntu problem, but maybe anyone has workaround for that problem?

T.I.A.

---

### Post by Billsputters on 2009-04-12
This looks interesting. 

There's a Wiki at [[COLOR="Red"]here[/COLOR]]("http://www.mythtv.org/wiki/ProjectM") that might be of use.

Might have a go at this if I can get the everything else all going.

---

### Post by azmyth on 2009-04-12
I saw your post and gave it a whirl since it looks like it would be neat to have. I installed the projectm packages from the repo. I got the same exact error as you 8.10 AMD 64. I did some searching and there was a bug on bugtrack and someone said the found a fix that required modifying the source code and then compiling. Too bad they didn't provide the edit.

---

### Post by am88b on 2009-05-03
This patch fixed the problem for me: [http://svn.mythtv.org/trac/ticket/5438](http://svn.mythtv.org/trac/ticket/5438)

Apparently, this patch have been in trunk version of MythTV for months but never got into 0.21, so you probably need to recompile from source (at least for now).

---

### Post by NateMan on 2009-05-10
I too have been trying to get mythtv and projectM to play nice together, however I am using projectM 2.0 compiled from their svn. I was looking at the patch and trying to figure out were to add it, but can't seem to find the mythmusic folder where it can be patched. Does this mean that the mythmusic plugin needs to be recompiled from source or does all of mythtv? I would love a little guide perhaps on how you were able to get your patch to work. ProjectM would add a great function to my mythtv and any help would be greatly appreciated. Thank you in advance.

---

