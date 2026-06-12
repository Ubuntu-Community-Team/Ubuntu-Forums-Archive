---
title: "vlc and vdpau"
date: 2014-06-21
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2014-06-21
I am wondering why all Ubuntu builds of vlc >= 2.1.2 (repo & a few ppas I checked) have no vdpau support while it has been available since vlc 2.1.2? The box in Preferences > Input/Codecs > Hardware decoding shows only automatic, disable and vaapi even in Trusty. But compiling from source there is an extra entry for vdpau. See screen shot for vlc 2.1.4.  

I can confirm that it works on supported graphic driver: AMD with r600 open driver, Nvidia with the blob and Intel i965 with libvdpau-va-gl for supported cards(though can use vaapi in this case).

---

### Post by mc4man on 2014-06-21
Several reasons, the least of which is vlc's relatively poor track record with hw accel
More to the point is the version of libavcodec, for 2.1.4+ it's libavcodec >= 54.36.0, libav9 in trusty is at libavcodec >= 54.35.0 
For 2.2.0 it's >= 55.26.0 (14.10 should have 55.34.1 but 14.10 is somewhat a dead horse that gets 9 months of beating on.

Overall those with recent hardware don't gain that much anyway, very high br vids here never use more than 5-6% overall. Those with older hw that could really benefit may or may not have good support for vdpau.

I have one trusty install that is on libav10, I may try it there (  slowly working thru adding sources to [here]("https://launchpad.net/~mc3man/+archive/testing4"), though current focus is how  gtk-3.12 is on 14.04

---

### Post by monkeybrain20122 on 2014-06-22
That explains it since I compile against ffmpeg 2.2.3 (2.1.4 in Saucy). I have installed Ubuntu on some machines with weak cpu but decent  graphic cards, I find hardware decoding makes a lot of difference (even  though hw accel for vlc may not be as efficient as mpv or mplayer, but  it is nice to have)

P.S. Another odd thing is some ppa builds don't work with smtube on Trusty. If I set set smtube's player to vlc, choose a video and vlc would open and then crash immediately. Tried it with your ppa [https://bugs.launchpad.net/~mc3man/+archive/trusty-media](https://bugs.launchpad.net/~mc3man/+archive/trusty-media) as well as another with 2.1.4. Haven't tried stock Ubuntu vlc yet. Again no problem with self compile.

---

### Post by Yellow Pasque on 2014-06-22
You can use va-api with a vdpau backend (vpdau-va-driver package). [https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1302012](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1302012)

---

### Post by monkeybrain20122 on 2014-06-22
> **Temüjin said:**
> You can use va-api with a vdpau backend (vpdau-va-driver package). [https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1302012](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1302012)

Since I compile vlc myself I have no problem using either vaapi or vdpau for the appropriate card since 13.10 (vlc2.1.2). I was just wondering why it doesn't work with Ubuntu builds and mc4man's explanation makes sense.

---

### Post by mc4man on 2014-06-22
> **monkeybrain20122 said:**
> 

P.S. Another odd thing is some ppa builds don't work with smtube on Trusty. If I set set smtube's player to vlc, choose a video and vlc would open and then crash immediately. Tried it with your ppa [https://bugs.launchpad.net/~mc3man/+archive/trusty-media](https://bugs.launchpad.net/~mc3man/+archive/trusty-media) as well as another with 2.1.4. Haven't tried stock Ubuntu vlc yet. Again no problem with self compile.
If you have a yt vid that caused you issue let me know. I've seen no issue using vlc as the player for smtube. (normally I use mpv but do ck. all
 Generally check some random & also vevo music vids for tests.
This would be with 2.1.5 & I have 2.2.0 ready to go, just been running for several days to ck. out.

(- the only thing bothering me about 2.2.0 is the auto-resume. While it's a nice feature can't yet find any setting for it like 'always', 'never' or 'ask'

---

### Post by monkeybrain20122 on 2014-06-23
> **mc4man said:**
> If you have a yt vid that caused you issue let me know. I've seen no issue using vlc as the player for smtube. (normally I use mpv but do ck. all
 Generally check some random & also vevo music vids for tests.
This would be with 2.1.5 & I have 2.2.0 ready to go, just been running for several days to ck. out.

(- the only thing bothering me about 2.2.0 is the auto-resume. While it's a nice feature can't yet find any setting for it like 'always', 'never' or 'ask'

Actually I can't play any video on smtube with vlc 2.1.5 from your ppa and 2.1.4 from [https://launchpad.net/~djcj/+archive/vlc-stable](https://launchpad.net/~djcj/+archive/vlc-stable), vlc crashes as soon as it starts, tested in two machines. smtube is installed with the rvm ppa. This is on xubuntu 14.04 if it is relevant. 

I have no problem using vlc with smtube(vlc 2.1.5 is self compiled here) on my own machine.I too normally use mpv with smtube , but that is for my roommate and he prefers vlc.

---

### Post by mc4man on 2014-06-23
> **monkeybrain20122 said:**
> Actually I can't play any video on smtube with vlc 2.1.5 from your ppa and 2.1.4 from [https://launchpad.net/~djcj/+archive/vlc-stable](https://launchpad.net/~djcj/+archive/vlc-stable), vlc crashes as soon as it starts, tested in two machines. smtube is installed with the rvm ppa. This is on xubuntu 14.04 if it is relevant. 

I have no problem using vlc with smtube(vlc 2.1.5 is self compiled here) on my own machine.I too normally use mpv with smtube , but that is for my roommate and he prefers vlc.
No clue, haven't seen any issue here nor has any been forwarded to me.  Maybe I'll try Xubuntu though seems a long shot that that's the problem.

---

