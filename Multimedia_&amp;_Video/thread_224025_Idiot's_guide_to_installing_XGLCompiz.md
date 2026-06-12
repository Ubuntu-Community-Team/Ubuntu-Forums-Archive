---
title: "Idiot's guide to installing XGL/Compiz?"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by landwomble on 2006-07-27
Hi All,
Anyone got a real newbie's guide to installing XGL/Compiz and configuring xorg.conf?
I've an IBM thinkpad X31 with an ATI mobility 7000 card in it (which by all accounts doesn't support the fxglr driver, but instead appears natively accelerated using the Ubuntu 6.06 default radeon driver).
I've seen a few guides but they all seem different: what I'm after is an idiot-proof one that I can easily reverse if I hose my system trying it.  In particular, configuring xorg.conf seems to be a nightmare...
thanks!
Ric

---

### Post by Zelut on 2006-07-27
I put together a pretty decent tutorial but its based on my nVidia card.  I, unfortunately, don't have an ATI card to test or I'd put one of those together.  The biggest thing is getting the 3d drivers to work, and then XGL Compiz is a snap.  

One thing I'd suggest before you even think of messing with your xorg.conf is BACK IT UP!  Make a backup, ie; 'cp xorg.conf xorg.conf-GOOD-BACKUP' so you always have a known-working backup to get to.

Take a look at [http://wiki.ubuntu.com/BinaryDriverHowto/ATI](http://wiki.ubuntu.com/BinaryDriverHowto/ATI)

You can find my tutorial in my sig

---

### Post by landwomble on 2006-07-31
> **kuyaedz said:**
> I put together a pretty decent tutorial but its based on my nVidia card.  I, unfortunately, don't have an ATI card to test or I'd put one of those together.  The biggest thing is getting the 3d drivers to work, and then XGL Compiz is a snap.  

One thing I'd suggest before you even think of messing with your xorg.conf is BACK IT UP!  Make a backup, ie; 'cp xorg.conf xorg.conf-GOOD-BACKUP' so you always have a known-working backup to get to.

Take a look at [http://wiki.ubuntu.com/BinaryDriverHowto/ATI](http://wiki.ubuntu.com/BinaryDriverHowto/ATI)

You can find my tutorial in my sig

thanks: using that and the other "thefuture" post on here i've kind of got xgl/compiz working.  "kind of" as in it worked once, and now i'm back to plain gnome for some reason.  not had chance to find out why yet...!

---

### Post by Incense on 2006-07-31
I got mine working useing the guide on this page [http://tazforum.thetazzone.com/viewtopic.php?t=2189&postdays=0&postorder=asc&start=0]("http://tazforum.thetazzone.com/viewtopic.php?t=2189&postdays=0&postorder=asc&start=0")
Good luck.

---

### Post by az on 2006-07-31
> **landwomble said:**
>  what I'm after is an idiot-proof one that I can easily reverse if I hose my system trying it.  In particular, configuring xorg.conf seems to be a nightmare...
thanks!
Ric

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

---

### Post by srikat on 2006-07-31
[http://www.ubuntuforums.org/showthread.php?t=225967](http://www.ubuntuforums.org/showthread.php?t=225967).

---

