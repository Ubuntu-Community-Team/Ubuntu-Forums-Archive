---
title: "wmv webstreaming by European Parliament"
date: 2012-09-03
forum: Multimedia Software
---

### Post by Dafydd on 2012-09-03
Hi,

Does anyone know how to watch these videos by the European Parliament? I've tried on different flavours of Ubuntu for the past year but with no success (except for kmplayer, downloading the file which was then not searchable). This has been the case with the last three editions of Ubuntu.

[http://www.europarl.europa.eu/ep-live/EN/committees/video?event=20120712-1500-COMMITTEE-ITRE&category=COMMITTEE&format=wmv](http://www.europarl.europa.eu/ep-live/EN/committees/video?event=20120712-1500-COMMITTEE-ITRE&category=COMMITTEE&format=wmv)


Anyone have any ideas?

I've just tried the Ubuntu multimedia guide (for webstreaming) but with no success.

---

### Post by ron999 on 2012-09-03
> **Dafydd said:**
> ... Does anyone know how to watch these videos by the European Parliament?...

... not searchable...
Hi
Look where it says "**URL of the video stream**".
To watch the video use the URL with mPlayer:-
```
mplayer mms://vodwms.europarl.europa.eu/wmv/nas/nasvod01/cod1207/wm_pad/Channel08/VODChapter_20120712_15062000_16160100_Ch08_7c68ca8213868e9193f3ed0.wmv?wmcache=0
```

Or paste it into **SMPlayer**.

(But it's not searchable) :mad:

---

### Post by Dafydd on 2012-09-04
> **ron999 said:**
> Hi
Look where it says "**URL of the video stream**".
To watch the video use the URL with mPlayer:-
```
mplayer mms://vodwms.europarl.europa.eu/wmv/nas/nasvod01/cod1207/wm_pad/Channel08/VODChapter_20120712_15062000_16160100_Ch08_7c68ca8213868e9193f3ed0.wmv?wmcache=0
```

Or paste it into **SMPlayer**.

(But it's not searchable) :mad:


Thanks for this! Some of us complained about the video service and maybe that's why they've added the direct link.

Still -- it's not searchable and that makes it pretty useless if you have to listen through three hours of MEP bla bla till you get to what you want to follow.

Also, for some reason I can only get audio in German!

There's not another way to listen to this on Ubuntu? This is a general problem I've had on Ubuntu at least from 10.04 (prob before).

It makes me sick that the Parliament pretends to be 'open' and 'available to citizens' and makes it impossible for those not using Windows to listen to the debates.

---

### Post by Dafydd on 2012-09-04
Now using SMplayer to view the webstream. The annoying thing is the lack of searchability. Also if you change audio stream (for some reason this is only possible for me in SMplayer and not Mplayer or VLC) then you start at the very beginning again.

---

### Post by Dafydd on 2012-09-04
Actually now downloading with mplayer ie.

mplayer mms:/link/something.xxx -dumpstream -dumpfile file.xxx

Or see: 

[http://ubuntuhowtos.com/howtos/download_mms_stream](http://ubuntuhowtos.com/howtos/download_mms_stream)

---

