---
title: "Audacious 3.3"
date: 2012-08-04
forum: Multimedia Software
---

### Post by irv on 2012-08-04
I have tried so many different audio players. Rhythmbox is OK, but it just seems to lack something. The other day I installed Audacious [http://audacious-media-player.org/]("http://audacious-media-player.org/") And I really like it. I know it is still in the beta testing but I found it works quite well.
[ATTACH]222234[/ATTACH]
There was and is a lot of developers involved in this project and I believe it will become a big player when it come to audio players.
If you are looking for something like this it is worth looking into.
This version was released on July 26, 2012.
If you are interested in installing it, [Read This.]("http://www.webupd8.org/2012/08/install-audacious-33-in-ubuntu-1204.html")

---

### Post by cottfcfan on 2012-08-04
I 1st installed Audacious about 3 weeks ago, and now use it as my main audio player.
It doesn't have all the Bells & Whistles & Bloat of other players, but by tweaking the equalizer, crystalizer, & extra stereo, the sound quality is better than anything else I have tried.
Also version 3.3 is now out of Beta.

---

### Post by ads52 on 2012-08-11
Interestingly enough 3.3.1 has just just been released with a few bug fixes. I am a huge fan of the current audacious in particular when it has been built against a recent FFmpeg. I attach a screenshot of the newest audacious playing an Opus file, only possible if FFmpeg has been built with* --enable-opus* ......

---

### Post by mc4man on 2012-08-11
Additionally when built against a recent FFmpeg aud will also support wmal thru the ffaudio plugin
(libav remains lacking in that area thru it's version of libavcodec

---

### Post by ads52 on 2012-08-11
> **mc4man said:**
> Additionally when built against a recent FFmpeg aud will also support wmal thru the ffaudio plugin

Quantal Quetzal will be interesting then. I know you are following Quantal, how fully featured might Audacious be for this release (on 3.2.3 atm)? I guess a lot depends on libavcodec-extra-53....

---

### Post by mc4man on 2012-08-12
> **ads52 said:**
> Quantal Quetzal will be interesting then. I know you are following Quantal, how fully featured might Audacious be for this release (on 3.2.3 atm)? I guess a lot depends on libavcodec-extra-53....

Yeah it's on 3.2.3 which generally should be fine. The interface is a little nicer in looking here in 3.3.x, & as we've mentioned can be extended slightly when built off of FFmpeg
Aud bases on FFmpeg instead of Libav so Debian/Ubuntu can occasional lose out a bit or more till taken care  of.

Atm I don't bother testing the repo aud in 12.10, a bit of an offshoot of trying in 11.10 to get ffaudio.so returned. Took a couple of bug reports, many months & was finally returned to 12.04 last Feb. after some typical Debian/Libav boys/fix the dev version 1st. nonsense

---

### Post by ads52 on 2012-08-12
> **mc4man said:**
> Atm I don't bother testing the repo aud in 12.10, a bit of an offshoot of trying in 11.10 to get ffaudio.so returned. Took a couple of bug reports, many months & was finally returned to 12.04 last Feb. after some typical Debian/Libav boys/fix the dev version 1st. nonsense

As always there are huge benefits to building your own copies of multimedia applications, or at the very least moving to the latest version of Ubuntu every 6 months. In my own usage have *completely* converted to audacious for listening to ripped audio cds although at heart I am an MPlayer user and use it in preference to audacious for all other media files :).

---

