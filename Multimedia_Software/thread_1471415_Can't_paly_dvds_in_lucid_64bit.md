---
title: "Can't paly dvds in lucid 64bit"
date: 2010-05-03
forum: Multimedia Software
---

### Post by w1ll1am on 2010-05-03
Hello i just updated to lucid and i went to install medibuntu and following the instructions on this page [https://help.ubuntu.com/community/Medibuntu ]("https://help.ubuntu.com/community/Medibuntu")just like i did in Karmic but after i have done everything that i had to do in Karmic to get it to work i tried to play a dvd in totem and it pops up and says 

The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported.

No packages with the requested plugins found 

The requested plugins are:

DVD subpicture decoder

I click ok and then the dvd starts to play and says internal data flow error

If anyone can help it would be nice thanks

---

### Post by axel206 on 2010-05-03
Read the DVD playback section of this guide:

[Ubuntu Lucid Lynx 10.04 Post Installation Guide](http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide)

---

### Post by w1ll1am on 2010-05-03
Thanks i downloaded vlc and it works every now and then there is a slight glitch but nothing too bad

---

### Post by axel206 on 2010-05-03
Actually I was referring to this [http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide#dvd-playback](http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide#dvd-playback) but if you are ok with VLC no problem. :)

---

### Post by mknepher on 2010-05-07
I've got the same issue as the original poster, after taking steps to install libdvdcss2 as outlined on the linked page. First totem searches for DVD subpicture decoder, can't find suitable plugin package, then starts to play the movie, but craps out with internal data error. This is a nasty bit of regression.

---

### Post by mknepher on 2010-05-08
Following up, I tried installing the fluendo codec pack, and totem stopped looking for codecs, and started playing the movie of the dvd I tried. However, it was playing the wrong audio track (French track of "Moon"). Trying to change audio tracks resulted in silence, and totem would not go to the dvd menu or switch chapters. 

I then uninstalled the fluendo codec pack, and installed gstreamer0.10-fluendo-mpegmux and gstreamer0.10-fluendo-mpegdemux. Now the movie plays with the correct soundtrack, but menus still don't work.

---

### Post by pgwulfing on 2010-05-09
(I hope you mean can't PLAY DVD's 

I have a similar problem. 

I have a DVD which plays fine under Karmic 32, but which doesn't decode properly under Lucid 64. It opens, can be navigated, VLC TRIES to play it, and even displays some recognizable bits of the film. But the screen is covered with improperly decoded blocks of noise and randomness. The sound is partially there too, but skips badly. 

Same story with Movie Player.

XINE refuses to continue at all when it gets to the encrypted part, and gives a message about needing libdvdcss2 (which is, of course, installed).

What's going on? Is my processor not really high performance enough to do this in 64 bit mode? Should I try Lucid 32? Is libdvdcss2 lower performance in Lucid(64)? Why does this disc play just fine under Karmic and Vista (both 32 bit) but not Lucid?

I've tried to reinstall all the restricted stuff, but to no avail. 

I want to use this machine specifically for media playing, and under Karmic, everything played fine. 

Any ideas?

Hardware is Toshiba Satellite P105-S6197, Core2 Duo T5200 1.6GHz, 3GB RAM

---

### Post by w1ll1am on 2010-05-13
> **mknepher said:**
> Following up, I tried installing the fluendo codec pack, and totem stopped looking for codecs, and started playing the movie of the dvd I tried. However, it was playing the wrong audio track (French track of "Moon"). Trying to change audio tracks resulted in silence, and totem would not go to the dvd menu or switch chapters. 
 
I then uninstalled the fluendo codec pack, and installed gstreamer0.10-fluendo-mpegmux and gstreamer0.10-fluendo-mpegdemux. Now the movie plays with the correct soundtrack, but menus still don't work.
 
 
You should try out VLC it worked for me. Let me know.

---

### Post by w1ll1am on 2010-05-13
> **pgwulfing said:**
> (I hope you mean can't PLAY DVD's 
 
I have a similar problem. 
 
I have a DVD which plays fine under Karmic 32, but which doesn't decode properly under Lucid 64. It opens, can be navigated, VLC TRIES to play it, and even displays some recognizable bits of the film. But the screen is covered with improperly decoded blocks of noise and randomness. The sound is partially there too, but skips badly. 
 
Same story with Movie Player.
 
XINE refuses to continue at all when it gets to the encrypted part, and gives a message about needing libdvdcss2 (which is, of course, installed).
 
What's going on? Is my processor not really high performance enough to do this in 64 bit mode? Should I try Lucid 32? Is libdvdcss2 lower performance in Lucid(64)? Why does this disc play just fine under Karmic and Vista (both 32 bit) but not Lucid?
 
I've tried to reinstall all the restricted stuff, but to no avail. 
 
I want to use this machine specifically for media playing, and under Karmic, everything played fine. 
 
Any ideas?
 
Hardware is Toshiba Satellite P105-S6197, Core2 Duo T5200 1.6GHz, 3GB RAM
 
 
If you have no reason to use 64-bit and you don't have all kinds of files to back up matbe the 32 is worth a try it seems to have alot less problems than the 64 bit. hope this helps

---

### Post by yurx cherio on 2010-07-05
Same problem occurs when trying to burn video DVD with Brasero. While trying to import VOB files Brasero raises an error complaining on the missing plugin (see screenshot)

No packages with the requested plugins found
The requested plugins are:
DVD subpicture decoder

---

### Post by morbo2010 on 2010-08-31
Has anybody found a solution to this other than VLC?

I seem to be getting a very similar problem with lucid 10.04 32-bit.

Followed all steps that are recommended in Ubuntu documentation for getting DVD playback to work, but alas I get the "Internal data stream error" message.

---

### Post by jmore9 on 2010-08-31
Right after i finish the install i go here and load what i need from the list :

Comprehensive Multimedia & Video Howto

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Everything i need gets installed from this howto.  Hope it helps you some.

---

