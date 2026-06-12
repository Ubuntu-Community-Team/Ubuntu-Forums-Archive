---
title: "any way to add photo to playlist say m3u or pls to play in Audacious ...."
date: 2022-04-24
forum: Multimedia Software
---

### Post by shantiq on 2022-04-24
.... or any player really
Cannot find any way to do this on net ....    any of you have managed this?

&#10122; the items in the playlist are radio stations
&#10123; would ideally want a different cover for each

otherwise it looks a little bleak

[[IMG]https://i.postimg.cc/YjMZ4Cgx/Screenshot-from-2022-04-24-16-35-58.png[/IMG]]("https://postimg.cc/YjMZ4Cgx")

---

### Post by #&amp;thj^% on 2022-04-24
Audacious searches cover arts by their name e.g. 'cover' and 'front'.
Does your folder/file contain such an image?
Otherwise it is probably integrated into the mp3 file.

---

### Post by shantiq on 2022-04-24
[COLOR=#000000]thanks but

&#10122; the items in the playlist are radio stations 

so m3u    not mp3   :)[/COLOR]

---

### Post by Yellow Pasque on 2022-04-24
I've moved on from Audacious to Strawberry. Audacious doesn't see much development these days and Strawberry generally does a better job at finding lyrics and cover art.

---

### Post by #&amp;thj^% on 2022-04-24
> **shantiq said:**
> [COLOR=#000000]thanks but

&#10122; the items in the playlist are radio stations 

so m3u    not mp3   :)[/COLOR]

picky picky :P
VLC can do that then.
easy to add net media or local photo

---

### Post by shantiq on 2022-04-25
> **1fallen said:**
> picky picky :P
VLC can do that then.
easy to add net media or local photo


sorry not sure what you are showing me here; it looks like a cover for an album on an mp3 file
Great band :) by the way 

But what I am trying to do here; is to attach a cover image to each of those radio stations on a pls and/or m3u list so it shows in Audacious or elsewhere which looks thus:

PLS

```
[playlist]
File1=http://radio.stereoscenic.com/asp-h
Title1=Ambient Sleeping Pill
Length1=-1



File2=http://lyd.nrk.no:80/nrk_radio_klassisk_mp3_h
Title2=NRK radio_klassisk Norway
Length2=-1


File3=http://www.radioking.com/play/radio-planeta-occitania
Title3=RADIO PLANÈTA OCCITÀNIA
Length3=-1


File4=http://82.94.205.73/proxy/onlineworldradio?mp=/
Title4=World Hi On Line Radio - Hifi Internet Radio - 320 kbps
Length4=-1


File5=http://68.168.101.146:8417
Title5=Kripalu Bhakti Radio
Length5=-1


File6=http://81.25.96.13:8090
Title6=Radio Krishna Centrale - RKC
Length6=-1


File7=http://amp.cesnet.cz:8000/cro-d-dur-256.ogg
Title7=Czech 256kbps
Length7=-1


File8=http://216.144.255.186:8100/live
Title8=RST Radio Rock Brasil
Length8=-1


File9=http://94.249.254.14:7592/stream
Title9=Krautrock-World
Length9=-1


File10=http://142.44.227.24:10022
Title10=http://beprogrock.com/
Length10=-1


File11=http://a.files.bbci.co.uk/media/live/manifesto/audio/simulcast/hls/uk/sbr_high/ak/bbc_radio_three.m3u8
Title11=BBC3HD
Length11=-1


File12=http://stream2.srr.ro:8022/
Title12=SRR Radio România Muzical
Length12=-1


File13=http://109.169.23.22/stream.mp3?ipport=109.169.23.22_37782
Title13=Radio Darvish
Length13=-1


File14=http://www.rootslegacy.fr:8080/
Title14=Roots Legacy 
Length14=-1


File15=https://radio-dzair.net/proxy/raina?mp=/stream
Title15=Radio Dzair Raina
# https://onlineradiobox.com/dz/dzairraina/?cs=dz.dzairraina
Length15=-1



```


m3u

```

#ambient sleeping pill
http://radio.stereoscenic.com/asp-h
# NRK radio_klassisk Norway
http://lyd.nrk.no:80/nrk_radio_klassisk_mp3_h
#radio-planeta-occitania  
http://www.radioking.com/play/radio-planeta-occitania
#Hi On Line World Radio World Music
http://82.94.205.73/proxy/onlineworldradio?mp=/
#Chroma Ambient
http://148.251.184.14:8004
#Kripalu Bhakti Radio
http://68.168.101.146:8417
#RKC New Music HQ Radio Krishna Central Italy
http://81.25.96.13:8090
#cro-d-dur Classical Czech
# BBC 3 HD 
http://a.files.bbci.co.uk/media/live/manifesto/audio/simulcast/hls/uk/sbr_high/ak/bbc_radio_three.m3u8
# RST Radio Rock Live
http://216.144.255.186:8100/live
# krautrock-world
http://94.249.254.14:7592/stream krautrockworld
#beprogrock
http://142.44.227.24:10022
#SRR Radio România Muzical
http://stream2.srr.ro:8022/
https://radio-dzair.net/proxy/raina?mp=/stream
#Radio Dzair Raina



```

I would like this cover.jpg to be written into the pls or m3u text if at all feasible (path or folder)

Hope this clarifies

---

### Post by shantiq on 2022-04-25
> **Yellow Pasque said:**
> I've moved on from Audacious to Strawberry. Audacious doesn't see much development these days and Strawberry generally does a better job at finding lyrics and cover art.

Strawberry is ace indeed  usually i stay with Foobar but Audacious or XMMS more my tipple since not a library player aficionado

---

### Post by #&amp;thj^% on 2022-04-25
> **Yellow Pasque said:**
> I've moved on from Audacious to Strawberry. Audacious doesn't see much development these days and Strawberry generally does a better job at finding lyrics and cover art.
I've always liked your suggestions, and Strawberry has me now. :)
Nice Player
Strawberry is a music player and music collection organizer. It is a fork of Clementine released in 2018 aimed at music collectors and audiophiles. It's written in C++ using the Qt toolkit.

---

### Post by Yellow Pasque on 2022-04-25
> **1fallen said:**
> I've always liked your suggestions, and Strawberry has me now. :)
Nice Player
Strawberry is a music player and music collection organizer. It is a fork of Clementine released in 2018 aimed at music collectors and audiophiles. It's written in C++ using the Qt toolkit.

Yeah, I think I use it as more of a playlist-driven player, though those that prefer the "library"/Rhythmbox approach may be able to tailor it to their needs. I'm not big on streams and radio stations on a computer, so I can't comment on that aspect, but right now, Strawberry does the job for me. I just wish it had more fine-grained control of lyrics.

---

### Post by #&amp;thj^% on 2022-04-25
> **Yellow Pasque said:**
>  I'm not big on streams and radio stations on a computer, so I can't comment on that aspect, but right now, Strawberry does the job for me. I just wish it had more fine-grained control of lyrics.

That was a strong point of me keeping it (tags the song meta and art when available), agreed on the lyric control.
but pound for pound I'll take it. :)

---

