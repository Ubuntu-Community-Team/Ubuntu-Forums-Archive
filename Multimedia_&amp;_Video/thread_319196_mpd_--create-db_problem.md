---
title: "mpd --create-db problem"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by cos4 on 2006-12-15
After upgrading to v. 6.10 I wanted to recreate my mpd database but got the following error
> isildur@Hel:~$ mpd --create-db
cannot setgid for user "mpd" at line 188: Operation not permitted

Well I have no real idea how to solve this, has anyone an idea?

Thanks for reading!

---

### Post by cos4 on 2006-12-19
I tried to solve it by adding the user mpd but it didn't work. The problem only occurs when I try to start mpd as a normal user
> $ mpd
cannot setgid for user "mpd" at line 188: Operation not permitted
When I try it as root I get the following
> #mpd
No audio_output specified and unable to detect a default audio output device

So somewhere(line 188 in which file?) a script seems to try to change a gid. Anybody an idea with this info?

_EDIT:_
**Problem fixed.** The reason was that during the dist-upgrade my /etc/mpd.conf was overwritten but luckily an automatic backup was created. Know I use the old conf again and everything works well.

---

