---
title: "DVD works in windows, but not in ubuntu"
date: 2012-11-03
forum: Multimedia Software
---

### Post by motoperpetuo on 2012-11-03
i have a DVD that works in windows 7 (in windows media player), but not in ubuntu. when i try to play it in vlc, nothing happens. totem doesn't see the DVD at all.

i thought i would try copying to see if the copy would work better, and brasero sees the DVD, but i'm not able to actually select the DVD to start the copy project. the DVD title appears in the "select disc to copy" drop down menu, but when i select it, the field just stays blank.

i can browse the files on the disc in nautilus or in bash normally.

i would greatly appreciate any ideas anyone has for troubleshooting this. thanks!

---

### Post by ibjsb4 on 2012-11-03
Got libdvdcss?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And if brasero still gives you trouble you may want to try something else.

I prefer k3b;  simple and just works.

---

### Post by ajgreeny on 2012-11-03
Do other DVDs play OK or is this the situation with all commercially released DVDs?

It sounds as if you need libdvdcss2 installed.  For details see [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) especially the DVD section.

---

### Post by motoperpetuo on 2012-11-03
sorry, i should have mentioned that i do have libdvdcss2 installed, and that other commercial DVDs work fine in ubuntu. it's just this one that doesn't seem to like ubuntu, for some reason.

i'll give k3b a shot.

---

### Post by ibjsb4 on 2012-11-03
Once in the past I found a player that did that.  It depended on a windows driver that did not have a linux equivalent.

What kind of player is this?

---

### Post by motoperpetuo on 2012-11-04
> **ibjsb4 said:**
> Once in the past I found a player that did that.  It depended on a windows driver that did not have a linux equivalent.

What kind of player is this?

hmm...i'm not even sure how to tell what the make and model of my optical drive is (i think that's what you meant). although, any other DVD plays fine on it, just not this particular DVD (it's the "P90X 1 on 1 Yoga: MC2" DVD, from beachbody, the company that makes P90X, for what it's worth).

k3b was a good suggestion. i was able to burn a copy with k3b, however the copy still doesn't work under ubuntu, only under windows 7.

actually, i just tried the copy again, and it started playing in VLC, for just a few seconds, first time that's ever happened. then my computer froze up for a few seconds and VLC crashed with an "unexpected error."

i appreciate the help of everyone who has replied to this. please let me know if any of you have ever seen a problem like this before, or if you have any idea how i might get this DVD to play under ubuntu.

---

