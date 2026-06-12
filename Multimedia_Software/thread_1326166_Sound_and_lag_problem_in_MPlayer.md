---
title: "Sound and lag problem in MPlayer"
date: 2009-11-14
forum: Multimedia Software
---

### Post by Raff1 on 2009-11-14
I am running Ubuntu 9.04 and recently installed MPlayer in order to see certain webstreams on the web with Firefox. I opened my streams with a Totem-plugin for Firefox earlier, but everything did not work:

Webstreams which *worked*:
- [http://www1.nrk.no/nett-tv/](http://www1.nrk.no/nett-tv/)
- [http://dagskra.ruv.is/ras1/](http://dagskra.ruv.is/ras1/) (internet radio)
Webstreams which *did not work*:
- [http://dagskra.ruv.is/sjonvarpid/](http://dagskra.ruv.is/sjonvarpid/)
After installing MPlayer and MPlayer Firefox plugin I got the same working status as displayed over, except that *none* of them had sound! Even opening an .mp3 file on my computer with MPlayer yealded no sound. And for [http://www1.nrk.no/nett-tv/](http://www1.nrk.no/nett-tv/) the videostream was very laggy. (As for [http://dagskra.ruv.is/ras1/](http://dagskra.ruv.is/ras1/) I have no idea about any lag because its sound only and currently muted.)

So what should I do in order to get sound work at all with MPlayer? Can I get rid of the lag-problem? How do I switch between using Totem and MPlayer? I was not able to do that in Tools > Manage content plug-ins, afaik.

The problem I initially had with [http://dagskra.ruv.is/sjonvarpid/]("http://dagskra.ruv.is/sjonvarpid/was") was that Totem complained about missing html/text decoder, which I understand is an adress parsing incapability(?). (And how to fix that?)

This is a snapshot from about : Plugins in Firefox (I hope this is the concerned section):

**Windows Media Player Plug-in**

 File name:  mplayerplug-in-wmp.so [mplayerplug-in]("http://mplayerplug-in.sourceforge.net/") 3.55

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/") 
JavaScript Enabled and Using GTK2 Widgets

[IMG]http://folk.ntnu.no/%7Ehrafnmar/bilder/plugins.jpg[/IMG]


I really appreciate any help! :D

---

### Post by Raff1 on 2009-11-14
I switched to Gnome MPlayer and the lag-problem disappeared. I still got no sound though, even on files on my computer. I still get the visual from local videos. This time [http://dagskra.ruv.is/sjonvarpid/](http://dagskra.ruv.is/sjonvarpid/) freezes at "Connecting" everytime I try. And [http://www.apple.com/trailers/](http://www.apple.com/trailers/) goes freaky every time I start playing a trailer, by jumping between play and pause all the time.

I followed part 2/5 of [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I have also ticked the "Software Volume Control" box in Gnome MPlayer options.

---

### Post by Raff1 on 2009-11-14
I managed to switch between Totem and Gnome (Gekko) MPlayer, but since Totem don't support the streams I want to play I need to get the problem with the sound in Gnome MPlayer fixed. Nothing I have so far have made [http://dagskra.ruv.is/sjonvarpid/]("http://dagskra.ruv.is/sjonvarpid/was") or [http://www.apple.com/trailers/](http://www.apple.com/trailers/) working at all. I have not been able to stream them from URL without going through Firefox either.

---

### Post by Raff1 on 2009-11-14
Okey! I finally got the sound working by changing the sound output in MPlayer from pulseaudio to alsa (or even oss). But I still don't seem to be able to stream x-ms-asf and .mov :-(

Some hints on what codecs I might be lacking? I thought I had it all covered, but apparantly not.

---

### Post by andrew.46 on 2009-11-14
Hi Raffl,

> **Raff1 said:**
>  But I still don't seem to be able to stream x-ms-asf and .mov :-(

Do you have specific examples of these streams that are still failing?

Andrew

---

### Post by Raff1 on 2009-11-15
Thanks for your reply, Andrew!

I actually tried the procedures suggested in [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) on my laptop with freshly installed Ubuntu 9.10 as well, and there I have similar problems.

There the following streams are troublesome; they start buffering until 0.02 % and jumps between play and pause, and resets the buffering, and starts the cycle all over again:

[http://dagskra.ruv.is/sjonvarpid/streymi/beint/?29](http://dagskra.ruv.is/sjonvarpid/streymi/beint/?29)
[http://dagskra.ruv.is/ras1/streymi/beint/?55](http://dagskra.ruv.is/ras1/streymi/beint/?55)

The first one is a video stream, while the second is sound only.
Opening these streams directly in Gnome MPLayer with File > Open Location yealds the same results. And then I get spammed with "Media Change - Stream from http://dagaskra.ruv.is/..." pop-up messages in the right upper corner. Minutes after I still get these messages. :p I just went into top and killed the notifier.

On my laptop with 9.10 I can watch the trailers at [http://www.apple.com/trailers/](http://www.apple.com/trailers/) but not in my PC with 9.04. For the examples listed above, I get the radio stream working on 9.04 but not the video stream from [http://dagskra.ruv.is/sjonvarpid/streymi/beint/?29](http://dagskra.ruv.is/sjonvarpid/streymi/beint/?29)

During the How-To on the top of this post I got these errors for my 9.10 laptop, but I don't know if thats relevant:
```
E: Couldn't find package libflash-mozplugin #(remove attempt)
E: Couldn't find package liblame0 #(install attempt)
``` I didn't get those on my 9.04 PC.

I really hope this made things clearer, rather than adding an extra element of confusion! Just tell me if somethings not clear.

Regards,
Raff1

---

### Post by andrew.46 on 2009-11-16
Hi Raffl,

I had mixed success with these streams:

> **Raff1 said:**
> 
[http://dagskra.ruv.is/sjonvarpid/streymi/beint/?29](http://dagskra.ruv.is/sjonvarpid/streymi/beint/?29)

This stream I could not raise with any software at my disposal which was more than a little disappointing. I suspect the elaborate movement of urls from this address could be part of the problem but I would welcome input from others on this forum.

> [http://dagskra.ruv.is/ras1/streymi/beint/?55](http://dagskra.ruv.is/ras1/streymi/beint/?55)

This stream was less troublesome, as you have experienced yourself, particularly when the *real* address is used:

mms://http.0.muli.rs.ruv.is/ras1.ruv.is?MSWMExt=.asf 

So for these streams I am not sure if there is a ready answer...

Andrew

---

### Post by Raff1 on 2009-11-16
> **andrew.46 said:**
> 

This stream was less troublesome, as you have experienced yourself, particularly when the *real* address is used:

mms://http.0.muli.rs.ruv.is/ras1.ruv.is?MSWMExt=.asf 



So the addresses are hidden? How did you extract the real address of the radio stream? :) But that wasn't possible for the video stream then...

---

### Post by andrew.46 on 2009-11-17
Hi Raffl,

> **Raff1 said:**
> How did you extract the real address of the radio stream? :) But that wasn't possible for the video stream then...

I have never setup streaming media to play from a website so I am not entirely sure of the mechanics of the addresses. But to find the direct addresses usually it is enough to feed the original url to vlc and let vlc sift out the real address or use MPlayer with the syntax:
```

mplayer -playlist stream_address
```

although this failed with both of the streams you posted.

Andrew

---

### Post by Raff1 on 2009-11-18
Thanks for your help Andrew! Seems I will have to investigate how I made the internet radio channel work properly on my 9.04.

I still can't get [http://www.apple.com/trailers/](http://www.apple.com/trailers/) to work on my 9.04 install. Someone have any suggestion on what kind of player or codecs should I try? Anyone who can provide me with a direct url to any of those streams, so I can test directly without FF?

Raff1

---

### Post by andrew.46 on 2009-11-18
Hi Raffl,

> **Raff1 said:**
> I still can't get [http://www.apple.com/trailers/](http://www.apple.com/trailers/) to work on my 9.04 install. Someone have any suggestion on what kind of player or codecs should I try?

These days something with Quicktime emulation is required. Firefox + the gecko-mediaplayer plugin work for me, screenshot attached.

Andrew

---

