---
title: "mplayer (gmplayer) black windows."
date: 2010-09-13
forum: Multimedia Software
---

### Post by ajgreeny on 2010-09-13
I have to use mplayer, using the gmplayer executable, in order to see some HD videos in MTS file format from my digital camera, and though they play reasonably in mplayer it is impossible to control the video as the control window is blank and black, as is the video window until the video starts to play.  See screenshot.

I have an ATI 9200SE video card, sempron 2400+ cpu, 2GB ram, if that makes any difference.  I have never had this problem in previous Ubuntu versions, only now in Lucid, fully updated.

I have the packages mplayer, mplayer-gui and mplayer-skins installed.  Can anyone tell me what I'm missing.

EDIT:

OK, problem over.

To get the best from my ATI card I was using 16 bit colour.  Discussions last night on another forum questioned many things which made me look again at that, and a change of colour depth has solved that difficulty.

I now need to make sure that the24 bit colour does not introduce other problems which are more difficult to live with, but my xorg.conf is customised and edited from the one I needed to get any display from karmic, so it is possible that I may be able to live with 24 bit colour now in Lucid.

I'll keep you posted.

---

### Post by ajgreeny on 2010-09-16
OK folks.  A follow up to my last SOLVED entry.

I have decided I can't live with the 24 bit colour depth and gone back to 16 bit.  Rendering at 24 bit is painful at times with scrolling in apps going jerky and slow, and things not generally as snappy as at 16 bit.

I am therefore back to 16 bit and living with mplayer acting that way.  I can control it with the keyboard fairly easily, though I am not used to doing it that way.

I am hoping that maverick will be better than lucid with my ATI card; certainly a quick look at the alpha3 maverick seems to suggest things are improving in a number of ways; I can even run the live CD of that on my old laptop that will not manage lucid, without it getting dangerously overheated.  Presumably the newer kernel and kernel power management now working as it should.

---

