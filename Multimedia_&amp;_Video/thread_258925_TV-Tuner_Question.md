---
title: "TV-Tuner Question"
date: 2006-09-16
forum: Multimedia &amp; Video
---

### Post by yoink23 on 2006-09-16
Does anyone have any information on when ATI All-In-Wonder 9800 cards will be supported for tv tuner capabilities?  

I think the GATOS project was working on it, but now that project has merged with x.org.  I am having trouble finding any up to date info on it at all, I suppose because the card is getting old.  

Will I ever be able to tune TV in linux with this card?

Thanks,
Yoink

---

### Post by dawdler on 2006-09-21
Check this thread:

[http://www.ubuntuforums.org/showthread.php?t=215763]("http://www.ubuntuforums.org/showthread.php?t=215763")

which has instructions similar to this site:

[http://doc.gwos.org/index.php/TVout_for_legacy_ATI_cards_using_GATOS]("http://doc.gwos.org/index.php/TVout_for_legacy_ATI_cards_using_GATOS")

except the ubuntu thread has the following line:

```
gunzip -c xorg7-6.5.8.0-tv_output.patch.gz | patch -p1 -d xf86-video-ati-6.5.8.0
```

rather than this line from the doc:

```
gunzip -c xorg7-6.5.8.0-tv_output.patch.gz
```

I followed the doc site and failed to get my tv-tuner working.  I have a ATI Rage Mobility LT.

---

