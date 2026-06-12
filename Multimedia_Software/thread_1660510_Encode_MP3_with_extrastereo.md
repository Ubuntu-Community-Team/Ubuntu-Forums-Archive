---
title: "Encode MP3 with extrastereo"
date: 2011-01-05
forum: Multimedia Software
---

### Post by linuxyogi on 2011-01-05
Hi,

Recently I started using the extrastereo filter in mplayer & liked it a lot.

My portable MP3 player has no such option built in (like SRS).

I was just wondering if it is possible to re-encode a MP3 track using mencoder with the extrastereo effect. Tried google but couldn't find anything helpful. If its possible, I will just copy the remastered track to my MP3 player & listen to the track with the extrastereo effect.

Thanks in advance.

---

### Post by inobe on 2011-01-05
audacity has plugins/ affects, one is extra stereo and not extrastereo.

---

### Post by cchhrriiss121212 on 2011-01-05
Quoth [mplayerhq]("http://www.mplayerhq.hu/DOCS/HTML/en/advaudio-channels.html"):
> Mono sounds a lot better when played through two speakers - especially when using headphones. Audio files that truly have one channel are automatically played through two speakers; unfortunately, most files with mono sound are actually encoded as stereo with one channel silent. The easiest and most foolproof way to make both speakers output the same audio is the extrastereo filter: 
Do you have a lot of mono mp3s? This effect will only make left and right channels the same, which defeats the purpose of nearly all stereo recordings. Is that what you want to do?

If you really do want this for whatever reason, you could do it manually in Audacity or by using sound recorder to capture mplayer's output.

---

### Post by linuxyogi on 2011-01-06
> **cchhrriiss121212 said:**
> Quoth [mplayerhq]("http://www.mplayerhq.hu/DOCS/HTML/en/advaudio-channels.html"):

Do you have a lot of mono mp3s? This effect will only make left and right channels the same, which defeats the purpose of nearly all stereo recordings. Is that what you want to do?

.

No. 

I want some filter or plugin similar to SRS Wow effect in WMP or Trusurround/Dolby Headphone in Power Dvd.

mplayer's extrastereo is what I have found so far which somewhat sounds like srs wow of WMP.

[COLOR=Red]**Now, the next step is to find a way to encode a mp3 with that effect.**[/COLOR]

After reading what you wrote/quoted, I played a stereo mp3 just to see if both channels are sounding the same. But they don't. I can clearly hear different instruments playing in the L & R channels. 

Therefore the extrastereo filter doesn't make a stereo track sound like mono. Try it yourself, just to be sure.

They (at mplayerhq), are talking about how to make a mono track sound better, but that's  a different issue.

---

### Post by inobe on 2011-01-06
i took a track and added 0.2 echo delay and 0.4 decay, then amplified by 0.8 and the results were just freakn amazing.

audacity will convert to that setting.

---

### Post by linuxyogi on 2011-01-06
> **inobe said:**
> i took a track and added 0.2 echo delay and 0.4 decay, then amplified by 0.8 and the results were just freakn amazing.

audacity will convert to that setting.

Thanks for sharing those values.

I am emphasizing on extrastereo because the values there are already set by experts. Creating these effects involves very complex combination of filters.Once I become sure of the fact that there is no way implementing extrastereo in the encoding process I will try the audacity way.

Thanks again.

---

### Post by inobe on 2011-01-06
i found some interesting stuff for you, i too was looking for such an affect a few years back.

[http://forum.audacityteam.org/viewtopic.php?f=16&t=44043](http://forum.audacityteam.org/viewtopic.php?f=16&t=44043)

---

### Post by linuxyogi on 2011-01-06
> **inobe said:**
> i found some interesting stuff for you, i too was looking for such an affect a few years back.

[http://forum.audacityteam.org/viewtopic.php?f=16&t=44043](http://forum.audacityteam.org/viewtopic.php?f=16&t=44043)

Please tell me how to complete the 6th step.

"6. Mix and render tracks 1 and 2 into a single track. "

Tracks >> Mix & Render  Is that it?

---

