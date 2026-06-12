---
title: "classicfm (uk) on 7.10 ?"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by jamaas on 2007-11-15
Can anyone tell me if it is possible to get classicfm (uk) to stream on 7.10, and if so what player to use?  I will likely need some setup instructions, thanks a bunch.

Jim

---

### Post by Cantabile on 2008-02-05
ClassicFM also won't play in my Feisty box. Although I have the mplayer-plugin installed, there is still this pop-up window warning me that I'll need a compatible player to listen to their program.

After searching the forum, it seems somebody has got classifm play in konqueror. Anyway, does anybody know how to get it work in firefox? Thanks.

---

### Post by ron999 on 2008-02-05
Hi
It's playing ok for me.
When the popup window tells you that you need a compatible player I had to click where it says _click here_.
Then it opens up with the mozilla mplayer plug in.

You can also play it straight from the command line using:-
> mplayer [http://mediasrv-the.musicradio.com/ClassicFM?MSWMExt=.asf](http://mediasrv-the.musicradio.com/ClassicFM?MSWMExt=.asf)
(That's not meant to be a link, it's a command line instruction.)

Use 
mplayer
http://
mediasrv-the.musicradio.com/ClassicFM?MSWMExt=.asf
All on one line.  When I print it here as one line it gets shown as a link.

---

### Post by Cantabile on 2008-02-05
Hi Ron999,

Great! it works. The "click-here" trick didn't work for me, but the command line works like a charm. Then I copied it into the open -> play URL window in the GUI of mplayer, and it works too. 

Thanks a lot:)

---

### Post by westdale on 2008-05-30
And just to keep things simple for me as a beginner, pasting the link straight into Firefox 3 beta works under Heron.

---

