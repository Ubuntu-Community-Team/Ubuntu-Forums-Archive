---
title: "Unable to get Tascam US-122 audio interface working"
date: 2012-12-25
forum: Multimedia Software
---

### Post by eboats on 2012-12-25
I'm trying to get my Tascam US-122 USB audio interface working with Ubuntu 12.10 based on the "Installation (newer releases)"  instructions at :  

[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

At Step 2, I was able to find and install the 
alsa-firmware-1.0.25.tar.bz2

But at Step 7, when I sudo usx2yloader

I get the error : No USX2Y-compatible cards found

I tried the suggested fix :

sudo ln -s /usr/share/alsa/firmware/usx2yloader /lib/firmware/usx2yloader

but get the same error.  Any ideas?

---

### Post by eboats on 2012-12-26
As an update, I was able to get around this error, and now the Tascam US-122 lights up when I run    sudo usx2yloader
However, I'm not able to get any sound out of the US-122 even though  
it lights up.  When I go to System Settings/Sound, I first
don't see the Tascam US-122 in the Output tab, but after unplugging/re-plugging
the Tascam back in I do see it.  But no sound.  Oddly, I don't
see my Dell internal soundcard in the Output tab, even though I can hear the internal soundcard
just fine.

Any idea?

---

