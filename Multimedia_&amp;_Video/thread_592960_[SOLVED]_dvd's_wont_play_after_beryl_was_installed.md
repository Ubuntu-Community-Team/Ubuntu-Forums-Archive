---
title: "[SOLVED] dvd's wont play after beryl was installed on x3100"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by doppis on 2007-10-26
I can longer get dvd's, mpegs, wmv to play after I enabled desktop effects and installed beryl, I tried many different players and I have search through all the threads about the different codecs I need and I have them all.  I am using the 1420n with the x3100, I tweaked it a little to get the effects and beryl working properly by following this post 

[http://ubuntuforums.org/showthread.php?t=506744&highlight=x3100+desktop+effects](http://ubuntuforums.org/showthread.php?t=506744&highlight=x3100+desktop+effects)

If anyone has a clue your help would be great.

I tried kaffeine and I get audio but no video, that is about as far as I have got.

Seems like this fixed it

sudo apt-get autoremove
sudo apt-get install libgl1-mesa-dri

---

