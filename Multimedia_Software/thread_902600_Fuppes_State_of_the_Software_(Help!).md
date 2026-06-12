---
title: "Fuppes: State of the Software? (Help!)"
date: 2008-08-27
forum: Multimedia Software
---

### Post by flatline on 2008-08-27
Ok, here's the deal.  I built a server (specs are in my sig), and successfully compiled FUPPES on it.  I wasn't able to check out a recent SVN copy (couldn't connect to the server - is it still being updated?), so I had to download a tarball from sourceforge (r578 IIRC).  Anyways, it appears to be working more or less correctly.  I am having some issues however:

First, a minor question - since it is on a server, I have it running in /etc/init.d/fuppesd as a daemon.  I am using a job in cron.hourly to rebuild the database and the virtual containers.  If this happends while someone is watching a video, would that be bad, or is it smart enough to work around it?  I could always move the rebuild script to cron.daily and try to schedule it for a more convenient time, but I just setup the server and have been adding lots of new media to it.

It is only being used to stream to Xbox 360s - mine and my roommates.  Files used to start playing almost instantly when I had AVI transcoding enabled, but then it would stop playing after several seconds.  Now, with it disabled, it takes quite a long time of "Buffering" before it starts a video - is this normal?

This pops up now and then:
```
$ == lib/Fuppes.cpp (203) :: Wed Aug 27 13:29:00 2008 ==
device: Xbox 360 timed out

:1: parser warning : xmlns:ms: ' urn:microsoft-com:wmc-1-0' is not a valid URI
ot xmlns="urn:schemas-upnp-org:device-1-0" xmlns:ms=" urn:microsoft-com:wmc-1-0"
```

Additionally, once it begins playing, my roommates' xbox seems to be fine, but mine only plays for a minute or two before it starts buffering again, and it either never stops or the audio gets out of sync with the video.  This I'm afraid might be due to everything being wireless - he is much, much closer to the AP.  Is there any config item I can mess with to try to alleviate this, or should I just buy a big honkin' cat5 cable?

Also - .divx files do not show up.  It was my understanding that the 360 can now natively play xvid/divx ([http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Microsoft_Xbox_360](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Microsoft_Xbox_360)), yet my Season 1 of Robin Hood does not show up.  Also, my, erm, screener of Global Frequency (which is a .mpg) does not show up either.  Thoughts?

Any help on any of these issues would be greatly appreciated; I thought getting fuppes compiled was supposed to be the hard part!

I have attached my fuppes.cfg for your criticizing pleasure.

---

### Post by flatline on 2008-08-27
Lovely, it also appears that now, some files that previously worked are coming up with an error...

Doctor Who 2005 - 1x07 - The Long Game (ws_pdtv_xvid-fov.[BT]).avi

The file above now refuses to play, even though I watched it this weekend.  Is this because I turned off transcoding?  Is it possible to enable transcoding for only certain AVI files? *grumble*

---

### Post by flatline on 2008-08-27
Bump...

---

### Post by flatline on 2008-08-28
Bumping... No one out there can address ANY of my problems?

---

