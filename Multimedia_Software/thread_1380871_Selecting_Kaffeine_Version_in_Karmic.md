---
title: "Selecting Kaffeine Version in Karmic?"
date: 2010-01-14
forum: Multimedia Software
---

### Post by Col-1023 on 2010-01-14
I'm having problems with the default version of kaffeine in karmic.

When I check kaffeine in synaptic and look at the versions, there is the older 0.8.7 version listed.

Can I select this older version, which worked well for me in jaunty, and if I can select it, will this older version cause problwms in karmic.

I was thinking that since it's listed, as one of the version it should be safe, but I want to be sure, since DVB-T capture is  important for my karmic 64 bit box.

Any help appreciated.

---

### Post by Col-1023 on 2010-01-15
Has anyone tried the older package in the karmic repos?

---

### Post by Col-1023 on 2010-01-16
bump

---

### Post by Col-1023 on 2010-01-17
bump

---

### Post by mc4man on 2010-01-17
If the question is - can I use kaffeine 0.8.7 in karmic?, sure, why not.

It may even prove to be a more useful player than the new one depending on what you're using it for
(xine backend with complete settings, good dvd playback with navigation ect.

If you're running ubuntu I can say it works fine, if kubuntu don't know.

I installed it directly from [here]("http://packages.ubuntu.com/en/jaunty/kaffeine"), had 2 add. packages that needed to be installed and works fine after a few config's in xine engine parameters.

As far as it being available in karmic repos (synaptic) then that's a bit curious because it's not an available karmic app (at least here on ubuntu 9.10

You may want to ck. your sources and see if you still have some jaunty repo's enabled.

---

### Post by howefield on 2010-01-17
1.0~pre2-0ubuntu1

This should be the version you find in Karmic and it works very well and also looks good.

[http://packages.ubuntu.com/karmic/kaffeine](http://packages.ubuntu.com/karmic/kaffeine)

Have you that and the older one showing ?

---

### Post by Riverside on 2010-02-15
> **howefield said:**
> 1.0~pre2-0ubuntu1

This should be the version you find in Karmic and it works very well and also looks good.I beg to differ.  I have been using Kaffeine from Ubuntu 8.04 onwards (0.8.6) and have previously been delighted with it however the new version 1.0-pre2 shipped with 9.10 is unfortunately very poor indeed by comparison.

Picture quality in playback (compared to media playback picture quality in other apps on the same machine) is disappointing, the vital (for watching DVB-T) "Minimal" mode (just the picture, all controls and toolbars etc removed) is no more and all of the advanced configuration options are no longer present.

Thankfully, since DVB-T playback is important to me, I have discovered that is it possible to obtain excellent DVB-T playback using VLC.

Notes I made earlier:

First, create a channels list using the scan utility:

anthony@riverside:~$ scan /usr/share/dvb/dvb-t/uk-EmleyMoor -o zap > .tzap/channels.conf

"-o zap" means "output in zap format".

Then, to run vlc using this channels list:

anthony@riverside:~$ vlc .tzap/channels.conf

Picture quality is superb, better than any other media player that I
have used to date to watch DVB-T.  There is a minimal mode, similar to
that which Kaffeine used to have which has now been removed, accessible
from the View menu.

Changing channels is done by View > Playlist.

Based on (expanded a bit to provide more detail):

[http://blog.lynxworks.eu/20090814/watch-tv-with-vlc-and-a-freecom-dvb-t-stick](http://blog.lynxworks.eu/20090814/watch-tv-with-vlc-and-a-freecom-dvb-t-stick)

---

