---
title: "Playing streaming Real/Windows media with xfmedia"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by Barely Here on 2007-09-15
Has anyone managed to get xfmedia in Xubuntu Dapper to play streaming Real media or streaming Windows media?

I've installed all the packages suggested in Xubuntu Dapper's Official Documentation: Get media support, and the gstreamer and libxine packages suggested in Community Docs: RestrictedFormats. I've also installed the w32codecs from Medibuntu.

I was partially rewarded with my effort: I can play stand-alone Real media and Windows media audio files saved in my hard disks....

But I still cannot get xfmedia to play the streaming version :x

---

### Post by Barely Here on 2007-09-19
Should I just throw in the towel and install gxine plus the gxine Mozilla plugin?

---

### Post by andrew.46 on 2007-09-20
Hi,

 The best way to play all of these formats is to use mplayer. I am not sure how fully kitted out the repository version is but if you can compile from source and add the codecs manually you will be able to play almost all media streams.

 The mplayer site is:

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

 And a half made site that describes installing the svn mplayer and the full version of the codecs is here:

[http://people.aapt.net.au/~adjlstrong/ftgws.html](http://people.aapt.net.au/~adjlstrong/ftgws.html)

 This half a walkthrough does not include the gui. One day I will finish it :-)

                  Andrew

---

### Post by Barely Here on 2007-09-23
Ah, a fellow Aussie! I will check out the web sites.

---

### Post by andrew.46 on 2007-09-23
Hi!

Quite a few Australians here I think, I am in the Blue Mountains in NSW.

> **Barely Here said:**
> Ah, a fellow Aussie! I will check out the web sites.

My svn mplayer page is actually complete now. Compiling the svn mplayr is not the _easiest_ thiing that you will ever do in Linux but it is well worth the effort.

                Andrew

---

