---
title: "The Perfect Media Player"
date: 2006-02-05
forum: Multimedia &amp; Video
---

### Post by aseem_mal on 2006-02-05
Hi All. Can someone suggest a no-qualms, easy-going, user-friendly Media Player for Ubuntu?
I mean, for someone who is switching from Windows to Ubuntu, there must be a decent player that plays most formats, including wmv, mp3 and quick-time videos, and maybe a DVD player too.
I tried playing a wmv video on the Totem player that comes with Ubuntu. I got a error message saying it couldn't play the video.:confused: 

Any suggestions?

Thanks,
A

---

### Post by el3ktro on 2006-02-05
Totem is perfect - it's easy, simple, plays almost everything (incl. DVDs). Just like in Windows, you have to install the right codecs first. I suggest you search the forum for the "Automatix" script which basically just installs all this codec stuff for you + some other extras (Flash etc.). You can also do this by hand, but this script makes it much easier.

Tom

---

### Post by saubz on 2006-02-05
i think totem-xine works best.  for me at least

---

### Post by el3ktro on 2006-02-05
Not only for you ;-) Doesn't automatix install totem-xine anyway?

@aseem:
Totem can use two "backends" which do the actual movie decoding: totem-gstreamer or totem-xine. Both work fine, but totem-xine supports more codecs afaik. I can play mpeg, divx, xvid, wmv & DVDs with no problems.

Tom

---

### Post by JeffV on 2006-02-05
I've been messing around with Totem, but what I don't like is it's deinterlacing doesn't seem to work.  Has anyone else had issues with this?  Are there any media players that deinterlace video decently?

I also installed Totem-xine through Synaptic Package Manager, but It didn't get added to any menus.  So I can't figure out how to launch it.

---

### Post by trevorv on 2006-02-05
You need to install the correct codecs, which as others have said, are provided by Automatix. If you want to do it "by hand" instead, or just want to know what it's doing, check out [this link]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs").

---

### Post by trevorv on 2006-02-05
[QUOTE=JeffV]I also installed Totem-xine through Synaptic Package Manager, but It didn't get added to any menus.  So I can't figure out how to launch it.[/QUOTE]

It replaces totem-gstreamer, so just running Totem from the menu runs totem-xine. AFAIK there are no aesthetic differences, so you can't really tell that way.

As for deinterlacing, I've no idea really, but gxine might be worth a gamble if Totem really won't work.

---

### Post by JeffV on 2006-02-05
I installed all the codecs following all the guides and How-To's I could find.  They all seemed to work and I can play pretty much anything, but it still won't deinterlace the video.  I'll play around with it some more, maybe try some other players.

---

### Post by el3ktro on 2006-02-05
If you don't like Totem then try another player, you could use gxine (which is just another GUI for the Xine media player) or use gmplayer.

All players around are basically just GUIs for either the xine, the mplayer or the gstreamer media player libraries.

xine and mplayer play most codecs, while xine can also play DVDs (including menus), mplayer can also play DVDs, but it doesn't support menus. Generally, mplayer is said to be very fault-tolerant when it comes to broken videos.

Tom

---

