---
title: "Divx web player help"
date: 2013-05-14
forum: Multimedia Software
---

### Post by Dinocookies on 2013-05-14
I'm new to linux and was hoping somone could help me with a problem. My seedbox provider installed Divx web player plugin in their box so that I can stream  from it, but  I cant figure out how to install Divx web player on linux :(

---

### Post by monkeybrain2012 on 2013-05-15
Use  Firefox and install the gecko-mediaplayer. 

```
sudo apt-get install gecko-mediaplayer
```

Edited; Opps sorry, misunderstood your question. forget the above. :)

---

### Post by SeijiSensei on 2013-05-15
That's the right answer if you want to watch streamed DivX materials with a browser.  If you are looking for a standalone player, any mplayer-based media player supports DivX.  I recommend **smplayer** which you can install from the Ubuntu repositories.

If you need to connect to a URL, use File > URL in smplayer.

---

### Post by Dinocookies on 2013-05-19
Ah ok thx guys. One more question how to I remove the vlc plugin from firefox? I cant seem to figure out how to access the extension.

---

### Post by monkeybrain2012 on 2013-05-20
Open Firefox, go to tools > plugins and disable it and then restart Firefox. You can remove the totem-mozilla from the software centre, but I would keep it around. It plays quicktime better than gecko-mediaplayer (so you can disable gecko's quicktime plugin from tools > plugins)

---

