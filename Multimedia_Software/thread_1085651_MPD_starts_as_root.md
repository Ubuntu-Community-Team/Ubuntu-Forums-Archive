---
title: "MPD starts as root"
date: 2009-03-03
forum: Multimedia Software
---

### Post by gldtn on 2009-03-03
Hello,

 I'm having a small problem while starting MPD under session.. Where it starts as root instead of the user(me), not allowing my music database to be read. So I have to kill MPD with 'sudo killall mpd' and run MPD again as user to be able to get my music Database.

Any idea as why this is happening? I was told that under Session, MPD should've started as the user not as root.

Thanks in advance!

---

### Post by and.be.like on 2011-12-18
[QUOTE="gldtn"]         Hello,

 I'm having a small problem while starting MPD under session.. Where it  starts as root instead of the user(me), not allowing my music database  to be read. So I have to kill MPD with 'sudo killall mpd' and run MPD  again as user to be able to get my music Database.

Any idea as why this is happening? I was told that under Session, MPD should've started as the user not as root.

Thanks in advance!     [/QUOTE]Old post, but I had the same issue too, so a reply is needed.

Open /etc/default/mpd as root with
> gksudo gedit /etc/default/mpd(or whatever editor you like/use) and edit the option START_MPD to
> START_MPD=falseThat's it.

---

