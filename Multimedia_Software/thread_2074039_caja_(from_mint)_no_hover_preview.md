---
title: "caja (from mint) no hover preview"
date: 2012-10-20
forum: Multimedia Software
---

### Post by a z on 2012-10-20
howdy all, great job on 12.10!

on my laptop, caja does the mouse-hover-preview-mp3 thing beautifully. on my wife's dell inspiron 4010 laptop, not so much. the icon looks right when you hover, just no sound. i can open the same file in audacious or whatever, and it plays fine there. no other sound issues. 

i should also mention, both our laptops are lubuntu 12.10 (fresh,too).

checked alsamixer - nothing muted.

had my laptop sitting side-by-side with hers and (in synaptic) search/compared things like mpg, mp3, lame, gstreamer, etc, to install anything i might've missed on her machine. made everything identical...
???
any thoughts?

---

### Post by a z on 2012-10-21
c'mon, anybody?

caja is (if you didn't know) a forked ver of nautilus 2.something, from the linux mint repo. the new nautilus doesn't do the hover-preview thing(anymore), which if you have a lot of music files (hello ubuntustudio folks), is super cool when wading through them. you don't have to open each one in a player, just hover over it for a second. 

this is one of the coolest things ever, and snared me back in hardy 8.04.

like i said, my wife and i have Lubuntu 12.10 on laptops - it works on my little hp mini-1010, but not on her dell inspiron N4010.

inquiring minds...

---

### Post by a z on 2012-10-23
wow, nobody...

well, the mate-desktop forum had the answer:

gstreamer0.10-tools

installed that, boom. done. mp3-hover-preview works. awesome if you have to wade thru tons of music files (a hell of a lot faster than gnome-sushi!)

a z

---

