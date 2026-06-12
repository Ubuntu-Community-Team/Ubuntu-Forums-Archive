---
title: "cant play 720p smoothly on netbook"
date: 2012-07-31
forum: Multimedia Software
---

### Post by dioxholster on 2012-07-31
Im using VLC. Usually with windows one will use MPC-HC with special codecs to improve performance but with ubuntu that choice doesnt exist. I tried tweaking VLC settings, like GPU accel. and deblocking; doesnt do much.

---

### Post by GreatDanton on 2012-07-31
Can you post your computer configuration?

Play a little bit with Video settings in Vlc. Try changing the output from default to something else.

---

### Post by TheFu on 2012-07-31
> **dioxholster said:**
> Im using VLC. Usually with windows one will use MPC-HC with special codecs to improve performance but with ubuntu that choice doesnt exist. I tried tweaking VLC settings, like GPU accel. and deblocking; doesnt do much.

Well, there may not be accelerated GPU for your chipset, so the netbook CPU is trying to do everything it can, but simply doesn't have the power.  **I feel your pain** ... seriously.  

I have a netbook (Asus Eee w/ **dual core Intel(R) Atom(TM) CPU N280   @ 1.66GHz**) that can't playback 720p under XBMC without massive stuttering. It is an Lubuntu 10.04 install. The GPU is an **Mobile 945GME Express Integrated Graphics Controller.**

My solution is to use** handbrake** to transcode videos to 592p resolution for smooth playback.  Any higher resolution and the CPU stutters.  DVD resolutions are 480p, so this is still really sharp.

I've heard that Intel GPU drivers are better recently, so perhaps I'll try an OS upgrade to 12.04 - I've done that on other systems and been relatively happy, but if the XBMC box doesn't work one evening, I may not wake up the next morning or get a hot meal again. ;)

---

### Post by miegiel on 2012-07-31
720p is more or less the limit for a linux netbook, I know windows does a little better if you tweak it (but not that much). Some people really know what they're doing when they _en_code 720p vids (so they play on netbooks too), others don't. Some shots are just to much. Pan shots, shots with crowds of moving people or trees with a lot of moving leaves. If it's a 720p news cast (people sitting behind a desk), I just accept a little stutter. If it's a movie or something with more motion, I go find a lower quality version, transcode it or go do/watch something else.

Audio podcasts FTW :lolflag:

---

### Post by dioxholster on 2012-07-31
> **TheFu said:**
> Well, there may not be accelerated GPU for your chipset, so the netbook CPU is trying to do everything it can, but simply doesn't have the power.  **I feel your pain** ... seriously.  

I have a netbook (Asus Eee w/ **dual core Intel(R) Atom(TM) CPU N280   @ 1.66GHz**) that can't playback 720p under XBMC without massive stuttering. It is an Lubuntu 10.04 install. The GPU is an **Mobile 945GME Express Integrated Graphics Controller.**

My solution is to use** handbrake** to transcode videos to 592p resolution for smooth playback.  Any higher resolution and the CPU stutters.  DVD resolutions are 480p, so this is still really sharp.

I've heard that Intel GPU drivers are better recently, so perhaps I'll try an OS upgrade to 12.04 - I've done that on other systems and been relatively happy, but if the XBMC box doesn't work one evening, I may not wake up the next morning or get a hot meal again. ;)

Im on the same boat, asus eee and its a problem because a lot of things are 720p nowadays. Ive accepted that I wont be able to watch youtube in HD but not long ago I used to be able to watch HD videos on that same netbook, it was different file though. Also I found before to my surprise that .ts  1080p videos (uncompressed) played really well with VLC, I think after an upgrade from ubuntu or VLC   has diminished that possibility. So I know that its technically possible to have a netbook play HD with the right file and software.

---

### Post by miegiel on 2012-07-31
> **dioxholster said:**
> Im on the same boat, asus eee and its a problem because a lot of things are 720p nowadays. Ive accepted that I wont be able to watch youtube in HD but not long ago I used to be able to watch HD videos on that same netbook, it was different file though. Also I found before to my surprise that .ts  1080p videos (uncompressed) played really well with VLC, I think after an upgrade from ubuntu or VLC   has diminished that possibility. So I know that its technically possible to have a netbook play HD with the right file and software.

A lot depends on the codes and settings used while encoding the video. Some codecs are very demanding on the CPU or graphics processor while others require much less processing to decode. Obviously an uncompressed video will require minimal processing. While some people are really good at creating compressed vids that don't demand fast CPU's to decode, many encoders go for radical compression or extreme quallity (maybe they think everyone has a quad core CPU).

---

### Post by dioxholster on 2012-08-01
> **miegiel said:**
> A lot depends on the codes and settings used while encoding the video. Some codecs are very demanding on the CPU or graphics processor while others require much less processing to decode. Obviously an uncompressed video will require minimal processing. While some people are really good at creating compressed vids that don't demand fast CPU's to decode, many encoders go for radical compression or extreme quallity (maybe they think everyone has a quad core CPU).

I have a uncompressed 1080i video that it used to play before the summer but now it simply cant without massive stuttering.

---

