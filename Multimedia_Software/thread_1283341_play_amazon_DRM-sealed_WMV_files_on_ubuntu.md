---
title: "play amazon DRM-sealed WMV files on ubuntu?"
date: 2009-10-05
forum: Multimedia Software
---

### Post by pythonscript on 2009-10-05
Is there any way to play the DRM-protected WMV movies I downloaded off amazon on linux? I've been looking for a way to play them, but I can't seem to find anything. VLC will open them, but they don't have any sound and the picture is all garbled. I figure this is the encryption. 

Can I break the encryption and convert them to a more useable format? I'd love to play movie *that I paid for* on linux, but according to amazon, "mac os x and linux systems are not supported at this time." Any one have any ideas how I can play these? Thanks!

---

### Post by bumanie on 2009-10-05
Try going [here]("https://help.ubuntu.com/community/Medibuntu") and following the instructions - it should provide all the things you need. Alternatively [Canonical]("http://shop.canonical.com/index.php?cPath=19&osCsid=de40da6b8351f50e7e9c42afcf94b232") do provide a paid for service for codecs etc.

---

### Post by pythonscript on 2009-10-05
I installed the w32codecs, but:

mplayer returns an error: "The file has been encumbered by DRM encryption and will not play in mplayer"

vlc still plays it, but it's still garbled, just as before. Is there any other way to do this, without paying Canonical? If possible, I'd rather not pay *two *companies for the rights to movies. Thanks!

---

### Post by qyot27 on 2009-10-05
You'd have to do it on Windows.  It fundamentally relies on Microsoft's media frameworks (DirectShow, most probably, although on Vista/Win7 Media Foundation might be involved) to retrieve the necessary keys and give you proper playback of the videos.  I highly doubt it would work under Wine, as I haven't gotten DirectShow-based stuff working there.

Even worse, I've only ever been able to decrypt one or two WMV files, and that was a couple years ago (they weren't Amazon purchases either).  Subsequent updates to the encryption methods and Windows Media Player have rendered more recent attempts totally fruitless.  I absolutely abhor screen capping measures on stuff like this, but with how nasty WM DRM is, it seems to be the only well-workable solution.

In short, you'll probably just have to wait.



EDIT: Also, there's no way that the paid service from Canonical would handle this.  DRM is a very tightly-controlled entity, and circumvention is - in many countries, such as the US, under the DMCA - a criminal offense (although there are often provisions for personal use).  Providing a commercial framework would unmistakably run afoul of that, even if doing it yourself for private purposes falls into legally-grey territory.

---

### Post by pythonscript on 2009-10-05
> **qyot27 said:**
> You'd have to do it on Windows.

I'm starting to see that this is the case. I'm trying to work out playing them in virtualbox (under windows xp) but of course, I grumble because of the nature of such an awkward solution. Thanks for the help!

---

### Post by lukeiamyourfather on 2009-10-05
Its a little late now, but buying anything with DRM is a waste of money. Even if it did play on Linux there would probably come a day when the DRM servers are no longer running making the content useless again (e.g. Wal-Mart's online music store).

---

### Post by pythonscript on 2009-10-06
You just rent the movies (for a pretty low price) off Amazon, so that wasn't really an issue for me. None of my music is DRM protected, and that's really what I'm concerned about.

---

