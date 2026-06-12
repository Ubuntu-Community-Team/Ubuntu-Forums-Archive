---
title: "Firefox mplayer plugin and nhl.com"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by kotter71 on 2006-10-28
Via Edgy, I simply cannot get mplayer-plugin to render the highlights from [www.nhl.com](www.nhl.com).  I installed all of the additional multimedia applications/codecs using Automatix and everything else works nicely except for wmv files.

Has anyone else had any trouble with [www.nhl.com](www.nhl.com) streams?  I can get it to work in Fedora Core 6, but not with Edgy.

In any event, I simply re-compiled the latest mplayer source from scratch, installed it (as well as the most recent codecs) to /usr/local, and now everything works perfectly.

I am just wondering if anyone else is having trouble with the default install via Automatix.

---

### Post by lognok on 2006-10-28
Yes, installed it via Automatix2, but can't play the highlights from the link you posted.

As well I can't play quicktime files from apple's trailer page.

Guess I have to compile it, to get it working.

---

### Post by lognok on 2006-10-28
Ok, got it working. Just had to clean up my /usr/lib/firefox/plugins directory also the /usr/lib/firefox/components directory for signs of other players that plays the same format. Have removed gxine and vlc plugins from those directories.

Could be some kind of mix-up, in that it throws firefox of, because it can't decide which plugin to use, maybe?.

The highlights from your link plays in the pop-up window. Also the trailers page from apple now plays fine too :p

---

### Post by tool462rules on 2006-10-28
How did you go about building mplayer?

---

### Post by kotter71 on 2006-10-28
> **tool462rules said:**
> How did you go about building mplayer?

I basically just downloaded the latest source as explained on the mplayerhq.hu webpage:

> 
Downloading MPlayer from Subversion

You can also get MPlayer via Subversion. Issue the following command to get the latest sources:

  svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

A directory named mplayer will be created in the current directory.


And then I more or less followed the build instructions listed here:

[http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt)

After running 'make install' all of the new files were installed into /usr/local and now, instead of the mplayer binaries supplied by Automatix, somehow the my new mplayer binaries handle all the mplayer requests by default - which is nice.

Otherwise, I also went into the /usr/lib/mozilla/plugins directory and removed totem plugins and other plugins which attempt (and fail miserably) to handle realplayer.

---

### Post by kotter71 on 2006-10-28
> **lognok said:**
> Ok, got it working. Just had to clean up my /usr/lib/firefox/plugins directory also the /usr/lib/firefox/components directory for signs of other players that plays the same format. Have removed gxine and vlc plugins from those directories.

Could be some kind of mix-up, in that it throws firefox of, because it can't decide which plugin to use, maybe?.

The highlights from your link plays in the pop-up window. Also the trailers page from apple now plays fine too :p

I have to install ubuntu on my machine at work (because, after 6 iterations, I abandoning Fedora) so I will try your method of cleaning up all the plugin and component directories (no gxine nor vlc plugins).  I don't mind compiling from source so much, but your method is much easier.

Are there any other multimedia-streaming WEB sites out there that any of you are experiencing any troubles with?

---

