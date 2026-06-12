---
title: "[SOLVED] WMAP codec"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by dr.koljan on 2007-08-28
Maybe the question sounds dumb, but it's really a problem for me.

Recently I downloaded a brand-new Half-Life 2: Episode Two trailer from the GC presentation ([link]("http://streamingmovies.ign.com/pc/article/815/815078/halflife2ep2_theadvisor_082_wmvhd.wmv")). Since I had almost all the codecs available, I didn't expect any problems. However, when I opened the file with Totem Movie Player, it asked me I wanted to download a suitable codec. ([screensho]("http://img46.imageshack.us/img46/1962/dialogvr2.png")t) I clicked yes, but in the list there was only one selection which was already installed. ([screensho]("http://img47.imageshack.us/img47/7418/menuwm2.png")t) I managed to make a screenshot before it gave me the list, and I could see that Add/Remove Programs was searching for "**0.10:decoder-audio/x-wma**". ([1]("http://img103.imageshack.us/img103/2346/screenshotpb2.png"), [2]("http://img113.imageshack.us/my.php?image=screenshot1eu1.png")) What could it be?

Then I opened the properties for that particular file and found that Nautilus (or whatever that gives me that info) doesn't see the audio at all. [lol.]("http://img209.imageshack.us/img209/7995/noaudioip6.png")

Then I tried opening the file with VLC (which I don't really like, honestly). It didn't give me any sound either. However, I was able to open Stream and Media Info dialog box and the Advanced Information tab stated that the audio codec was **_wmap_**. ([see]("http://img131.imageshack.us/img131/6886/infosx5.png"))

Launching VLC through console produced the following error:

```
nicholas@nicholas-desktop:/media/disk/Downloads$ vlc hal*
VLC media player 0.8.6 Janus
[00000303] main decoder error: no suitable decoder module for fourcc `**_wmap_**'.
VLC probably does not support this sound or video format.
```

As far as I understand, I need to find a **wmap** codec somewhere. Googling for 'codec wmap' only made me desperate.

Is there any way to open my file without installing Windows which I hate?

Thanks in advance :)

---

### Post by Gremlinzzz on 2007-08-28
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats?action=fullsearch&context=180&value=codecs&titlesearch=Titles](https://help.ubuntu.com/community/RestrictedFormats?action=fullsearch&context=180&value=codecs&titlesearch=Titles)
:guitar:

---

### Post by dr.koljan on 2007-08-29
> **Gremlinzzz said:**
> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats?action=fullsearch&context=180&value=codecs&titlesearch=Titles](https://help.ubuntu.com/community/RestrictedFormats?action=fullsearch&context=180&value=codecs&titlesearch=Titles)
:guitar:

Thank you for the links :)

Installing the w32codecs and opening the file with MPlayer made the sound work :guitar:

However, I like Totem better than MPlayer, is there any way to make the codecs work with Totem?

Thanks in advance

---

### Post by kostkon on 2007-08-29
EDIT:

OK I saw that you managed to make it to play sound. If you install the *gstreamer0.10-pitfdll*, *Totem* will be able to use the *w32codecs*.

---

### Post by dr.koljan on 2007-08-29
I have installed gstreamer0.10-pitfdll but still no sound in Totem :(
Every other program works fine.

---

### Post by kostkon on 2007-08-29
Try to install the rest of the *GStreamer* codecs that you don't have installed. From your screenshot above of the *Add/Remove*, I can see that there are two items on the list of codecs that are not installed.

Install them and try again to play the file in *Totem*.

---

### Post by dr.koljan on 2007-08-29
I installed them just after I made the screenshot, thanks for the help anyway.

Would you mind downloading that file and trying to play it, maybe it is not just me who has such problems?

Maybe I have to configure pitfdll thing to make it see the w32codecs?

---

### Post by Gremlinzzz on 2007-08-29
A excellent player may also improve other players once installed
[http://smplayer.sourceforge.net/en/linux/index.php](http://smplayer.sourceforge.net/en/linux/index.php)
use the deb package for easy install:guitar:

---

### Post by dr.koljan on 2007-08-30
Problem solved by deleting .gstreamer-0.10 folder in my home folder and restarting :)

---

### Post by Club17 on 2007-09-23
> **Gremlinzzz said:**
> A excellent player may also improve other players once installed
[http://smplayer.sourceforge.net/en/linux/index.php](http://smplayer.sourceforge.net/en/linux/index.php)
use the deb package for easy install:guitar:

WOW!, That player solved to play my WMA 10 Professional audio files. TY! :KS

---

### Post by crono141 on 2007-10-31
This didn't solve my problem on amd64.  I get no sound from wma10pro anywhere.

---

### Post by Nais on 2008-07-02
I'm also curious if there's any way to get the WMAP audio to work on amd64?

---

