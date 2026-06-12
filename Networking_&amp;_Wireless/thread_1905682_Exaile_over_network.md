---
title: "Exaile over network"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by abqsteve on 2012-01-07
All,

I'm having some trouble with exaile running over the wireless network.  I'm not sure where the post the question because I don't know whether to look at ubuntu or exaile.

What I'm seeing is intermittent skipping when exaile is playing mp3s.  The mp3s it's playing are  from shares on a windows XP home SP3 box.  It's accessing them over the wireless connection.  When the skips occur, there is a often a multi-second pause and then exaile continues the song as if it had been playing all along.  For example, the song might stop at 2:30, have a 5 second pause, and then start playing at 2:35 as if nothing happened.

I've tried these things without it making any difference:
- updating everything on the linux box via aptitude
- updating everything recommended on the windows xp box via windowsupdate
- setting the priority of exaile to -15
- disabling all plugins in exaile

When I check the wireless signal strength via my conky bar graph, it's always at 50% or more.

When I run a mp3 that's on the local drive of the linux box, there is no skipping.  I'm suspecting something about the file not being sufficiently buffered while it's trying to play but I don't know how address that.

The setup is:
- exaile 0.3.2.2
- ubuntu 11.10
- Linux zippy 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

I'm accessing the windows shares using shortcuts made in nautilus.

I appreciate any help!

~Steve

---

### Post by abqsteve on 2012-01-15
Since I didn't get any response, I'm going to try a bug report on launchpad:
[https://bugs.launchpad.net/exaile/+bug/916836](https://bugs.launchpad.net/exaile/+bug/916836)

---

