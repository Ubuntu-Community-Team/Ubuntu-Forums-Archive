---
title: "Ubuntu 8.04 RC1 Audio problems"
date: 2008-04-22
forum: Multimedia Software
---

### Post by koosoli on 2008-04-22
Hello,

I have a strange problem.
When I boot ubuntu and i start Rhithmbox the audo work, but if I then
start firefox and a youtube video, the youtube video will play without
audio.

When I then log out of ubuntu and back in, and then start a youtube
video, the audio works, but if I then try Rhithmbox, Rhithmbox will
not be able to play any audio.

I thought the problem might have to do with firefox so I installed the
Epiphany Browser, and guess what, the sound didn t worked at all on
Rhithmbox, even after a reboot without starting Epiphany, so I deleted
Epiphany and I am back to the first problem.

Has anyone the same problem?
My workaround is, logout and back in ubuntu to use firefox or
rhithmbox with audio.

Hope this problem will not be in the finished ubtunu 8.04

Oli

---

### Post by koosoli on 2008-04-22
Oh, and one more thing;

I got my music on a ntfs 3.1 partition.
Is it normal that ubuntu 8.04 is not mounting this partition on start-up and that I have to do it every time myself? This was not the case on ubuntu 7.10.

---

### Post by jaymz168 on 2008-04-22
Hello, having some problems with sound here.  I had sound working in flash (in Firefox and Opera beta) under Hardy beta just fine, but then I just *had* to run the upgrade to RC1.  Now it's gone again.  This was the only thing keeping me from switching from windows because I like to take music lessons on youtube.

Sound works in all other programs, it's just the flashplugin that broke with the upgrade.

---

### Post by RgnKjnVA on 2008-04-22
I have this problem in Gutsy

---

### Post by koosoli on 2008-04-22
We should hand in a bug-report, but I have no clue how that works :(

---

### Post by thebestofall007 on 2008-04-28
> **koosoli said:**
> Hello,

I have a strange problem.
When I boot ubuntu and i start Rhithmbox the audo work, but if I then
start firefox and a youtube video, the youtube video will play without
audio.

When I then log out of ubuntu and back in, and then start a youtube
video, the audio works, but if I then try Rhithmbox, Rhithmbox will
not be able to play any audio.

I thought the problem might have to do with firefox so I installed the
Epiphany Browser, and guess what, the sound didn t worked at all on
Rhithmbox, even after a reboot without starting Epiphany, so I deleted
Epiphany and I am back to the first problem.

Has anyone the same problem?
My workaround is, logout and back in ubuntu to use firefox or
rhithmbox with audio.

Hope this problem will not be in the finished ubtunu 8.04

Oli

i had this problem too when i upgraded to hardy. heres the fix: 
open up a terminal and type:

sudo apt-get install libflashsupport

(or search for "libflashsupport" in the synaptics package manager, right click on the package and choose "mark for installation", then click "apply")



then restart.
that fixed it for me. ;)

---

### Post by amanjain on 2009-03-07
Installing libflashsupport did the job for me too.
But I want to know why was did this problem(at any given time either firefox **OR** other applications got sound working, but not both) exist before installing libflashsupport.

Thanks
Aman Jain

---

