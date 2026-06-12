---
title: "[SOLVED] Totem and YouTube"
date: 2008-05-27
forum: Multimedia Software
---

### Post by thelugnut on 2008-05-27
I can't seem to get Totem to play the YouTube vids.When I do the search the results come up but then I get a message saying:

> Totem cannot play this type of media (YouTube) because you do not have the appropriate plugins to handle it.

Please install the necessary plugins and restart Totem to be able to play this media.

Will someone please explain to me what I am supposed to do? Thanks a lot.

---

### Post by wolfen69 on 2008-05-27
are you trying to play youtube vids in firefox? if so, you need the flashplugin.
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by thelugnut on 2008-05-27
No, I am trying to play YouTube in Totem.

---

### Post by gandaran on 2008-05-27
> **thelugnut said:**
> No, I am trying to play YouTube in Totem.

using the youtube plugin in totem, right? have you installed the correct gstreamer plugins? install all the gstreamer plugins in add/remove programs, or in synaptic, totem should play .flv media files after installing the necessary codecs.

---

### Post by DMK62 on 2008-05-27
Ubuntu Restricted Extras in Add Remove or Synaptic should also take care of it for you. It will also install flash ( if not already installed ) and a few other packages.

Dale

---

### Post by Bablefish on 2008-05-27
You might have to play that file on your browser

---

### Post by thelugnut on 2008-05-28
I really appreciate the responses. Thanks to all of you.

DMK62 nailed it down, and a special thanks goes out to that person.

This is really a great forum.

Thanks again to everybody.

---

### Post by OpenFish on 2008-05-28
if any one is still watching this thread then now u have the correct libs to play the vids with totem u can now use VLC to convert them so they will play on ur portable media device (ipod/etc) (.mp4's) if vlc dosnt do it the first time do it again it! vlc usaly likes u to do it 6/7 times before it works perfectly!! no idea why but when it dose work its the best!!

---

