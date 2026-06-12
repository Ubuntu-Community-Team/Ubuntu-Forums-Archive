---
title: "Which firefox plugin to use?"
date: 2006-08-30
forum: Multimedia &amp; Video
---

### Post by itchanddino on 2006-08-30
I'm running Xubuntu and it looks like I can install either VLC, Mplayer or Totem.  Does anyone know which one has the best performance (I have a really old Neomagic 3MB graphics card on a laptop) and/or has the least dependencies of the three?  Thanks!

---

### Post by neilp85 on 2006-08-30
I would recommend either VLC or Mplayer as they will play just about anything you throw at them. I know mplayer is the more popular of the two. If your worried about dependencies you can simulate the install then check what other packages you need then make your choice.
```
sudo apt-get install -s mozilla-plugin-vlc
sudo apt-get install -s mozilla-mplayer
```

---

### Post by fk4n on 2006-08-30
i tryed sudo apt-get install -s mozilla-mplayer

and it couldnt find the file.:(

---

### Post by fk4n on 2006-08-30
sorry post again. But this is the biggest problem with VLC

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=15090&stc=1&d=1156973719[/IMG]

---

### Post by thelocust on 2006-09-04
I tried all 3. I couldnt get Totem to play anything and VLC does not have any control options in firefox, you just watch the clip and when it over it goes away no pause or rewind or anything. So i went with mplayer and the firefox plugin it plays everything except wmv's i think, and has those options in firefox. (for wmv's i go with kaffeine).

---

### Post by stanz on 2006-09-05
> **fk4n said:**
> i tryed sudo apt-get install -s mozilla-mplayer

and it couldnt find the file.:(
Did you check out your sources list--?
Are Xubuntu & Dappers repos the same? Because I got it there.
Might Automatix be a help?...

---

