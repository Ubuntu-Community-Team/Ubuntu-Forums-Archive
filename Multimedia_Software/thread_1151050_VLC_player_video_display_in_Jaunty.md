---
title: "VLC player video display in Jaunty"
date: 2009-05-06
forum: Multimedia Software
---

### Post by Daerun on 2009-05-06
This is not a real problem but it is really annoying: every time I play a video in VLC, video itself opens in a separate window instance; I've checked the "integrate video in interface" at Tools > Preferences > Interface, but doesn't work. Is there a way to make VLC to work like in previous versions?

---

### Post by andrew.46 on 2009-05-06
Hi Daerun,

> **Daerun said:**
> This is not a real problem but it is really annoying: every time I play a video in VLC, video itself opens in a separate window instance; I've checked the "integrate video in interface" at Tools > Preferences > Interface, but doesn't work. Is there a way to make VLC to work like in previous versions?

Unfortunately this is a *feature* of this particular version of vlc. I believe that version 1.0, when it is released, will have the old behaviour.

Andrew

---

### Post by rainwalker on 2009-05-06
It's not a "feature" as andrew.46 said, it's a bug. The embedded video feature is broken in Jaunty for VLC versions <1.0
See here: [http://ubuntuforums.org/showthread.php?t=1111272](http://ubuntuforums.org/showthread.php?t=1111272)

---

### Post by Zunino on 2009-05-06
Indeed a very annoying problem. Try adding many short clips to the playlist and watching them. You might get a little dizzy trying to track the video window.

Rainwalker, if you look a little closer, you'll notice that Andrew did try to emphasize the word *feature* on his post. :)

Cheers!

---

### Post by rainwalker on 2009-05-06
> **Zunino said:**
> Indeed a very annoying problem. Try adding many short clips to the playlist and watching them. You might get a little dizzy trying to track the video window.

Rainwalker, if you look a little closer, you'll notice that Andrew did try to emphasize the word *feature* on his post. :)

Cheers!

Ah, indeed, my bad :P
Still, I don't see why an updated version was included in the repositories if it was broken like that.

---

### Post by andrew.46 on 2009-05-06
Hi Zunino,

> **Zunino said:**
> Rainwalker, if you look a little closer, you'll notice that Andrew did try to emphasize the word *feature* on his post. :)

Irony comes across very poorly in a forum post :-).

Andrew

---

### Post by mc4man on 2009-05-06
The 'embedded video' has been considered broken for some time, basically since 0.9.x was released. It was disabled in the source around 0.9.3 and has been ever since then for all 0.9.x sources (only 1 line changed

The issue was it could create a race condition in some combo's of usage, hardware and distro.

For the most part debian/ubuntu users seemed to not be affected so in intrepid the embedded was restored in the 0.9.4 and remains so .  (unfortunately intrepid choose one of the worst 0.9.x versions and doesn't seem inclined to update to 0.9.9a which is half decent

For whatever reason in jaunty the decision was made not to enable the 'embedded'.

The 'issue' was resolved in the 1.0 sources so there is embedded by default.


You are free to upgrade your vlc  to  an embedded enabled whether using hardy, intrepid, or jaunty to 0.9.9a or a 1.0 rev. either by building and editing the source or using a ppa that offers an enabled build (some do, some don't, many posts linking those that do

Most people using ubuntu seem to not have an issue with the embedded  enabled


In a way or another all 0.9.x and 1.0 revisions are broken or have regressions, whether it affects one depends on what version your using and your individual usage.


for instance
for jaunty a 0.9.9a
[https://edge.launchpad.net/~medigeek/+archive/ppa](https://edge.launchpad.net/~medigeek/+archive/ppa)
a 1.0 pre for jaunty
[https://edge.launchpad.net/~kow/+archive/ppa](https://edge.launchpad.net/~kow/+archive/ppa)

a 0.9.9a for intrepid
[https://edge.launchpad.net/~mlind/+archive/ppa](https://edge.launchpad.net/~mlind/+archive/ppa)

And a 0.9.9a for hardy (ck.ing his diff'ed source it appears it's patched
[https://edge.launchpad.net/~c-korn/+archive/vlc](https://edge.launchpad.net/~c-korn/+archive/vlc)

---

### Post by rainwalker on 2009-05-06
I installed the 1.0 version from Kow's ppa to remedy this, and everything works perfectly for me :)

---

### Post by Daerun on 2009-05-07
Thanks for the replies, I've also installed the KOW 1.0 version, and works fine :D

---

