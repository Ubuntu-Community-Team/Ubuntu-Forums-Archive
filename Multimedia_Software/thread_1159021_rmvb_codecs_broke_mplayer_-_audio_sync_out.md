---
title: "rmvb codecs broke mplayer - audio sync out"
date: 2009-05-14
forum: Multimedia Software
---

### Post by lannatwin on 2009-05-14
Ubuntu 8.10

So, I followed the instructions here: [http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/](http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/) to install the codecs to play rmvb files in mplayer.  rmvb files now play fine.

The problem is that now when watching some avi files, the audio and video are way out of sync.  They play fine in VLC player.  I have fooled around with various settings to no avail.

Short of removing the codecs, anyone have any suggestions for correcting this?

Thank you.

---

### Post by andrew.46 on 2009-05-14
Hi lannatwin,

Can I ask which version of MPlayer you are using? Best way to see this is with:

```
andrew@skamandros~$ **[COLOR="Red"]mplayer | head -n 1[/COLOR]**
MPlayer SVN-r29286-4.2.4 (C) 2000-2009 MPlayer Team
```

It would be great if you could post some of these troubled avi files online somewhere as well.

All the best,

Andrew

---

### Post by lannatwin on 2009-05-15
Andrew,

Thank you for the reply.

This is the mplayer version:
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team

One video I am having trouble with can be downloaded here: [http://torrent.zoink.it/The.Daily.Show.2009.05.13.(DSR-YT)%5BVTV%5D.torrent](http://torrent.zoink.it/The.Daily.Show.2009.05.13.(DSR-YT)%5BVTV%5D.torrent)

It plays fine with mplayer on another machine that I haven't installed the rmvb codecs in.  On two other machines that have the rmvb codecs, the audio sync problems are very bad.

Cheers,
lannatwin

---

### Post by andrew.46 on 2009-05-15
Hi lannatwin,

> **lannatwin said:**
> 
This is the mplayer version:
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team

Can I suggest that you update your version of MPlayer? This alone may be enough to fix the problem, although it does not explain everything that you have described. Perhaps the easiest way might be to use [RVM's PPA]("https://launchpad.net/~rvm/+archive/mplayer"), a harder option is to [compile your own]("http://ubuntuforums.org/showthread.php?t=1081070").

> One video I am having trouble with can be downloaded here: [http://torrent.zoink.it/The.Daily.Show.2009.05.13.(DSR-YT)%5BVTV%5D.torrent](http://torrent.zoink.it/The.Daily.Show.2009.05.13.(DSR-YT)%5BVTV%5D.torrent)

Oops, a 170meg torrent download is a little too much for my connection :-).

> It plays fine with mplayer on another machine that I haven't installed the rmvb codecs in.  On two other machines that have the rmvb codecs, the audio sync problems are very bad.

I doubt that the codecs themselves are the problem, mind you there are [newer codecs available]("ftp://ftp.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2") than the ones mentioned in that guide. I would suggest again that a newer version of MPlayer would be an excellent starting point, and if the errors persist there are a few more options still that can be explored.

All the best,

Andrew

---

