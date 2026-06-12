---
title: "Feisty Mplayer Workaround"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by Amaroq on 2007-04-24
I don't know who else is having problems with Mplayer in feisty, but I sure was. I upgraded from dapper to edgy, then to fiesty. Somewhere along the way, the sync between video and sound in mplayer that I had to tamper around to get working right, got messed up again. The video was playing slower than the audio. I fixed it for the most part just by enabling direct rendering and messing with which drivers it used, but no matter what I did, the best I could get it was the audio still being slightly faster than the video.

But alas, google has proven to be my friend, just as it has time and time again. A search brought me to this page.
[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

At the bottom of that page is a .deb package for, you guessed it, mplayer. I simply removed mplayer and mencoder, downloaded and installed that .deb via dpkg, and my mplayer's sound and video were synced again.

Unfortunately, it comes with a bit of a price. I don't have a gmplayer anymore. Trying to right click anything and play in mplayer results in some error box that dissapears before I can see it. The only way to view it is to use mplayer from the terminal.

---

### Post by sseitz on 2007-05-03
the error is caused by an invalid skin path. this is easily corrected by:

sudo mkdir /usr/local/share/mplayer
sudo ln -s /usr/share/mplayer/skins /usr/local/share/mplayer

the only message left is the (to me, wellknown) 'New_Face' font ... failed.
If someone could enlighten me, how and where to install this Font?

---

### Post by Michaelt74 on 2007-05-03
I found mplayer difficult ( impossible) to use. I'm new to Ubuntu but found VLC a much better option. This post may help to set up VLC.

[http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/](http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/)

---

### Post by m_kylli on 2007-06-02
Found the problem. There's no need to reinstall mplayer from a different source. All you need
to do is to open the "/etc/mplayer/mplayer.conf" file and comment out the line "ac=mad," witch
sets mad as the default audio codec.

---

