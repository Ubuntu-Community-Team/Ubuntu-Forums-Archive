---
title: "Amarok starts up slow"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by FuturePilot on 2007-03-11
In Edgy whenever I start up Amarok it takes like 10 seconds before the splash screen even shows up. When I click on Amarok there's almost no hard drive activity for around 10 seconds then there's a little and then none.  The splash screen just sits there for a long time before Amarok even starts.  And there seems to be no hard drive activity when the splash screen is sitting there.  If I reinstall it it works fine and it's fast but then the next time I use it it's slow again. Anyone else having these problems? It always worked perfectly in Dapper.

---

### Post by gkiller on 2007-04-21
I'm having the same problem, in Edgy and Feisty.
I have disabled the splash screen, so when I start Amarok, CPU just goes to 100% for like 15-20 seconds, before the is usable.

I have about 4000 tracks in my collection and I'm using the SQLite backend. But this should not be a problem, 4000 isn't that much compared to others. So the problem is probably elsewhere.

Oh, and I'm using Gnome... maybe all the KDE libs take so long to start?

Did you solve your problem? If yes, please tell me how :)

---

### Post by tictacman on 2007-04-21
I had a problem with edgy and amarok in that everytime I loaded the hard drives would start thrashing - so once I loaded up my library in configure > collection tab I unchecked watch folders for changes.  Not sure if that will help

---

### Post by gkiller on 2007-04-21
That did not help unfortunately.

Every time I start amarok (even when just closed before), I get 100% CPU but no hard drive activity at all. This is strange. Because it happens every time and not just the first time I now think it's not the KDE libs either.

---

### Post by wataboutbob on 2007-04-21
> **gkiller said:**
> That did not help unfortunately.

Every time I start amarok (even when just closed before), I get 100% CPU but no hard drive activity at all. This is strange. Because it happens every time and not just the first time I now think it's not the KDE libs either.

I agree. I have the same problem. Just populating or skipping a song will result in Amarok hanging. I think I'll uninstall and try 1.4.4 rather than this 1.4.5 version.

---

### Post by gkiller on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/108573](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/108573) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have opened a bug report about this:
[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/108573](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/108573)

If you are experiencing the same problem, please add a comment there. But only if it is the same issue (ie: high CPU usage for some time after starting Amarok, while Amarok is not responding), to avoid mixing several problems in one bug entry.

---

### Post by gsiliceo on 2007-07-03
same problem here, does installing .4 ver. helped?

---

