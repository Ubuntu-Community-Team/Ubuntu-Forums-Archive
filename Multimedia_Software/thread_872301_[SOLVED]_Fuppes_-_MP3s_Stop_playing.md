---
title: "[SOLVED] Fuppes - MP3s Stop playing"
date: 2008-07-27
forum: Multimedia Software
---

### Post by BrokenKingpin on 2008-07-27
I have Fuppes installed on Ubuntu 8.04 streaming to my Xbox 360. When I play MP3s the song starts off playing fine, but about half way through the song the sound cuts out or the song restarts. The weird thing about it is that the sound second counter keeps going when it does this. Has anyone ran into this or know a solution? My video playback is working perfectly. I have attached my config files. Thanks!

---

### Post by BrokenKingpin on 2008-07-28
Sorry for the double post, but it seems to be doing the same thing with my videos too (I guess I didn't test them enough before). I am thinking maybe my wireless connection might be cutting out. I will try a wired connection to see if that helps.

---

### Post by BrokenKingpin on 2008-07-29
I have now confirmed it is definitly my wirless connection. I tried a wired connection and everything runs perfectly. 

When I first installed Ubuntu I had to enable the restricted Brodcom driver and after that I was able to connect to my router just fine using the defaul network manager (I am assuming it is using Ndiswrapper behind the scenes, but I am not sure). I sometimes see the bitrate on the connection go down to 2 Mb/s, but I still run into the issue when it's at 54. Does anyone have any idea of what the problem is?

---

### Post by BrokenKingpin on 2008-08-04
Turns out I had the wireless driver installed with fwcutter. I reinstalled the driver, only this time with Ndiswrapper... and now it works perfectly (I am actually getting 54MB/s.

---

