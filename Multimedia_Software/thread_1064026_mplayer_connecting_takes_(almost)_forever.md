---
title: "mplayer connecting takes (almost) forever"
date: 2009-02-08
forum: Multimedia Software
---

### Post by norkbork on 2009-02-08
I just installed 8.10 amd64 and most things work fine but then I tried to get multimedia working and followed the ["Comprehensive Multimedia & Video Howto"]("http://ubuntuforums.org/showthread.php?t=766683")
to the letter. Now, streaming video is problematic with mplayer for some reason (flash works fine but I must disable flashblock completely on some sites due to an evidently known cross-platform bug). The problem is that playback takes an extremely long time to start ("Connecting to server..." is shown) - I've tried reducing the cache and also the percentage of a file that must be cached before playback starts. That did, however, not improve anything and I don't know what to try next - the site I've tested is the Finnish National Broadcasting Company's service (e.g. [news broadcast here]("http://areena.yle.fi/toista?id=1831699")) and it starts almost immediately in Windows but in Linux I must wait several minutes (but once it has started, there are no problems). I've tried both alternatives suggested in the guide, i.e. gecko media player and mplayerplug-in but mplayerplug-in works better (gecko has difficulties switching back from fullscreen). I remember that many other sites somehow (probably by checking user-agent) refuse to work completely in Linux but that worked fine with my previous installation (interestingly, they even suggest mplayer for Linux users). So what should I do to fix this problem? Is there some more cache setting I must adjust? Or could it be something else?

Edit: In my latest attempts, it has begun to take really forever - at least 30 min with nothing happening.

---

### Post by andrew.46 on 2009-02-08
Hi,

I am unable to play the stream with the svn MPlayer and I have posted a query on MPlayer-users so wiser heads than mine can ponder:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-February/075882.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-February/075882.html)

Andrew

---

### Post by norkbork on 2009-02-09
Thanks for doing that! Now, however, I've managed to get it to work with vlc. I decided to reinstall my system completely due to other reasons so I have very little idea of the cause since many things can be different and I'm a little bit reluctant to try with mplayer now that I've gotten it to work. I must add that I was really impressed with how the installation could be launched from firefox when the plugin wasn't there yet.

---

### Post by andrew.46 on 2009-02-10
Hi,

Well if it works with vlc I reckon you should stick with vlc :-). I am a little peeved that my favoured program (MPlayer) has failed where vlc has succeeded! I might have to have a look at vlc which I admit with a little shame I have not really ever done.

Andrew

**Edit:** Mind you I compiled vlc from source, which is not for the faint-hearted, and I still could not play the stream!

---

