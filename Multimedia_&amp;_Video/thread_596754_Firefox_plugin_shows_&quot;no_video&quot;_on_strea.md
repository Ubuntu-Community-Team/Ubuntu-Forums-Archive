---
title: "Firefox plugin shows &quot;no video&quot; on streaming audio"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by rafaelcapanema on 2007-10-29
After upgrading to Gutsy, when I listen to streaming audio content on Firefox, I get this black square with the words "(no video)" on it (see the attached screenshot). The sound plays perfectly, but I get no controls like play, pause, stop and volume. This is really annoying. When streaming video fails, I also get the black square.

Any ideas?

---

### Post by rafaelcapanema on 2007-10-30
bump!

---

### Post by Roasted on 2007-11-02
Bump to help a brotha out. Plus I need the exact same question answered...

---

### Post by Neon Lights on 2007-11-02
Yup, same here.

---

### Post by NifNif_as on 2007-11-06
Can anyone help us? I also have the same problem. After upgrade to Gutsy Firefox gives (no video) message on video or audio files with no control toolbar.

---

### Post by vpavel on 2008-03-18
same problem

---

### Post by ItalOz on 2008-03-18
same but my video is [COLOR="Green"]GREEN[/COLOR] (nice variant uh?)
I think it should be a problem of codecs, as a matter of fact I could not play the videos I downloaded with Totem so I installed Mplayer, I followed the "how to" of this forum [http://ubuntuforums.org/showthread.php?t=661833]("http://ubuntuforums.org/showthread.php?t=661833")
in particular the PART 2/5, STREAMING WITH FIREFOX--
Now I see the videos with Mplayer if I download them but if I try to play them embedded into Firefox I get the [COLOR="Green"]GREEN square[/COLOR] I told you about.

So I guess I am stuck with you guys... BUMP!

---

### Post by wolfen69 on 2008-03-18
> Now I see the videos with Mplayer if I download them but if I try to play them embedded into Firefox I get the GREEN square I told you about.
try removing  totem-mozilla (or regular totem if you dont have the plugin) and installing mozilla-mplayer. totem can cause conflicts. all i have is mplayer(and plugin) and vlc, and i can play any format, web or otherwise.

unless the upgrade to gutsy broke something,(next time keep in mind a fresh install) this should work. i have tried it on several pc's.

---

### Post by Roasted on 2008-03-19
> **wolfen69 said:**
> try removing  totem-mozilla (or regular totem if you dont have the plugin) and installing mozilla-mplayer. totem can cause conflicts. all i have is mplayer(and plugin) and vlc, and i can play any format, web or otherwise.

unless the upgrade to gutsy broke something,(next time keep in mind a fresh install) this should work. i have tried it on several pc's.

Question for you. On youtube, can you full screen videos? When I full screen them, it's unusually slow, choppy, skips a lot, etc. However if I just keep it at the default setting embedded on the page, it plays absolutely fine.

When I get home I'll try removing totem and see if that helps. Until then, what's your experience with youtube?

---

### Post by Roasted on 2008-03-20
I tried with totem-mozilla installed (mplayer-mozilla removed) and vice versa.

Both yield same results (no video) white text black background.

However, SOME web sites still play the video after 5-10 seconds of the (no video) screen showing. But, there's no controls, no idea how long the video is, etc.

What am I missing?

---

### Post by mjoethvitnir on 2008-03-28
I really need help with this one too! Anyone?

---

### Post by mjoethvitnir on 2008-03-29
I seemed to have partially fixed this problem by installing the MediaPlayerConnectivity add-on and using MPlayer to launch the streams. It's not flawless but it's working for the time being.

---

### Post by johnmc on 2008-05-04
Problem still persists... having the same problem with hardy. A fix would be nice - substituting totem with mplayer doesn't resolve the problem.

---

### Post by rickyross on 2008-07-09
Hey guys

I think I have the solution! After reading a bit I soon realized the problem wasn't my browser, but indeed the codecs installed. Also, since Internet Explorer was not playing my videos flawlessly. 

What did I do:
1. I Closed my browser(s)

2. Then I opened up the Software module through the control panel and went through it - step by step - deleting all the items remotely related to codecs. Especially things like DivX and the K-Lite Codec Pack.

3. Opened up my firefox (3, version 2 same problem by the way) and surfed to something like filehippo DOT com ([http://www.filehippo.com](http://www.filehippo.com)) and downloaded the latest K-Lite Codec Pack (full). 

4. Installed & from then on, it worked like a charm.

My suspicion is that there is somewhere some conflicting software messing up the browser. Cleaning up before reinstalling and starting from scratch - paying special attention to the previously mentioned software items, should do the trick... At least it did for me!

Curious to find out if it works for you too. Good luck!


Greets,
Rick

---

### Post by rickyross on 2008-07-09
Update... Despite the fact that the video works, now the audio only presents a problem. This only occurs when you skip forward in the video, and the effect is that the video finally plays perfectly - but the audio tracks are missing.

Who knows now? :)

---

### Post by lysalf on 2008-07-23
Well i fixed this exact promblem by removing the mozilla-plugin-vlc. It seems it was the VLC player plugin for my browser that had problems. Now everything is working fine again.

sudo apt-get remove mozilla-plugin-vlc 

should do the trick ;-)

---

### Post by Roasted on 2008-07-23
lysalf - What plugin are you running? mplayer?

---

