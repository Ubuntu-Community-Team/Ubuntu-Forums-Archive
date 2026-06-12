---
title: "Myth 0.22-fixes branch jya vs mythbuntu"
date: 2009-11-14
forum: Mythbuntu
---

### Post by utar on 2009-11-14
Hi


"Quick" question.

I was just wondering the difference between using mythbuntu's daily builds:

[http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)

Versus jya's builds of the fixes branch:

[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

I used jya's 0.21 repository and was very happy with it, but as a matter of interest I just wondered what the difference was, as I assume both are compiled off the same source?


Cheers.

---

### Post by jyavenard on 2009-11-14
I posted an entry on the differences.

[http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/7_MythTV_0.22-fixes_Released_!.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/7_MythTV_0.22-fixes_Released_!.html)

Basically, extra support for Studio RGB level and TV-HD colorspace, as well as complete new audio code: much easier to set up and provide extra features.

Additionally, the mythtv repository in this repo don't have a hard dependency on nvidia drivers 185.18.36 ; you can use any drivers with it (180.60, 185.18.36, 190.42)..

The mythbuntu automatic weekly build is now also using the same external libvdpau.

If you want to upgrade, make sure you read the following:
[http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html).

---

### Post by xinix on 2009-11-14
> **jyavenard said:**
>  as well as complete new audio code: much easier to set up and provide extra features.

For me this was a big factor in choosing which one to use.  Playback stutters when I watch 720p recordings if I set the audio channels to 5.1 using JYA's repo.  On the other hand, playback is just fine if I use the mythbuntu repo.

---

### Post by jyavenard on 2009-11-15
> **xinix said:**
> For me this was a big factor in choosing which one to use.  Playback stutters when I watch 720p recordings if I set the audio channels to 5.1 using JYA's repo.  On the other hand, playback is just fine if I use the mythbuntu repo.

If your machine is too slow ; there are plenty of option to reduce CPU load.

First try overriding the samplerate conversion quality ; change from Best to Good/Normal ; this will reduce CPU usage a fair bit.

If that still doesn't help. completely disable the upmixing.

When doing so, performance should be the same as with old audio-code (if not better)

You will want to find out the right settings, because with 0.23 that code is in..

---

### Post by utar on 2009-11-15
@jyavenard: Many thanks for the clarification.


Utar

---

### Post by xinix on 2009-11-15
My cpu (AMD 3800+ x2) may be a bit underpowered but audio and playback work well under the Mythbuntu pakages.  I used to use the JYA packages and disabling upmixing did the trick with 0.21 (backported code right?).  Now with 0.22 I have very different end user experiences when comparing the Mythbuntu and JYA packages with the same settings.  At least I think they are the same settings.  If you can help me figure out the right settings to get me back on track to use JYA packages that would be great.  Like you said the difference is what will be in 0.23.

I'm attaching screenshots of the audio setup screen and a description of my experience with both packages.

With Mythbuntu's packages; I can set max audio channels to 5.1 and get smooth playback.  I really don't need upmixing, but it is nice.  It's  AC3 passthrough that makes a difference for me.  With this package I get AC3 passthrough when the max audio channels is set to 5.1 or Stereo.  What this means in terms of my watching experience is this:  I can have upmixing for stereo shows if I want it,  but if a show has an AC3 track it plays that audio track.  This is the behaviour I want.

With JYA's packages;  I do not get smooth playback with 720p recordings (shows on Fox) when max audio channels is set to 5.1.  I do get smooth play back if it is set to stereo, but I do not get AC3 passthrough with this setting.  I only get AC3 passthrough when it is set to 5.1. 

How do I know when I am  and am not getting AC3 passthrough?  My audio receiver has a red light on its display that lights up when it is getting AC3 audio.  It also tells me the number of channels in the track, eg 3/2/1 or 2/0. 

It would be nice to sort out what settings I need to change in order to have AC3 passthrough without needing to set max audio channels to 5.1.

---

