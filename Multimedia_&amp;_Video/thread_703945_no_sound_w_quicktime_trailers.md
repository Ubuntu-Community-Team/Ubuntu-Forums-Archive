---
title: "no sound w/ quicktime trailers"
date: 2008-02-21
forum: Multimedia &amp; Video
---

### Post by trmentry on 2008-02-21
I'm running Gutsy, pretty much defaults for audio/video.  I added in gstreamer-ugly and -good.

I go out to Quicktime trailer site and can see the video play.. but no audio.  I tried the -bad codecs but no joy.

Any pointers on this?  

Thanks

---

### Post by linuxwizard on 2008-02-21
Do you have the w32codecs installed ?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by trmentry on 2008-02-21
Yup.

```

~$ dpkg -l | grep w32
ii  w32codecs                                  20071007-0medibuntu1             
```

My /usr/lib/codecs dir has a lot of files in it.  THere is a symlink /usr/lib/win32 --> /usr/lib/codecs  And I created a /usr/lib/codecs/win32 --> /usr/lib/codecs symlink.  Still no joy.

---

### Post by ubuntu-freak on 2008-02-21
Have you installed faad? Take a look at my [how-to](http://ubuntuforums.org/showthread.php?t=661833) as well, just incase.
 
Nathan

---

### Post by trmentry on 2008-02-23
> **reassuringlyoffensive said:**
> Have you installed faad? Take a look at my [how-to](http://ubuntuforums.org/showthread.php?t=661833) as well, just incase.
 
Nathan

Thanks Nathan.

I followed your guide and mplayer now attempts to stream the quicktime trailer but now I get no video or audio.  Just a gray box where it should be.  

:(

---

### Post by ubuntu-freak on 2008-02-23
> **trmentry said:**
> Thanks Nathan.

I followed your guide and mplayer now attempts to stream the quicktime trailer but now I get no video or audio.  Just a gray box where it should be.  

:(

 
Well that's odd. Did you do all of part 1 and 2? Do other sites work okay? Stage6 for example. Did you reboot?
 
Nathan

---

### Post by trmentry on 2008-02-23
> **reassuringlyoffensive said:**
> Well that's odd. Did you do all of part 1 and 2? Do other sites work okay? Stage6 for example. Did you reboot?
 
Nathan


Yup... all other sites I tested afterwards work fine.  I went to Stage6 just now and worked fine.  

I did part 1 and 2 of your guide.  And as I mentioned before, this is a fairly stock 7.10 install.  I've not added much to it.

Yup.. rebooted after installing everything.

---

### Post by ubuntu-freak on 2008-02-23
> **trmentry said:**
> Yup... all other sites I tested afterwards work fine.  I went to Stage6 just now and worked fine.  

I did part 1 and 2 of your guide.  And as I mentioned before, this is a fairly stock 7.10 install.  I've not added much to it.

Yup.. rebooted after installing everything.

 
That's both good and bad. Perhaps apple.com have done something which confuses MPlayer, or a bad update to mozilla-mplayer. Test some qt movies that aren't from the apple site.

---

### Post by trmentry on 2008-02-23
> **reassuringlyoffensive said:**
> That's both good and bad. Perhaps apple.com have done something which confuses MPlayer, or a bad update to mozilla-mplayer. Test some qt movies that aren't from the apple site.


heh... do you happen to have a link to site that has quicktime out there to test?   I've been searching but keep finding flash type things.

---

### Post by trmentry on 2008-02-23
> **trmentry said:**
> heh... do you happen to have a link to site that has quicktime out there to test?   I've been searching but keep finding flash type things.

Nevermind.. found one... and it works fine.  So I'm guessing its Apple doing something wonky.

---

### Post by wolfen69 on 2008-02-23
quicktime trailers work for me. go here [http://ubuntuforums.org/showthread.php?t=705687](http://ubuntuforums.org/showthread.php?t=705687) for the answer.

---

### Post by trmentry on 2008-02-23
nope.  didn't work for me.  I had most of those installed already from the other post /how to

mplayer just shows a gray box where the movie would be.

I did a about:plugins on firefox and it shows mplayer as the sole player for all media types.

```

QuickTime Plug-in 6.0 / 7

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.40
```

---

### Post by trmentry on 2008-02-23
hrmm... I rebooted again.. and now it works.  

/me backs away slowly so not to scare the computer.

---

### Post by ubuntu-freak on 2008-02-23
> **trmentry said:**
> hrmm... I rebooted again.. and now it works.  

/me backs away slowly so not to scare the computer.

 
Well that's a bit random. I don't know how to explain that. I should edit my how-to and say; "Please reboot between one and ten times after completing the how-to." :-)
 
MPlayer is awesome, it just needs to handle stream addresses better. Very random sometimes. Although that's usually on the BBC site.
 
Nathan

---

