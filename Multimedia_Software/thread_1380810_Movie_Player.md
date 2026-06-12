---
title: "Movie Player"
date: 2010-01-14
forum: Multimedia Software
---

### Post by nishant.singh28 on 2010-01-14
I'm a Movie Junkie. I have a collection of 720p movies, encoded in H264 format. I watch  lots and lots of movies. But i have a problem. I'm not happy with any of the movie players I tried in Ubuntu 9.10. Here's a list:

Movie Player(Totem): Too basic, no custom keyboard shortcuts.

VLC: Subtitles font and size not customisable, some formats suffer badly.

Mplayer and its frontends like SMPlayer: Almost perfect but gets stuck while playing heavy files, Gets stuck while seeking-a big problem.

Currently I use SMPlayer. It is fine as I said but the seeking and heavy file playing problems are too irritating. I used to use TheKMPlayer in Windows. I don't want to use Wine. Please help me out.

---

### Post by Yellow Pasque on 2010-01-14
Try something xine-based, like kaffeine or dragon player.

---

### Post by nishant.singh28 on 2010-01-14
> **Temüjin said:**
> Try something xine-based, like kaffeine or dragon player.
Never figured out how to use Kaffeine. Did not like Dragon Player. Lemme try Kaffeine again though. Thanks for ur advice though :).

---

### Post by nishant.singh28 on 2010-01-14
> **nishant.singh28 said:**
> Never figured out how to use Kaffeine. Did not like Dragon Player. Lemme try Kaffeine again though. Thanks for ur advice though :).
OK, I tried Kaffeine. It seemed OK but I did not figure out a way to change the output driver. Until I do that, I won't have Video Output. I can hear what's going on but not see. The window is transparent. I tried Gxine but its settings are too rudimentary as far as UI is concerned. Its seek option sucks big time and it did not load subtitles. Moreover, it does not have an option to remember last playback position. SO now what?

---

### Post by Yellow Pasque on 2010-01-14
INstall xine-ui and configure your video output settings there.

---

### Post by nishant.singh28 on 2010-01-14
> **Temüjin said:**
> INstall xine-ui and configure your video output settings there.
Video works in xine ui but not in Kaffeine

---

### Post by nishant.singh28 on 2010-01-14
> **nishant.singh28 said:**
> Video works in xine ui but not in Kaffeine
Can someone tell me why smplayer gets stuck while seeking?

---

### Post by nishant.singh28 on 2010-01-14
Bump!!!

---

### Post by rvm4000 on 2010-01-14
> **nishant.singh28 said:**
> Mplayer and its frontends like SMPlayer: Almost perfect but gets stuck while playing heavy files, Gets stuck while seeking-a big problem.

This is a known problem. Change the audio driver from alsa to pulse in preferences -> general -> audio and seeking will work again.

---

### Post by nishant.singh28 on 2010-01-14
> **rvm4000 said:**
> This is a known problem. Change the audio driver from alsa to pulse in preferences -> general -> audio and seeking will work again.
Hehe!!! Didn't know such a big problem could be because of just one setting. Thanks. Any other suggestions for the lightest possible run?

---

### Post by nishant.singh28 on 2010-01-14
And also why the fullscreen doesn't cover the 2nd panel by default? I've to Alt-Tab to it again to cover the 2nd panel. Any answers?

---

### Post by rvm4000 on 2010-01-14
> **nishant.singh28 said:**
> Hehe!!! Didn't know such a big problem could be because of just one setting. Thanks. Any other suggestions for the lightest possible run?

Well, I don't know exactly the problem you have. Anyway I can say that for mp4 and mov files is recommended to set the cache for files to 0. Otherwise they could play very bad.

---

### Post by nishant.singh28 on 2010-01-15
Thanks. But what about the 2nd panel not being covered automatically?

---

### Post by rvm4000 on 2010-01-15
I don't know, maybe you need to adjust the "monitor aspect" in preferences -> advanced?

---

### Post by nishant.singh28 on 2010-01-15
> **rvm4000 said:**
> I don't know, maybe you need to adjust the "monitor aspect" in preferences -> advanced?
Tried it. Didn't work. It has problems in the sense the entire output is shifted
See for yourself what I mean.The control bar does not appear fully in the 1st. The 2nd screenshot is after I alt-tabbed to it again as I said

---

### Post by rvm4000 on 2010-01-15
I see...

Actually I didn't experience that problem, fullscreen works ok for me in Ubuntu 9.10.

Do you have the "desktop effects" enabled?

---

### Post by nishant.singh28 on 2010-01-15
With a 512 MB ATI HD4570 graphics card?? Obviously yes :).

---

### Post by nishant.singh28 on 2010-01-15
And the fullscreen covers one of the 2 panels fine. The one with the task switcher gets covered whether it's on top or bottom. The other panel doesn't cover.

---

### Post by rvm4000 on 2010-01-16
Does the problem still happen if you disable the desktop effects?

---

### Post by nishant.singh28 on 2010-01-16
I'm not checking that. I'd rather Alt-Tab a bit rather than disable and reenabe the effects because reenabling effects calls for a reboot on my system. Sorry :).

---

### Post by rvm4000 on 2010-01-16
Well, all I can say is that fullscreen is working ok for me in Ubuntu 9.10 (using smplayer 0.6.8+SVN-r3392), as you can see in this video:

[http://www.youtube.com/watch?v=gL54mBzAI5Y](http://www.youtube.com/watch?v=gL54mBzAI5Y)

---

### Post by nishant.singh28 on 2010-01-16
No probs man. Don't worry about it. It's nothing too serious. This started happening after I changed video settings to direct render. That helps me watch heavy videos even while doing a CPU intensive job. BTW, how did you record your desktop so nicely? I never managed to get recordmydesktop or istanbul to work properly. Very choppy video quality. My system simply hung up in Istanbul.

---

### Post by nishant.singh28 on 2010-01-16
And considering that seeking is no problem any more, I simply have to click once on the playing window to go proper fullscreen.

---

### Post by nishant.singh28 on 2010-01-18
Okay. Turning off effects cleared out fullscreen problem. But the player itself did not work . Audio lag, nonresponsiveness....

---

### Post by nishant.singh28 on 2010-01-18
OK. So after I reenabled the desktop effects, the fullscreen problem reappeared.

---

### Post by littlepeon on 2010-01-18
well the 2 best players out there (regardless of o.s. platform) are VLC and MPlayer.  so if you have problems/issues with them, everything else is (imho) crap.

you can google for alternate players but the top 5 are: vlc, mplayer, totem player (which covers any gstreamer variants), xine, and kaffine.

that is basically it.

(there are dvd only players like ogle and lindvd)

---

### Post by nishant.singh28 on 2010-01-19
I know. This is now a thread for troubleshooting SMPlayer.

---

### Post by nishant.singh28 on 2010-01-25
I don't know what I did exactly but I fiddled around in the Workaround Section of ccsm and the fullscreen is good...

---

