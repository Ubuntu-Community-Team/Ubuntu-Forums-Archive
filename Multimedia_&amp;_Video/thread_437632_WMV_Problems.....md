---
title: "WMV Problems...."
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by bob1234 on 2007-05-09
I everyone. To start I should say that I am a complete linux newbie but I have always thought open source was the best way to go, so here I am.

My problem is that I am trying to watch a wmv video that is embedded in a webpage. I am using the totem video plug in for firefox and I am using ubuntu 7.04. I can get lots of other wmv files to play in firefox.

The files I can not play are located at [http://www.bnn.ca/shows/past_archive.tv](http://www.bnn.ca/shows/past_archive.tv)

Any help would be greatly appreciated,

Thanks

---

### Post by dolphin_oracle on 2007-05-09
that site is using a proprietary player based on Windows Media Player.  The links use javascript to call something called RobtvVideoPlayer, and do not call a wmv file directly.  I'm guessing either they are using a proprietary format or its DRM'd (or both), which the w32codecs don't support.

---

### Post by bob1234 on 2007-05-10
So I guess there would be no way to play that using Ubuntu...

---

### Post by anthony_barker on 2007-08-17
I have it working on older version of ubuntu (6.06) using firefox and mplayer.

Stupid website using wmv - complain to them.

---

### Post by mrmark24 on 2007-08-17
bob1234,

I had a similar problem, but with watching MLB.TV games online; they're in WMV format, too.

I went to the Firefox add-on page (Tools: Add-ons, from the menu bar), and discovered the "MediaPlayerConnectivity" add-on, which allowed me, with some tweaking, to open the ball games in VLC media player (available in "Applications: Add/Remove," in the Apps menus), which supports WMV format.

Search for it; download it; "tweak" it; and you should be on your way watching WMV streams.

Sincerely,
mrmark24

---

### Post by cinajohn on 2007-09-09
mrmark,

I am trying to tackle the same situation with mlb.tv.  


I have been able to get the audio broadcasts but no luck with the video on my 7.04 64bit.

Are you running 7.04 64bit?

--EDIT-- I got it working!  Thanks for the ideas.

---

