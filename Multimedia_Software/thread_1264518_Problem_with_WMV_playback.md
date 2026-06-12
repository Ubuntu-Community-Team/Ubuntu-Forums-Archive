---
title: "Problem with WMV playback"
date: 2009-09-12
forum: Multimedia Software
---

### Post by borophyll on 2009-09-12
I am having trouble playing back WMV formats using a single player.  When I try to play the streaming WMV from [http://home.att.net/~cherokee68/wmvtest2.html]("http://home.att.net/~cherokee68/wmvtest2.html"), it works fine in xine, but mplayer mangles it up badly.  On the other hand, if I play the WMV file at [http://home.att.net/~cherokee68/wmvtest.html]("http://home.att.net/~cherokee68/wmvtest.html"), mplayer handles it fine, but xine has no sound and the video is really jerky.

While I can successfully play both formats using one or the other, this is annoying when trying to play WMV in Firefox, where I have to use either xine or mplayer plugins.

I have installed the restricted extras, and the w64codecs from Medibuntu.  I'm not sure what else to do to get them working.  Why such different results?  Do they refer to different codecs?

regards,
B.

---

### Post by borophyll on 2009-09-12
Is anybody getting the same problem as I am?  What steps should I take to troubleshoot this?

---

### Post by tudor117 on 2009-09-12
I'm not sure how to fix it, however, both the files play fine for me in both firefox 3 and shiretoko (firefox 3.5).
Does firefox list "Windows Media Player Plug-in 10 (compatible; Totem)" in the Add-ons -> Plugins menu? Or at least anything similar?
Once I disable this plug-in, there is no longer video player on the site.

---

### Post by borophyll on 2009-09-12
At the moment I am using Gecko plugin, but it uses mplayer to play WMV.  It's not so much the Firefox plugin I'm worried about.  I am actually playing the files from the command line, as follows:

mplayer [http://home.att.net/~cherokee67/Budlight_sunburn.wmv](http://home.att.net/~cherokee67/Budlight_sunburn.wmv)
mplayer [http://home.att.net/~cherokee68/C4.wmv](http://home.att.net/~cherokee68/C4.wmv)

AND

xine [http://home.att.net/~cherokee67/Budlight_sunburn.wmv](http://home.att.net/~cherokee67/Budlight_sunburn.wmv)
xine [http://home.att.net/~cherokee68/C4.wmv](http://home.att.net/~cherokee68/C4.wmv)

Like I said above, with xine the first plays fine but not the second.  With mplayer the second video plays fine but not the first.  Both xine and mplayer *do something* with both files, but only render one or the other properly.

I think once I work this issue out, the Firefox stuff will resolve itself.

---

### Post by tudor117 on 2009-09-12
Hmmm so just to let you know, I have the same issue as you. One works with one player the other with the other. However xine does have sound on the second file, but you need to turn it up. For some reason xine does this to some files (just starts with audio muted or to lowest level).

On the other hand, have you considered an other player? Totem plays excellent and vlc isn't too bad.

---

### Post by borophyll on 2009-09-12
I tried both of these videos in Totem, and they both work fine.  I'm guessing it is a bug with mplayer and xine?  I think I will ask around on the mplayer and xine forums about these issues, and see what they say.  If anything of interest comes up, I will post it here.

For now, I will use Totem.  Thanks for your help tudor!

---

### Post by tudor117 on 2009-09-12
No prob.

The problem is that every player has its faults. For example totem can't play some of my avi's correctly; they need to be indexed and resaved used avidemux.
So, I guess... nobody's perfect :P

---

