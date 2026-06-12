---
title: "How to play .mov (quicktime) files ?"
date: 2008-06-07
forum: Multimedia Software
---

### Post by ahmed_nasr on 2008-06-07
Hi ,

I am using ubuntu 7.04 and i wanna play .mov (quicktime) files

I installed VLC player but it doesnt play them 

so any help ?

---

### Post by Pjotr123 on 2008-06-07
Better change to 8.04 (do a clean installation, not an upgrade).

However, this should also work in 7.04:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

and afterwards do this:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by ahmed_nasr on 2008-06-07
done all that 

then i try to play it using VLC i get sound only no video

i try mplayer movie player i get this error message :

[IMG]http://b.imagehost.org/0753/Screenshot-Fatal_error.png[/IMG]

---

### Post by ahmed_nasr on 2008-06-07
i forgot to add when i search for "openjdk" in synaptic manager ,

i find no packages

does this have to do with anything ?

---

### Post by Pjotr123 on 2008-06-07
No, that's specific for 8.04. Has nothing to do with the problem.

Still my advice is: consider a clean installation of 8.04 and then follow the how-to I gave you.

---

### Post by ahmed_nasr on 2008-06-08
ok thanks dude

but i need to play mov files on 7.04

can anybody help me with that plz ?

---

### Post by mastermindg on 2008-06-08
MPlayer has support for Quicktime movies.

In Hardy the codecs are available stock or through w32codecs. If not, you can always install them manually via the binary package at:

[Link]("http://www.mplayerhq.hu/homepage/design7/dload.html")

---

### Post by ahmed_nasr on 2008-06-08
doesnt work too bro ... i feel so mad right now

---

### Post by dje on 2008-06-08
In mplayer right click and select preferences and then go to the video tab and select x11 for the driver, close mplayer and reopen with your .mov file

hope that helps,
dje

---

### Post by ahmed_nasr on 2008-06-08
> **dje said:**
> In mplayer right click and select preferences and then go to the video tab and select x11 for the driver, close mplayer and reopen with your .mov file

hope that helps,
dje

dje I love you man ... I have been banging my head across the wall and you saved me 

that really worked i cant believe it :guitar::guitar:

thanks brother

I just have one more request ... i would like to understand what this x11 had to do with getting the file played

thanks again bro

---

### Post by dje on 2008-06-08
No problem :KS

x11 is the driver needed to get any video to play in mplayer, not just .mov

dje

---

### Post by cariboo on 2008-06-08
X11 is the graphics layer of Linux. It has nothing to do with playing media.

Check out this link. 

[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

Jim

---

### Post by dje on 2008-06-08
> **cariboo907 said:**
> X11 is the graphics layer of Linux. It has nothing to do with playing media.

Check out this link. 

[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

Jim

thats what i meant, arent you choosing which graphics layer (or driver?) you are using to play the video?

dje

---

