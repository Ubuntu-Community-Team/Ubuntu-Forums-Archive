---
title: "Recommended DVD Player"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by tripwire45 on 2006-08-10
I'm testing out my new installation of Dapper Drake on my Dell laptop. It plays music CDs just fine, but Totem wasn't able to play a DVD movie stating that it couldn't locate a URI handler. 

Any recommendations for a good DVD player?

Thanks. 

-Trip

---

### Post by Fass on 2006-08-10
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Jagot on 2006-08-10
Totem should be able to play them just fine.  Did you do this:

[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

Failing that, VLC always works for me.

---

### Post by tripwire45 on 2006-08-10
Thanks, Jagot. I followed the instructions but got the same error message:
```
No URI handler implemented for "dvd".
```

Guess I'll try your other suggestion.

---

### Post by tripwire45 on 2006-08-10
Unfortunately...VLC doesn't seem to respond and I suspect for the same reason. I must be missing a configuration step on order to get the players to recognize the DVD. VLC knows there's a DVD there but apparently doesn't know what to do with it.

---

### Post by tripwire45 on 2006-08-10
Anyone?

---

### Post by tripwire45 on 2006-08-11
:bump:


Anybody? 


:confused:

---

### Post by click4851 on 2006-08-11
well....I would try Easy Ubuntu or Auntomatix cuz I get lazy. Have you installed the libdvdcss libraries, you will need the restricted repositories for that I'm pretty sure.

---

### Post by tripwire45 on 2006-08-12
Actually, gxine seems to be the answer. Pop a DVD in and it plays like a charm. :D

---

### Post by tripwire45 on 2006-08-21
Well...it did. A few nights ago, I played X-men one and two but tonight, I can't play a Star Trek TOS disk. I thought it was the disk itself but it won't play any of them. It plays the first 22 seconds when the Paramount logo launches, then goes black and nothing happens. The player locks up and has to be forced to quit. Ideas?

---

### Post by Carbonfish on 2006-08-22
Hi tripwire45,

While I know that misery doesn't *really* love company, at least I can put your mind at rest that your problem is not hardware specific. I have been using gxine for a little over a week on my IBM Thinkpad (T23) running Dapper, and everything has been okay until this evening when I was watching a dvd and about 1/3 of the way through the disk it froze hard. I had to force shut-down. I Googled "gxine freeze" and got quite a few hits, so it appears that it is a known issue. 

I will be searching for/working on a fix and if I stumble across anything I'll come back here and let you know.

KC

---

