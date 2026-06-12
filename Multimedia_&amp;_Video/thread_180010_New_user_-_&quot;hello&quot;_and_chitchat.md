---
title: "New user - &quot;hello&quot; and chitchat"
date: 2006-05-21
forum: Multimedia &amp; Video
---

### Post by prismatic7 on 2006-05-21
Hi all - finally made the switch away from Windows to Ubuntu after years of playing around and wishing WINE would work properly. Hurrah!

Yes, I'm a muso. I've been using [Buzz Tracker](http://www.buzzmachines.com) for a long time - it works in Dapper/WINE and I'll write up a full HOWTO bit later. But for now, I'm very interested in Ubuntu Studio, using Buzz as my main platform and mastering to Ardour or suchlike. 

Given that the kernel freeze date for Dapper was a few days ago, where does that leave Ubuntu Studio? Is there a current, recommended way to build a RT kernel for Dapper (I tried the Breezy way and flubbed it several times in a variety of different ways)?

---

### Post by Sef on 2006-05-21
Welcome Microsoft-Free user.  

> Given that the kernel freeze date for Dapper was a few days ago, where does that leave Ubuntu Studio? Is there a current, recommended way to build a RT kernel for Dapper (

Since it is a third party project that would depend on the people putting it together.

---

### Post by prismatic7 on 2006-05-21
[QUOTE=Sef]Since it is a third party project that would depend on the people putting it together.[/QUOTE]
Well, yes... I'd figured that. Perhaps I didn't explain myself correctly. I meant to refer to the post in [this thread](http://www.ubuntuforums.org/showthread.php?t=146236) which states:

[QUOTE=dolson]We already plan to release a -rt kernel for Dapper after kernel freeze.

Besides that, the entire point of The Ubuntu Studio Project is that it is a wiki for people to add documentation and such.[/QUOTE]

When I say I've switched from M$, I should point out that I've been a Debian server admin for about 7 years, four of those years in enterprise. The thing is, I'm an admin, not a coder. I'm interested to know if anyone's managed to bang up the -rt kernel in Dapper, because I couldn't get 2.6.16 vanilla and the -rt23 patch to play nice.

---

### Post by mimp on 2006-05-24
Yeah i'd love to see this too as i only ever managed to get an old kernel up and running in -rt, and that broke my wireless card and (more importantly) the lineout on my laptop. Worked at lovely low latencies, but only from my mini laptop speakers :-)

I'm a more-or-less complete linux newbie tho so pretty much at the mercy of my betters.

How well does buzz work in wine by the way? I've been using it for years and am finding it hard to ween myself off. Can you route it's output about in jack? that alone would make it more usefull then running it under windows.. Who knows maybe i could fudge some way of persuding it to sync to other apps, although i think i'm now in daydream territory.

---

### Post by prismatic7 on 2006-05-24
[QUOTE=mimp]
How well does buzz work in wine by the way? I've been using it for years and am finding it hard to ween myself off. Can you route it's output about in jack? that alone would make it more usefull then running it under windows.. Who knows maybe i could fudge some way of persuding it to sync to other apps, although i think i'm now in daydream territory.[/QUOTE]

To be honest, Buzz works well but issues with VST plugins and sound quality have sent me scurrying back to WinXP to use it. I'll be doing post and mastering in Ubuntu, though.

I've got a quick review up at [buzzmachines](http://web.hibo.no/~mva/viewreview.php?id=1138).

---

### Post by dolson on 2006-05-24
I haven't talked with any of the other guys who helped with the kernel lately, so I will contact them within a week and start working on it again.

We may have hit a "kernel freeze" but if you are paying any attention, there was still another update even today. So it is not very frozen if you ask me.

---

