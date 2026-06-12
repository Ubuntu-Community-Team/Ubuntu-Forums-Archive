---
title: "Looking For a really good flash player and a good movie player"
date: 2008-10-26
forum: Multimedia Software
---

### Post by Chloedog industrial on 2008-10-26
Ya i'm looking for a a good flash player and a good movie player the torrent i'm down loading look like crap and when ever i watch you tube it like watching a slide show the video is moving so slow. I might be my slow computer too if that's the case how do i turn down the resolution on the flash and movie player so it not pain full to watch? Oh help me great Ubuntu Wizards.

---

### Post by eternalnewbee on 2008-10-26
For flash, try:
```
sudo apt-get install libflashsupport
```
As for the movie player, that's a matter of personal choice. mine is vlc.

---

### Post by Chloedog industrial on 2008-10-26
sorry I'm really new how do u run a command?? like where do you go?

---

### Post by Chloedog industrial on 2008-10-26
also vic won't install. i tried multiple places to down load from and i keep geting this  Error: Dependency is not satisfiable: vic-nox

---

### Post by gandaran on 2008-10-26
> **Chloedog industrial said:**
> Ya i'm looking for a a good flash player and a good movie player the torrent i'm down loading look like crap and when ever i watch you tube it like watching a slide show the video is moving so slow. I might be my slow computer too if that's the case how do i turn down the resolution on the flash and movie player so it not pain full to watch? Oh help me great Ubuntu Wizards.


what did you install for firefox flash? adobe flash or something else
adobe flash usually works fine, some users have problems, if you have a problem with adobe flash, you'll have to figure out why it's not working properly
to install vlc or any other player, just open synaptic package manager scroll down to vlc mark for install and click the apply button.
don't install libflashsupport, it won't help you and can make firefox crash, libflashsupport is just a fix for pulseaudio and adobe flash 9 sound bug, don't need it if your system sound is set to alsa or if you have the new adobe flash 10 installed

---

### Post by cariboo on 2008-10-26
To install programs go to Applications-->Add/Remove Programs, make sure Show All Open Source Programs is selected, or System--Administration--Synaptic Package Manager. You don't need to download anything from some random web site. The last time I look there were over 20,000 packages in the repositories, not all of them are programs, but if you can't find something to do what you need in the repositories, then it probably isn't available.

Jim

---

