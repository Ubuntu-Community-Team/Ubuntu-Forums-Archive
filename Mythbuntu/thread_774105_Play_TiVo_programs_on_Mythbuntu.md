---
title: "Play TiVo programs on Mythbuntu"
date: 2008-04-29
forum: Mythbuntu
---

### Post by wusl.au on 2008-04-29
I've just installed Mythbuntu 8.04, and one of the things I'd like to do with it is allow remote playing of the content from my LAN connected (Oz)tivo.

Research has given me the impression that Mplayer will play the .ty streams.  I found a very terse page at [http://tivo-mplayer.sourceforge.net/mythtivo.html](http://tivo-mplayer.sourceforge.net/mythtivo.html) that 'looks' like someone's done some work in this area, but the code that I downloaded is putting up a damn good fight.

I have the vserver (TiVo) end working, and can successfully play tivo programs on a PC.

Is anyone else here in the same boat, or has got such an arrangement working?

---

### Post by murchball on 2008-04-29
Looks like the latest version was for MythTV Version 0.11. I'd say that the project has died. Honestly, unless it supported the newer cablecard tivos, I'm not sure what this would do for you that you couldn't accomplish with an analog tuner in Myth.

---

### Post by wusl.au on 2008-04-29
Well, I'm hoping to do that as well, but the Tivo's merrily running around collecting my favourite shows onto its hard disk.

Seems a bit silly to collect that stuff twice, when all I need to do is just get these two devices to cooperate.

I *know* that the streaming will work, since a PC can do it, and apparently the XBMC will do it.

If no one's done it in Myth, maybe I need to look closer myself.

---

### Post by murchball on 2008-04-30
Depending on which series TiVo you have, isn't it possible to share videos between multiple TiVos? I haven't looked in a while, but I believe it used to be called multi room viewing. Of course, it required multiple TiVos :D

---

### Post by wusl.au on 2008-05-05
Okay, on a somewhat different tack, I've tried to play tivo files form the commend line.

Now, the mplayer manual says that you can open a tivo stream in Mplayer with **'mplayer tivo://<hostname>/<FSID>**' using the command line.

When I try this, I get the message (for example):
No stream found to handle url tivo://tivo/279953

Mplayer *will* play a .ty file if I import it into the machine via ftp, so it's not lack of codec support.  Has the version of Mplayer in Mythbuntu had tivo (and possibly other) streaming removed or not compiled in?

I can recall having done something like this quite a while ago, but I've had many sleeps since then, and hoped that a nice new HTPC distribution might be a little friendlier in this regard.  *Silly me*.

---

### Post by glenstewart on 2009-10-29
You need to find a version of mplayer (or build it yourself) that has vstream support compiled in.  Supposedly, the new Karmic build has it enabled.

---

### Post by mythding on 2009-10-30
You just need tivodecode and curl(or wget) no special mplayer compile.
[http://tivodecode.sourceforge.net/](http://tivodecode.sourceforge.net/)
> curl -k --digest -u tivo:{MAK} -c /dev/null "{tivo2go url}" |\
tivodecode -m {MAK} -- - |\
mplayer -vf pp=lb -cache 32768 -I have a plugin for mythtv that does this for me but I am still working on it
and I dont think there is much want for it anyhow.

BTW this thread was last active like more than a year ago. ;)

---

