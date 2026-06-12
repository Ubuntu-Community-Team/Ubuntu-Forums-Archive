---
title: "Totem vs. Other Media Players?"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by jharker on 2007-10-18
So, 7.10 Gutsy Gibbon has just come out, and Wired magazine had a [review of the last release candidate](http://www.wired.com/software/softwarereviews/news/2007/10/ubuntu_gutsy).  I noticed in the review that one negative comment stood out for me:> DVD playback was a slightly different story. The Totem media player, Ubuntu's default DVD player, lacked the necessary codecs out of the box, but helpfully offered to fetch them. Unfortunately, even after the codecs were installed, I was unable to get any of my Netflix DVDs to play.

This isn't a new experience, as I was never able to get DVDs to play under either of the previous two versions of Ubuntu using Totem. Luckily, finding and installing the more robust MPlayer DVD player through the Add/Remove programs panel is easy, and DVD playback in MPlayer worked without a hitch.This echoes my own experience: I have never had any luck getting Totem to do the things I want, whether it's playing DVDs, or video in a web browser, or... really, anything.

So my question is, how well does Totem work for you?

And of course the follow-up questions are, [list=1][*]Why hasn't the default install of Totem been fixed up so that it "just works"?[*]If Totem really fails to work as badly as many people have suggested (myself included), why won't the good folks at Ubuntu reconsider replacing it with something else as the default installation?[/list]
I've read other threads on the subject, which include arguments like "Totem fits the Ubuntu HIG", and "Totem's backend (gstreamer) is the future of Linux desktop multimedia, even if it's not there quite yet."  All of these arguments seem to miss the point, which is, *it doesn't do what I (the user) need it to do!*  All the great GUI in the world doesn't help if it has the functionality of a brick.

So, what does Ubuntu plan to do to make multimedia work better "out of the box"?

---

### Post by SmokingGun on 2007-10-18
I like Totem.  Plays DVD's fine after installing libdvdcss, as well as playing all other files i throw at it.  I always change gstreamer Totem to Xine Totem though.  Is the gstreamer version as good as xine now?

---

### Post by Tlon on 2007-10-18
I haven't had too much time to play with it yet, but I've found it a bit buggy.  The slider-bar seek function doesn't seem to work quite right with the DivX movies I've watched with it (I'll try to go, say, to "1:42", it will SAY that it's there, but then kick me back 10 seconds before or after that when I hit play... really annoying for fast-forwarding through intros, commercials, etc.).  Also, audio suddenly died on me last night while I was listening to a playlist.  I wasn't even doing anything on the computer at the time.  One second it was playing, and the next -- POOF! -- nothing.  I actually thought it had to have been mis-encoded audio files until I tried them in Audacious (everything went fine).  Haven't tested DVD yet; will do that when I get home.  I love the full-screen support in Totem, but I'm finding the bugs aggravating.

---

### Post by pbcartwright on 2007-10-18
I have 2 players that work fine for all DVDs that I play. mplayer and vlc . Both can be installed using:
sudo aptitude install mplayer vlc

mplayer will also install all the win32codecs that you will need for almost all theversions of videos.

---

### Post by vambo on 2007-10-18
Totem does just about everything I want. However only with the xine backend. Chucked gstreamer ages ago and have no intention of using it again - yes it was that bad. One day it might manage to play something

---

### Post by Depressed Man on 2007-10-18
Even with libdvdcss installed, Totem (g-streamer) can't play DVDs (for me). It'll play when you insert discs (skipping the menu completly). But if you try "play disc" it says it can't. Though it does work in Totem (xine).

---

### Post by Dr Small on 2007-10-18
I use VLC for everything these days, mainly because it will read my DVD menu's whereas totem would not, but I used to use totem a good bit. Now I just use VLC for music, videos and DVDs. It works great out of the box ;)

---

### Post by jharker on 2007-10-18
I should probably clarify that I'm not asking for help in any way.  I'm a long time Ubuntu user and I know how to get Ubuntu to do what I want.  :)

This thread is mainly to get a sense of how the community feels about the default Totem installation.  If it turns out that enough people feel it doesn't meet their needs, maybe we can implement some change, in the interest of making Ubuntu more user-friendly for beginners and "converts".  IMHO, multimedia is important enough that it really should "just work".

---

### Post by baysbenj on 2007-10-18
I am a recent XP convert.  So far, there are three things that made the transition difficult for me.

1. The video player (which I guess is called Totem) stinks.  The main problem is that the slider bar is very temperamental,  More often then not, if I try to skip ahead in a video, the video will just restart itself.  This occurs both in firefox and when using the player standalone.  I haven't tried this xine other posters have mentioned, I'm going to look into that.

2. Firefox doesn't seem to render all websites correctly.  This is quite frustrating.  I realize this is the wrong forum, but any suggestions on improving my web experience are welcome.

3. Getting compiz to work with my ATI 1650 Pro was a nightmare to say the least.  I'm using XGL, but its a processor hog.

These three things are minimal, but they were enough to deter two of my friends that also gave ubuntu a try.  Also, I'm a computer science grad, so I'd say my willingness to learn new technologies is above average.  If the target audience of ubuntu are people like my parents, then things like video and web browsing need to work out of the box.

---

### Post by FredB on 2007-10-18
I am using VLC + MPlayer 85% of the time. Totem is great for playing some audio files.

---

### Post by poiiop on 2007-10-22
Many has xine for their favorit compared to Gstreamer. For me it's the other way around.

Gstreamer worked just fine, but many said the I should choose Xine instead. Efter installing Xine - sudo aptitude install xine-ui libxine-extracodecs - nothing could be played on Xine. 

I think its because of missing codec etc. I normally play DVD from my harddisk. Xine give me Xine engine error and plugin not available. I had no luck using xine for anything yet, but everything works in Gstreamer.

What am i missing i xine ???

---

