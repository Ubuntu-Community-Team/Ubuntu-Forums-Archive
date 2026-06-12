---
title: "The most secure &amp; reliable mp3 and video player"
date: 2010-11-20
forum: Multimedia Software
---

### Post by zhaotianwu on 2010-11-20
I am seeking for a secure and reliable mp3 and video player.
For security reason, I'm reticent about Universe repository. Can anyone suggest a way to get my MP3 player and my video player to work without having to resort the Universe repository? Preferably can play RMVB files. thanks.

---

### Post by kidders on 2010-11-21
Hi there,

What particular security issues are you worried about? It would also be useful to know what kind of environment your box is running in, and what other software you've installed (or decided *not* to install!) on it.

All media players are inherently insecure. That said, since you mentioned video (ie you presumably have X installed), you've already exposed yourself to a whole world of security issues ... A media player isn't necessarily going to make things much worse.

The worst issues tend to be the ones involving network access (eg streaming protocols like RTSP and extraneous bells & whistles like CDDB data retrieval) because, in theory, they're much more readily exploitable. Depending on your working environment, building certain non-essential functionality out of a media player may well make it safe enough for you to run, but it's hard to be sure without knowing more.

---

### Post by nickguletskii on 2010-11-21
I would say VLC, although it doesn't want to run on root. Yeah, I like working in elevated privileges. ;)

---

### Post by zhaotianwu on 2010-11-21
> **kidders said:**
> Hi there,

What particular security issues are you worried about? It would also be useful to know what kind of environment your box is running in, and what other software you've installed (or decided *not* to install!) on it.

All media players are inherently insecure. That said, since you mentioned video (ie you presumably have X installed), you've already exposed yourself to a whole world of security issues ... A media player isn't necessarily going to make things much worse.

The worst issues tend to be the ones involving network access (eg streaming protocols like RTSP and extraneous bells & whistles like CDDB data retrieval) because, in theory, they're much more readily exploitable. Depending on your working environment, building certain non-essential functionality out of a media player may well make it safe enough for you to run, but it's hard to be sure without knowing more.

Hi kidders, here is my situation.
I do not download pirated videos, basically I just need my computer to play my sound recordings (mp3, wav, etc.) and occasionally play some RMVB videos I converted from my own DVDs. So basically I'm not worrying about online video/audio playing and network access is not important to me.
My environment is Ubuntu 10.10, freshly installed with only base installation. When install it, I disabled Universe repository so now I cannot play any mp3 or videos. I want to be able to play my mp3 (and videos, if possible) without exposing myself to any security hazard. I think that's why I switched from Windows to Ubuntu and disabled the Universe repository.
Could you please give me some thoughts, kidders? Many thanks.

By the way, what is "video (ie you presumably have X installed)"?

---

### Post by wther on 2010-11-21
Have you tried rhytmbox(gnome) or amarok(kde) ?

---

### Post by cchhrriiss121212 on 2010-11-21
There is basically zero security risk from enabling the universe repo. There is zero risk from just playing media files with a player like VLC, I don't understand why you think there would be.

What I would recommend you do is to enable the universe repo, install ubuntu-restricted extras, then disable it again. Then install VLC and use it to play whatever you like.

---

### Post by kidders on 2010-11-21
> **cchhrriiss121212 said:**
> There is basically zero security risk from enabling the universe repo.+1 ... It doesn't sound like zhaotianwu's setup warrants that kind of paranoia.

---

### Post by zhaotianwu on 2010-11-22
> **cchhrriiss121212 said:**
> There is basically zero security risk from enabling the universe repo. There is zero risk from just playing media files with a player like VLC, I don't understand why you think there would be.

What I would recommend you do is to enable the universe repo, install ubuntu-restricted extras, then disable it again. Then install VLC and use it to play whatever you like.

:Puh-huh, I see! Yeah it's a bit overdoing it. Actually I overheard that Universe could be some risky. By the way, how can I disable universe repo after installation? Will it handicap the normal functionality?

---

### Post by cchhrriiss121212 on 2010-11-22
Open synaptic package manager and go to Settings>Repositories and check the boxes for which sources you'd like enabled or disabled. Your repo selection has nothing to do with the ability to play media files, it just determines what you can download, so there is no functionality to lose.

---

