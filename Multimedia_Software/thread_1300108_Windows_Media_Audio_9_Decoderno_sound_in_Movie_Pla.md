---
title: "Windows Media Audio 9 Decoder/no sound in Movie Player"
date: 2009-10-24
forum: Multimedia Software
---

### Post by tdmoore on 2009-10-24
Testing Koala 9.10.

Sound is working fine and I have unmuted since upgrade and I can now use Rhythmbox and most aspects with sound including my music.

However still no sound in Movie Player and I received this notice (see attached screen shot) when I attempted to view a .wmv file sent to me by a colleague.

Can someone assist me here?  All updates done as of today and all repos installed (extras) that I have found through the forum.

Thanks...video without sound is pretty frustrating....

---

### Post by beastrace91 on 2009-10-24
Have you added the [Medibuntu repos](https://help.ubuntu.com/community/Medibuntu)? If not do so and then do ```
sudo apt-get install non-free-codecs
```

Should solve the issue for you.

~Jeff

---

### Post by tdmoore on 2009-10-24
Thanks Jeff...solved the issue for one of the media file but for some reason I cannot get sound on the other.

<EDIT> Seems as if the 1 file that worked was MS codec 8.  Still cannot get the audio on codec 9.

Curious...any ideas on how to get this to work?  Really, the file appears to be only a joke so I am not that worried but would be nice to be fixed.

Thanks.

---

### Post by beastrace91 on 2009-10-24
What you tried playing the files in MPlayer (not the default movie player) if not install it and see if that works with out the message (its a better player anyways)

Install it from the medibuntu repos using ```
sudo apt-get install mplayer
```

~Jeff

---

### Post by mc4man on 2009-10-24
wma2 is playable on gstreamer apps thru libavcodec

wma3 is sometimes playable thru w32codecs and the gstreamer0.10-pitfdll plugin ( windows media 9.1 should play (but may not), windows media 10 probably won't

wmal (lossless won't play in gstreamer (unless you purchase the fluendo windows media pack

xine based players, a 32 bit mplayer and a well built vlc can play all thru  libavcodec and w32codecs (wmal is only decoded thru w32codecs, wma3 could be either

---

### Post by tdmoore on 2009-10-24
> **beastrace91 said:**
> What you tried playing the files in MPlayer (not the default movie player) if not install it and see if that works with out the message (its a better player anyways)

Install it from the medibuntu repos using ```
sudo apt-get install mplayer
```

~Jeff

Appreciate the assistance...mark this solved.  I already had mplayer installed and opened the file there and it worked perfectly!

Thanks again Ubuntu community!!

---

### Post by vinutux on 2009-10-25
yes...plz mark thred SOLVED :)

---

