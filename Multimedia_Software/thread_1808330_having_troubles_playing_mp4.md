---
title: "having troubles playing mp4"
date: 2011-07-20
forum: Multimedia Software
---

### Post by Yamafae on 2011-07-20
[SIZE=3]Ok. so here is my problem. I cant play mp4 files with dual audio and dual subtitles. I am using a laptop with intel graphics. I've already tried mplayer, vlc, and smplayer. But still the files wont play properly. I been jumping all over the forums reading and trying anything i come up to. What do I need to do? oh btw I am using Ubuntu 10.04. I am a newbie to this kind of thing. so any help would be much appreciated.[/SIZE]

---

### Post by khelben1979 on 2011-07-20
> **Yamafae said:**
> [SIZE=3]"I cant play mp4 files with dual audio and dual subtitles."[/SIZE]

Can you clarify why you need that? And if VLC happen to lack features which aren't supported by VLC, you can always download and install the latest version of VLC [from their homepage]("http://www.videolan.org/vlc/").

---

### Post by SeijiSensei on 2011-07-20
The more pertinent question is what do you mean by "the files won't play properly?"  How about some computer specs or a model number?  If it's running an Atom processor with Intel graphics, you're going to have a very difficult time playing anything in high-definition (720p or 1080p) encoded with H.264.  Changing players won't help much.

@khelben1979
Many videos come with dual audio and dual subtitles, anime titles for one.  If they've been ripped from a DVD, they'll have EN/JP language tracks, and sometimes multiple EN subtitle tracks.

---

### Post by shantiq on 2011-07-22
> **Yamafae said:**
> [SIZE=3]Ok. so here is my problem. I cant play mp4 files with dual audio and dual subtitles. I am using a laptop with intel graphics. I've already tried mplayer, vlc, and smplayer. But still the files wont play properly. I been jumping all over the forums reading and trying anything i come up to. What do I need to do? oh btw I am using Ubuntu 10.04. I am a newbie to this kind of thing. so any help would be much appreciated.[/SIZE]



ok there since you say you are new to this my guess is you have not yet installed the restricted-extras and this could be the reason here


so open your terminal and enter

```
sudo apt-get install ubuntu-restricted-extras
```

or go to your synaptic or software center and do same


I have found often that if that is not installed a lot of things do not connect on the audio/video side    Good Luck:KS

---

