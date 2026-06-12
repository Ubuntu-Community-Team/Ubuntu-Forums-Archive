---
title: "A number of issues with Rhythmbox, GStreamer"
date: 2013-08-29
forum: Multimedia Software
---

### Post by EddyTheB on 2013-08-29
I had these problems on a Samsung laptop I bought earlier in the year, I thought they were caused by an issue with the Ubuntu build on that laptop, which was always kind of dodgy. But I returned the laptop, and got myself a System 76 laptop, and the problems persist...

1. I cannot change any track details, for example changing the name of a track.  I right click on a track, choose properties, and edit one of the text fields. When I press enter I get the warning:

```
Error while saving song information
GStreamer encountered a general stream error.
```

2. The IM Status plugin does nothing. I believe that all I should have to do is enable it and the track that I'm listening will become my status in empathy, but this does not happen. There are no error messages.

3. Streaming radio stations do not display track information. I believe they are meant to, from posts like this: [http://ubuntuforums.org/showthread.php?t=1941861](http://ubuntuforums.org/showthread.php?t=1941861).

I believe that all three issues are caused by some problem with GStreamer, but don't know how I'd go about checking that, or fixing the problem. Please could someone offer me some advice? Thanks.

I have Ubuntu 13.04 on a System 76 Galago Ultra Pro, but as I mentioned, the same problems occured on a Samsung also running 13.04.
2. The IM Status plugin does nothing. I believe that all I should have to do is enable it and the track that I'm listening will become my status in Empathy

---

### Post by tgalati4 on 2013-08-29
For 1, install *easytag* and look at the file tag information there.  See if you can edit it.  The tag editor in Rhythmbox may not be as robust as *easytag*.

I don't use IM status plug-in, so can't help there.  Send an email to the developer:  [http://www.vuntz.net/projects/rhythmbox/](http://www.vuntz.net/projects/rhythmbox/)

For 3, post a link for a stream that is not working.  There are so many variations of streams that without a specific example it's hard to diagnose.  Try opening the stream in *vlc* and see what happens.  There is a message/error box so you can cut and paste any details if it fails.

---

### Post by EddyTheB on 2013-08-29
1. easytag works, great, thanks for the tip.

2. Ok, I'll email the developer.

3. The link is here [http://www.bbc.co.uk/radio/listen/live/r6_aaclca.pls](http://www.bbc.co.uk/radio/listen/live/r6_aaclca.pls), and with further investigation I think the problem is with the link; most of the pre-included radio stations on rhythmbox don't work, but I found one that does, and it does list the track information. I suppose the BBC just don't provide that information.

Thanks for your help.

---

### Post by tgalati4 on 2013-08-29
Movie Player plays the linked stream OK, but there are no track titles.  But there is a BBC iplayer plug-in for Movie Player that might display that information.  I haven't tried it.

Inside the linked *.pls file are two streams with no titles:

tgalati4@Mint14-Extensa /tmp $ cat r6_aaclca.pls 
[playlist]
NumberOfEntries=2
File1=http://bbcmedia.ic.llnwd.net/stream/bbcmedia_intl_lc_6music_p?s=1377804652&e=1377819052&h=020fe5b4177baf1600952e6c57494134
Title1=No Title
Length1=-1
File2=http://bbcmedia.ic.llnwd.net/stream/bbcmedia_intl_lc_6music_q?s=1377804652&e=1377819052&h=f146f7edc4e2ec97a24614a044d12355
Title2=No Title
Length2=-1

The stream also plays in Rhythmbox, but no track titles.  There is an FM radio plug-in.  I haven't played with it.

iPlayer lists lots of BBC stations but no links.  You probably have to be in a British Colony and we opted out several years ago.

---

