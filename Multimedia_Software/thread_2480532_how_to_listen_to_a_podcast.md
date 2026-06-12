---
title: "how to listen to a podcast"
date: 2022-11-01
forum: Multimedia Software
---

### Post by Skaperen on 2022-11-01
i want to listen to a podcast on my Xubuntu 20.04 system using only software in the Ubuntu repository.  what do i need to install and where can i get podcasts for free?  podcasts are all new to me and i was only recently told they were audio only.

---

### Post by Dennis N on 2022-11-01
Look here:
[https://linuxhint.com/ubuntu_podcast_players/](https://linuxhint.com/ubuntu_podcast_players/)

Many (most?) also have an associated web page with an embedded player and will play in Firefox.

---

### Post by &amp;KyT$0P# on 2022-11-01
Every podcast I've tried to listen to is just normal, standard audio.  So I just use my usual web browser for streaming/listening podcasts online, or my usual media player if the podcast is a download.  No podcast-specific software required.

---

### Post by Skaperen on 2022-11-01
> **halogen2 said:**
> Every podcast I've tried to listen to is just normal, standard audio.  So I just use my usual web browser for streaming/listening podcasts online, or my usual media player if the podcast is a download.  No podcast-specific software required.

is there a single place to find all podcasts?  information in many media-based ads for podcasts and many other references suggest searching at the place "you get all your podcasts".  i have no such place.  is this something that is shared around and anyone with enough resources can run one?

if a web browser can do all i need, i'll just do that.  is spotify the only place to go?

---

### Post by &amp;KyT$0P# on 2022-11-01
> **Skaperen said:**
> is there a single place to find all podcasts?  ... is spotify the only place to go?

Spotify is one such option.

I don't use a single centralized source of podcasts.  I would start with the individual podcast creators' own websites, where they often self-host their podcasts.  Some podcasts are also available on Youtube.

---

### Post by TheFu on 2022-11-01
I use RSS feeds to get notified about podcasts from people/networks I care about.  In the RSS feed, there is usually a 'download' button.  Or you can use gpodder or fetchpods.

[https://linuxhint.com/ubuntu_podcast_players/](https://linuxhint.com/ubuntu_podcast_players/)

As for playback any software that can play the provided audio file can be used.  I use mpv, but I also place podcasts into a directory structure that nextcloud can see, so any nextcloud client can access and play those files. Additionally, that directory is part of my mpd server(s), so I can play episodes that way.

I get the feeling that most people listen to podcasts during their commutes. This means they use a smartphone/tablet and there must be 50 apps to have new episodes automatically downloaded and kept for X days, then deleted.

There are podcasts for any subject. It is great and sometimes scary.  Different podcast networks try to lock us into their specific network. Apple is famous for this and they make it easy, assuming the topic you want isn't something that 1 company thinks is offensive or they can't make any money by connecting you with it.  RSS is the most open method.  It is a standard with 2 competing file formats, both completely open.  

I only use RSS feeds. These are usually directly from the podcaster's own website. It let's them compete with the corporate overlords more directly.

---

### Post by Dennis N on 2022-11-01
> is there a single place to find all podcasts? 

All Podcasts in existence, no. But quite a few are at [Google Podcasts]("https://podcasts.google.com/"). Most play in your browser if you click on the icons. There is also a search function at the top.

---

### Post by iamjiwjr on 2022-11-03
Rhythmbox and gpodder to name two. But for me, the open source program, Pocket Casts, is best. Or Cpod. But they're a snap (or flatpak for those inclined).

---

### Post by Skaperen on 2022-11-03
it seems that various places that cast podcasts have different podcasts and many have only their own.  a podcast of interest ("Ultra" from MSNBC) i saw advertised on TV (the telly) with the words "listen to it wherever you get your podcasts".  that gave me the impression every caster has access to a copy of every podcast leaving me to wonder where the central source is.  maybe Apple?  i found many podcast sites that did not have that podcast.

i read that they are in mp3 format.  now i wonder how to just download the mp3 and listen later.  i also wonder how they make money.  i saw some begging for me to subscribe.  next, i might like to set up a "podcast cache".

---

### Post by TheFu on 2022-11-04
> **Skaperen said:**
> it seems that various places that cast podcasts have different podcasts and many have only their own.  a podcast of interest ("Ultra" from MSNBC) i saw advertised on TV (the telly) with the words "listen to it wherever you get your podcasts".  that gave me the impression every caster has access to a copy of every podcast leaving me to wonder where the central source is.  maybe Apple?  i found many podcast sites that did not have that podcast.
100% marketing.  They act like the podcast caching service they've selected is the only one.  Podcasters choose where they want to be. Some are all about gaining the widest audience, some want to make the most money, and some have a corporate overlord/partner that some contract mandates they use.

> **Skaperen said:**
> 
i read that they are in mp3 format.  now i wonder how to just download the mp3 and listen later.  i also wonder how they make money.  i saw some begging for me to subscribe.  next, i might like to set up a "podcast cache".

Audio files from podcasts can be in any audio format. Some have videos too, but those are usually just talking heads. The audio is their core communications format. I prefer vorbis, which is built-in support by all modern web browsers.  mp3 is the most popular, just because it is widely supported and the patents for creating it expired.  At low bitrates, vorbis has much higher quality and has always been without software patents.

Apple's podcasting platform is popular because for iOS, it is the easiest to use. This is by design.  More "walled garden", non-open, stuff. I'd bet those probably use aac audio.

Where to get podcasts isn't a single choice. A good pod-catcher will support all types of distribution channels.  Just remember that each of those channels makes money just like broadcast TV does - showing audience size, capturing "watch" statistics for advertisers.  The more you use the corporate platforms, the more embedded advertising you'll get to hear.  The smaller guys that are profitable usually have sponsorship messages just after the 15 sec leader and for a few minutes at the end.  Of course, that's just my experience, I go directly to the original podcasters RSS feeds.  

Might be an interesting topic to ask in the Cafe .... what podcasts do you like?

---

