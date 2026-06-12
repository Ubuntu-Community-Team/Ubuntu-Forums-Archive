---
title: "new problem: MPD won't connect (was doing fine just a few days ago)"
date: 2008-12-12
forum: Multimedia Software
---

### Post by mailbox on 2008-12-12
GMPC is giving me the following error: *"error code 13: problems connecting to "localhost" on port 6600: connection refused"*
When I try to restart MPD (*sudo /etc/init.d/mpd restart* or even *sudo /etc/init.d/mpd stop* all it says is *" * Stopping Music Player Daemon mpd        [fail]"*

MPD was working fine just a few days ago, but then my PSU bit the dust and I had to get a new one. Any idea what's going on here?

---

### Post by mailbox on 2008-12-12
SOLVED, disregard.
All I had to do was to remove */var/lib/mpd/state* and *~/.mpd/state*

---

### Post by mailbox on 2008-12-14
Actually, this is now unsolved again.
The above solution worked once and only once, now I am unable to start or stop MPD at all. I'm getting the same error as before.


Another problem:
eog, archive manager and gedit (and a few others which I have currently forgotten) take about 5 minutes to load. Every time I try to open an image, it takes a ridiculously long time to open. Furthermore, I am unable to uninstall eog through Add/Remove because it depends on ubuntu-desktop, something I'd rather not touch.

---

### Post by bobdobbs on 2009-10-05
I'm getting the same error.

To recover I stop and then start the mpd daemon. Then it works for a random short amount of time, but with no sound output.

A reboot takes the issue away for a few hours.

Anybody know what is going on here ?

---

### Post by Endolith on 2009-10-10
> **mailbox said:**
> GMPC is giving me the following error: *"error code 13: problems connecting to "localhost" on port 6600: connection refused"*
When I try to restart MPD (*sudo /etc/init.d/mpd restart* or even *sudo /etc/init.d/mpd stop* all it says is *" * Stopping Music Player Daemon mpd        [fail]"*

MPD was working fine just a few days ago, but then my PSU bit the dust and I had to get a new one. Any idea what's going on here?

I get error 13, too, from a remote computer.  From the local computer, it seems to connect, but there's no music.  I've just installed it for the first time.

---

### Post by Endolith on 2009-10-11
I finally got music to play through speakers, but only when I'm logged into the server through NX.  It won't play sound otherwise, and remote clients won't even connect, and that alone took me a day to figure out.  I give up.  MPD is stupid.

---

