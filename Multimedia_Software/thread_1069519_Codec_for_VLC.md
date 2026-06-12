---
title: "Codec for VLC"
date: 2009-02-14
forum: Multimedia Software
---

### Post by DeMus on 2009-02-14
Is there a codec to have VLC play Windows Media Audio 10 professional? I can watch a HD wmv file but I have no sound. Movieplayer doesn't even start, just gives me a black screen while the counter remains at zero.
I have looked around, installed several codecs and codecspacks but nothing works. Who can help me?

---

### Post by x33a on 2009-02-14
i don't think you can use external codecs with vlc. everything is built-in.

try mplayer if totem is not working.

---

### Post by DeMus on 2009-02-14
> **x33a said:**
> i don't think you can use external codecs with vlc. everything is built-in.

try mplayer if totem is not working.

Thank you for your answer.
But if mplayer also gives me no sound?
I wonder if there are codecs for this type of sound. MS probably changed the format again to keep it for the windows system only.

---

### Post by x33a on 2009-02-14
well i can play HD wmv files both in vlc and totem.

you can try the latest version of vlc 0.9.8a.

for totem, i don't remember which plugins i downloaded, but vlc can also play the same files easily.

---

### Post by andrew.46 on 2009-02-14
Hi,

I have been unable to find a sample file of this type. Do you have a link to such a file?

Andrew

---

### Post by DeMus on 2009-02-14
> **andrew.46 said:**
> Hi,

I have been unable to find a sample file of this type. Do you have a link to such a file?

Andrew

No, sorry. I downloaded a movie from usenet and in VLC I see it uses the WMA10 audio codec.
I have no idea where to find an example of such a file.

---

### Post by DeMus on 2009-02-14
> **x33a said:**
> well i can play HD wmv files both in vlc and totem.

you can try the latest version of vlc 0.9.8a.

for totem, i don't remember which plugins i downloaded, but vlc can also play the same files easily.

Where to find the 0.9.8. version for Ubuntu? When I start to download it from the videolan site it gives 0.8.6.

---

### Post by x33a on 2009-02-14
in the ubuntu repos it's 0.9.4 i guess.

try sudo aptitude install vlc*

latest debs: [http://archive.getdeb.net/dump/intrepid/vlc/](http://archive.getdeb.net/dump/intrepid/vlc/)

for the exact info regarding the file install mediainfo. it gives the detailed information about multimedia files.

---

### Post by DeMus on 2009-02-14
> **x33a said:**
> in the ubuntu repos it's 0.9.4 i guess.

try sudo aptitude install vlc*

latest debs: [http://archive.getdeb.net/dump/intrepid/vlc/](http://archive.getdeb.net/dump/intrepid/vlc/)

for the exact info regarding the file install mediainfo. it gives the detailed information about multimedia files.

I still use hardy 8.0.4 and, unless I am mistaken, vlc version 0.8.6 is the latest.

---

### Post by andrew.46 on 2009-02-14
Hi,

A picture is worth a thousand words and I attach a screenshot of the newest vlc at work :-). This is compiled from the source available here:

[http://download.videolan.org/pub/videolan/vlc/0.9.8a/vlc-0.9.8a.tar.bz2](http://download.videolan.org/pub/videolan/vlc/0.9.8a/vlc-0.9.8a.tar.bz2)

But I will admit that I am not sure what the most recent Ubuntu packaged version is at :(.

Andrew

---

### Post by doug1212 on 2009-02-14
Hi,
If you are willing to use a third party repo and are aware of the possible security implications then here is a Hardy repository with VLC-0.9.8a:

[HTML]http://ubuntufromscratch.wordpress.com/[/HTML]

Doug.

---

### Post by DeMus on 2009-02-14
> **doug1212 said:**
> Hi,
If you are willing to use a third party repo and are aware of the possible security implications then here is a Hardy repository with VLC-0.9.8a:

[HTML]http://ubuntufromscratch.wordpress.com/[/HTML]

Doug.

Thanks for the link. I uninstalled the old version and replaced it with the new one, eventhough my french is terrible. But this new version tells me this when opening the wmv-file:

No suitable decoder module:
VLC does not support the audio or video format "wmap". Unfortunately there is no way for you to fix this.

Okay, I have the latest version, but for this file it's of no help. Thank you anyway.

---

