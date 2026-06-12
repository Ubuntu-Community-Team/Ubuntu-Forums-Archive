---
title: "Veetle and Ubuntu 10.10"
date: 2010-10-17
forum: Multimedia Software
---

### Post by kmoneylongshanks on 2010-10-17
There was a fix to get Veetle working on 10.04, but it doesn't seem to be working anymore.  I had to edit that vlc file in the .vootle folder every time I wanted to watch Veetle, but now that does not even work.  Does anyone have a good fix for 10.10?  I'm talking about fixing the sound lag BTW.

---

### Post by nelson2006 on 2010-10-31
> **kmoneylongshanks said:**
> There was a fix to get Veetle working on 10.04, but it doesn't seem to be working anymore.  I had to edit that vlc file in the .vootle folder every time I wanted to watch Veetle, but now that does not even work.  Does anyone have a good fix for 10.10?  I'm talking about fixing the sound lag BTW.

Hey kmoneylongshanks, I found this fix on a veetle forum but there's still about a one second sound delay. 

#! /bin/sh
exec ~/.veetle_vlc/vlcori --aout oss "$@"

Replace it for:

#! /bin/sh
exec ~/.veetle_vlc/vlcori --alsadev 0 "$@"

---

### Post by emzbuntu on 2011-03-21
Hi, any update on this? 

Would be very much appreciated.

Thanks!

---

### Post by Mckayv on 2011-04-02
Any further ideas with this one? Same situation here, have tried above mentioned solution, but when running the alsa script as the vlc file, firefox freezes and greys out, and I have to quit. audio works with the oss script, but there is a significant delay. I'm at my wits end here, any help would be appreciated.

---

### Post by emzbuntu on 2011-04-03
if firefox freezes, you can take a look at the following site. 

It did work for me but i still have a 1 sec. delay between audio and video...
[http://www.lziegler.com/wordpress/?p=108](http://www.lziegler.com/wordpress/?p=108)

---

