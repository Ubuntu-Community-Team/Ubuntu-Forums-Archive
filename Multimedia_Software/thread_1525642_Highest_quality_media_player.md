---
title: "Highest quality media player"
date: 2010-07-07
forum: Multimedia Software
---

### Post by Prescience500 on 2010-07-07
What media player currently has the highest video and audio quality (not referring to performance)? I'll probably be using WebM, ogg vorbis, mp3, FLAC, avi, and wmv.

---

### Post by Yarui on 2010-07-07
This is really more of a question of the quality of the media, not so much the media player.  If a file has good quality video and sound, most players will play them with good quality video and sound.  What media player you use is just a matter of which interface you prefer, I think.

---

### Post by Prescience500 on 2010-07-07
I've heard that before, but I'm positive that there is a difference. I know when I visually compared VLC .9's video quality to xine and mplayer based media players, VLC's video quality wasn't as good. I'm not sure how the latest media players are though, I think they are probably closer now than before. I've read that the people who make Amorak say that VLC has better audio quality than xine.

---

### Post by cascade9 on 2010-07-07
VLC uses FFmpeg, as does xine-lib, mplayer and others. If there is a differenc between them it would be because of this- 

> lternatively, VLC has modules for codecs that are not based on FFmpeg's libraries.

[http://en.wikipedia.org/wiki/VLC_media_player](http://en.wikipedia.org/wiki/VLC_media_player)

Its possible that VLC 0.9.x had a superiour module to xine/mplayer when you tested. 

I'd pretty much agree with Yarui. BTW, here is what the foobar2000 (which has a reputation for being high quality) site says about 'does fb2k sound better'?  

> Does foobar2000 sound better than other players?

    No. Most of “sound quality differences” people “hear” are placebo effect (at least with real music), as actual differences in produced sound data are below their noise floor (1 or 2 last bits in 16bit samples). foobar2000 has sound processing features such as software resampling or 24bit output on new high-end soundcards, but most of the other mainstream players are capable of doing the same by now. 
  


[http://www.foobar2000.org/FAQ](http://www.foobar2000.org/FAQ)

---

### Post by Yarui on 2010-07-07
Ah, yeah, that foobar article makes a good point.  A high end sound card would make some difference and a media player's ability to use the features of that card would mean that media player can play higher quality sound than players that can't use those features (if you are using a high end sound card).  Like it said, though, most players are capable of that.

---

### Post by rkcjeengar on 2010-07-07
1. VLC Media Player
2. Media Jukebox

both are good player

---

### Post by Prescience500 on 2010-07-07
Hmm...So maybe one might have say better video quality on my computer because it supports certain things of my video card and driver that would improve video quality. Conversely, if I were to use another system, there's actually a chance that another media player may have better video quality because it supports that systems graphics better?

---

### Post by cascade9 on 2010-07-08
> **Yarui said:**
> Ah, yeah, that foobar article makes a good point.  A high end sound card would make some difference and a media player's ability to use the features of that card would mean that media player can play higher quality sound than players that can't use those features (if you are using a high end sound card).  Like it said, though, most players are capable of that.

Pretty much. Its not only features though, better sound cards have better quality DACs, etc. 

What the sound card quality increase (aside from better quality parts) is from what you can think of as  'resolution'. A sound card that can do 24bit has 1.5 times the resolution of 16bit. Then you can get 48/96/192kHz over the usual 44.1kHz. That wont help much in 99% of cases though, if the source file is 16/44.1kHz (like most are) then the ability of the sound card to use great bit depth and kHz wont matter. 

> **Prescience500 said:**
> Hmm...So maybe one might have say better video quality on my computer because it supports certain things of my video card and driver that would improve video quality. Conversely, if I were to use another system, there's actually a chance that another media player may have better video quality because it supports that systems graphics better?

Umm.....not in my expereince. I havent used XvBA (ATI hardware video decoding) but I have used VDPAU (NVidia  hardware video decoding). IMO, there is no difference in quality between VDPAU video quality and normal CPU video decoding quality. 

I think you might have read Yaruis post above and then 'moved' what was said there about sound cards to video.

---

