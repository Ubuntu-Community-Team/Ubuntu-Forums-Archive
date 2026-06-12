---
title: "Even with every codec at hand, still no m4a support in edgy."
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by Madhatter14641 on 2007-03-06
I've been with Ubuntu for a while now. At first, it was a bit of a struggle to get multimedia running. As I learned more, however, this process eased considerably. I upgraded to Edgy once it was stable and have been quite happy with the advances. My only problem  is that I can't get m4a support. It hasn't been a problem until now; breezy and dapper played them magnificently. I've installed all of the restricted formats and can even get m4a playing out of mplayer. 

My ultimate goal is to have m4a support in amarok (specifically the 1.4-svn). It's just too pretty, you know? It's compiled with faad2-dev and libmp4v2-dev; the required flags were inserted appropriately. All mp3 files are working fine. I think the problem is in the xine engine, although Songbird (running off of the gstreamer engine) is having the same problem. I have the files installed for both gstreamer0.8 and 0.10; xine-extracodecs is installed as well. I've been searching the boards for a long time now and just can't find a solution. Any ideas?

---

### Post by toasterofirony on 2007-03-06
Would installing faac and it's relevant gstreamer component not sort you out? I only say this because you've not mentioned it and I've got it installed and can play m4a's quite happily.

---

### Post by benjaminzsj on 2007-03-06
> **Madhatter14641 said:**
> I've been with Ubuntu for a while now. At first, it was a bit of a struggle to get multimedia running. As I learned more, however, this process eased considerably. I upgraded to Edgy once it was stable and have been quite happy with the advances. My only problem  is that I can't get m4a support. It hasn't been a problem until now; breezy and dapper played them magnificently. I've installed all of the restricted formats and can even get m4a playing out of mplayer. 

My ultimate goal is to have m4a support in amarok (specifically the 1.4-svn). It's just too pretty, you know? It's compiled with faad2-dev and libmp4v2-dev; the required flags were inserted appropriately. All mp3 files are working fine. I think the problem is in the xine engine, although Songbird (running off of the gstreamer engine) is having the same problem. I have the files installed for both gstreamer0.8 and 0.10; xine-extracodecs is installed as well. I've been searching the boards for a long time now and just can't find a solution. Any ideas?
Same here. Codecs are there but most of the players just won't play.

---

### Post by panch0 on 2007-03-07
Have you tried MPlayer (use KPlayer for a frontend)? It does practically every format out of the box.

---

### Post by Madhatter14641 on 2007-03-08
I've got the whole gstreamer suite installed, but I didn't compile amarok with the support. As a matter of fact, I can't even seem to find an option to do so. Mplayer works fine, but it's not as fleshed out as amarok is for what I want to do. 

It's also not picking up all of my mp3's, but I suspect that's an issue with the SVN and not codecs.

---

### Post by panch0 on 2007-03-09
Try KPlayer to see if it has what you need as far as GUI. It may not have all the features of amarok, but for me it does everything I need from a media player.

---

### Post by lebabyg on 2007-04-03
This topic is probably closed, but if not, go here
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Install the w32codecs using apt-get and all is well.

---

### Post by AusIV4 on 2007-04-04
I realize this thread is a couple of weeks old (aside from the last post), but on Amarok in Edgy, I'm pretty sure i was able to play m4a files after allowing Amarok to go out and get mp3 codecs.

On a fresh install, if you try playing an m4a file, it will say it can't find codecs. If you try to play an mp3, it will offer to retrieve codecs and install them. If you do that, m4a will be installed for you.

The same didn't work for dapper, but I haven't changed anything in my dapper install for several months, so I don't remember what codecs I installed there. libxine-extracodecs perhaps? (I think this is what is installed when Amarok retrieves codecs for you).

---

