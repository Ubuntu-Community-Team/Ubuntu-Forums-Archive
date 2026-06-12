---
title: "Flash on Android"
date: 2010-06-19
forum: Mythbuntu
---

### Post by betolley on 2010-06-19
I have froyo on my droid so I have flash.  Then I upgraded from Mythdora 10 server and formated and installed mythbuntu.  The only problem I have is that I am unable to play any of the flash movies in mythweb(I could with mythdora).  I think it has something to do with the browser not liking the symlinks.  I can't even download the flv files if I try.  SO  where are the flv files saved on the mythbuntu server?  I have looked and searched everywhere.  I was going to change apache to add it as a folder and fix the recorded php to point to the new location.

---

### Post by tmcgary on 2010-06-20
betolley,

I am pretty new with alot of this but here goes:

when you click on the links in mythweb from your android device, is there an error, a download screen that doesn't work or just nothing happens? In mythweb does it list all the files/folders with the titles of the videos or does it mention anything about storage groups? Are all the videos in flv format or are there other types?

---

### Post by betolley on 2010-06-20
i get http://fileserver.doesntexist.org:80//mythweb/pl/stream/2618/1275192000.flv>  can not be played.  Again I can't even download in android's browser if I try to dl the file.  It works fine from pcs.

---

### Post by nickrout on 2010-06-20
> **betolley said:**
> i get http://fileserver.doesntexist.org:80//mythweb/pl/stream/2618/1275192000.flv>  can not be played.  Again I can't even download in android's browser if I try to dl the file.  It works fine from pcs.

The flv file is not saved anywhere (except temporarily perhaps). It is created on the fly by one of the mythweb scripts, using ffmpeg.

---

### Post by betolley on 2010-06-21
Any idea which scripts? I could alter it to save the file also.

---

### Post by nickrout on 2010-06-21
dpkg -L mythweb will list all the scripts. Having had a quick look, it may have changed since I last looked at it.

---

