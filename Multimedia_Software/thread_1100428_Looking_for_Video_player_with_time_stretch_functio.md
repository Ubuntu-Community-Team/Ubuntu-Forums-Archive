---
title: "Looking for Video player with time stretch function"
date: 2009-03-19
forum: Multimedia Software
---

### Post by Piilen on 2009-03-19
Hi, I'm looking for a video player that can run the video faster than normal speed (or slower) without the sound getting "Mickie Mouse" like.
On Windows I've found "The KMPlayer" or PowerDVD that both provide this.
I've googled this and found this wikipedia page:
[http://en.wikipedia.org/wiki/Comparison_of_media_players](http://en.wikipedia.org/wiki/Comparison_of_media_players)
according to that the following players should be capable of time strech: Kaffeine, MPlayer, SMPlayer and VLC.

I've tried all of them but can't find any options for faster playback with correct sound pitch.

Can anybody point in the right direction here?

The nearest I came was that in 2004 there was a plugin to kaffeine called Stretch plugin, but it seems to be missing from their website today?

best regards 
Morten

---

### Post by lovinglinux on 2009-03-19
I don't get it. If you want to speed up the video without speeding up the sound they will become out of sync.

Smplayer can easily speed up the video, but I'm not sure if it can change the sound speed.

---

### Post by Piilen on 2009-03-19
Hi lovinglinux,
It needs to speed up the sound as well as the video, but if that's all it does then you end up with what I call Mickie Mouse voices.
So the program also need to keep the voice pitch constant so it sounds the same (only faster).
The Windows program I mentioned can do it but I can't find a linux version that can do it.
It involves some math that I can't understand, but the end result is quite ok if to save some time listening to say a podcast.
You can read about the process here:
[http://en.wikipedia.org/wiki/Audio_timescale-pitch_modification](http://en.wikipedia.org/wiki/Audio_timescale-pitch_modification)

---

### Post by lovinglinux on 2009-03-19
> **Piilen said:**
> Hi lovinglinux,
It needs to speed up the sound as well as the video, but if that's all it does then you end up with what I call Mickie Mouse voices.
So the program also need to keep the voice pitch constant so it sounds the same (only faster).
The Windows program I mentioned can do it but I can't find a linux version that can do it.
It involves some math that I can't understand, but the end result is quite ok if to save some time listening to say a podcast.
You can read about the process here:
[http://en.wikipedia.org/wiki/Audio_timescale-pitch_modification](http://en.wikipedia.org/wiki/Audio_timescale-pitch_modification)

Ok. Now I understand. I call those "Duck Donald" voices :D

Unfortunately, I can help you. Never tried this before. Maybe this will help you:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2007-December/070549.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2007-December/070549.html)

BTW, KMPlayer is really one of the best players for Windows I have used before. I liked GOM player too.

---

### Post by rvm4000 on 2009-03-19
> **Piilen said:**
> Hi, I'm looking for a video player that can run the video faster than normal speed (or slower) without the sound getting "Mickie Mouse" like.
On Windows I've found "The KMPlayer" or PowerDVD that both provide this.
I've googled this and found this wikipedia page:
[http://en.wikipedia.org/wiki/Comparison_of_media_players](http://en.wikipedia.org/wiki/Comparison_of_media_players)
according to that the following players should be capable of time strech: Kaffeine, MPlayer, SMPlayer and VLC.

I've tried all of them but can't find any options for faster playback with correct sound pitch.

In smplayer: Preferences -> General -> Audio -> High speed playback without altering pitch. (If you don't have that option, update your smplayer: [http://smplayer.berlios.de/downloads.php](http://smplayer.berlios.de/downloads.php))

Notice that you'll also need a recent version of mplayer. The one included in ubuntu (1.0rc2) won't work. You can find a newer version here (packages for hardy and intrepid): [https://launchpad.net/~rvm/+archive/ppa/](https://launchpad.net/~rvm/+archive/ppa/)

---

### Post by lovinglinux on 2009-03-19
> **rvm4000 said:**
> In smplayer: Preferences -> General -> Audio -> High speed playback without altering pitch. (If you don't have that option, update your smplayer: [http://smplayer.berlios.de/downloads.php](http://smplayer.berlios.de/downloads.php))

Notice that you'll also need a recent version of mplayer. The one included in ubuntu (1.0rc2) won't work. You can find a newer version here (packages for hardy and intrepid): [https://launchpad.net/~rvm/+archive/ppa/](https://launchpad.net/~rvm/+archive/ppa/)

Cool. It works.

---

### Post by Piilen on 2009-03-20
This is absolutely great !
Thanks al lot rvm4000
Morten

---

### Post by Raphae1 on 2009-06-11
xmms2 has a plugin for sound stretching as well.

---

### Post by synd7 on 2009-06-11
In VLC: Tools -> Preferences -> Audio -> Filters and theres an option to scale audio in sync with playback rate

---

### Post by Piilen on 2009-06-11
> **synd7 said:**
> In VLC: Tools -> Preferences -> Audio -> Filters and theres an option to scale audio in sync with playback rate

Hi synd7, this is absolutely fabulous - but I can't understand why it's not the default setting?
Never mind !
Great - VLC is better with subtitles in .ts files from DVB-T transmissions here in Denmark. My other choice (SMPlayer) can't see the subtitles that are embedded in the files.

Thanks very much for the tip!
Morten:popcorn:

---

### Post by george.henne on 2009-06-11
> **synd7 said:**
> In VLC: Tools -> Preferences -> Audio -> Filters and theres an option to scale audio in sync with playback rate

To be clear, at least on my version:

* open VLC
* go to Tools -> Preferences (Ctrl-P)
* in the bottom left corner, under 'Show settings', click the All button
* on the left menu, double-click Audio to expose the sub-menus
* click to select Filters
* On the right, check the checkbox labeled 'Scale audio tempo in sync with playback rate'
* Click save

Anyway, the reason I chimed it is that there is a feature to the alteration of playback speed that eluded me for a while.  While the faster and slower buttons are easy to find, they alter the speed by certain preset values.  If you want a more subtle tweak to the speed, right-click the speed indicator along the bottom status bar for a speed slide bar.

For watching movies, I like to slide it to 1.19x. :D

---

### Post by Raphae1 on 2009-06-11
> **Raphae1 said:**
> xmms2 has a plugin for sound stretching as well.

I'm sorry, but xmms2 doesn't seem to have the sndstretch plugin
(xmms did). The program that does it today is called audacious.

---

### Post by rvm4000 on 2009-06-11
> **Piilen said:**
> Great - VLC is better with subtitles in .ts files from DVB-T transmissions here in Denmark. My other choice (SMPlayer) can't see the subtitles that are embedded in the files.

I'm afraid mplayer doesn't support dvb-t subtitles. There was a [patch](http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-February/060659.html) sent to mplayer-dev-eng, but I think it was never committed.

I might try to add this patch in the future to my mplayer packages, if it still works...

---

### Post by james3880 on 2010-04-13
hi sind7, also wanted to thank you for the info on vlc time stretching, it's also available in gom, press c and x to slow down and speed up, i think the time stretch is default.
thanks again! james.

---

