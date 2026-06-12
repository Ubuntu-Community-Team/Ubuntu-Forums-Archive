---
title: "Very wierd video problem"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by insane_alien on 2006-09-01
When i play videos(the problem is with all players) from my harddrive each one is progressively dimmer until i finally can't see anyhting at all.

it gets completely dark after about 10 videos.

this can be fixed by restarting X but its really annoying. does anybody know what could be causing this.

---

### Post by galileon on 2006-09-01
what exactly goes dark? is it ur whole screen? or just the player? are you moving your mouse/using keyboard? could it be ur monitor trying to go into power-saving? if so, sudo gedit /etc/X11/xorg.conf, look for DPMS option in the Monitor section, comment it out...

---

### Post by insane_alien on 2006-09-01
no its just the video in the player. everything else is unaffected. the desktop stays bright.

---

### Post by galileon on 2006-09-01
so do you really need to close X and restart it? have you tried just closing the player?

maybe its something with the codec? is it some proprietary format? if so maybe your codec is corrupted? is this problem from a fresh install, or did it come up at some point?

---

### Post by insane_alien on 2006-09-02
i've tried just closing the player and that doesn't solve the problem.

i had only installed the base and updates when i spotted this problem and is over all codecs. be it open source or propriety.

---

### Post by insane_alien on 2006-09-03
yeah this is still annoying me

---

### Post by galileon on 2006-09-04
ooookkk,,,sorry i didint reply before, my internet is down at the mo, im squatting a cyber...

have you tried ps -A in a terminal? it will give you a list of running processes, that might tell us if any part of the player is still running when you close it - eg backends etc.

if you see anything that shud have died when the player was closed, type killall <name_that_you_see>, replacing the name by the name given by ps -A.

---

### Post by insane_alien on 2006-09-04
hmm, everything it opens closes as expected.

---

### Post by galileon on 2006-09-04
just wondering is that in dapper or edgy? just noticed you were testing edgy...

---

### Post by insane_alien on 2006-09-05
dapper. i have a seperate partition for edgy. i'm not moving to edgy till its officially released. but i have a copy to see how its coming along.

EDIT: your post inspired me to try it out on edgy. i mounted my videos folder into edgy and the videos didn't gradually fade to black! still happens in dapper though. edgy is pretty stable just now especially for just web browsing. i might switch to edgy with a dapper 'just in case' partition. the final comes out in october so it should be getting alot better.

---

