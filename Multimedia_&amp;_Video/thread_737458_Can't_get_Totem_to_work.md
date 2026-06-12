---
title: "Can't get Totem to work"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by Wittgenstein on 2008-03-27
Hi, I'm running Gutsy on a ThinkPad R60, most things work fine, but I am not able to play DVD's (movies). When installing a DVD it starts running and opens Totem correctly, but then it complains about not finding the right plugins. I've installed all the gstreamer plugins (several times!), but it does not help!

Anybody?

---

### Post by Tomatz on 2008-03-27
In a terminal type:

**sudo apt-get install libdvdcss2**

Now your dvd's should play :)


Failing that vlc should play them "out of the box".

---

### Post by Wittgenstein on 2008-03-27
libdvdcss2 allready installed...

---

### Post by Tomatz on 2008-03-27
Strange?

Just use vlc its better at playing dvd's anyway.

---

### Post by Wittgenstein on 2008-03-27
vlc??

---

### Post by xc3RnbFO8P on 2008-03-27
Install this:
[http://ubuntuforums.org/showpost.php?p=4565970&postcount=4]("http://ubuntuforums.org/showpost.php?p=4565970&postcount=4")

---

### Post by Tomatz on 2008-03-27
sudo apt-get install vlc

Its a media player with all codecs needed in one package :)


*P.s the **regionset** package may get totem working*

---

### Post by Wittgenstein on 2008-03-30
All of a sudden both Totem and vlc are working!!:) Don't know what happened (maybe what the laptop needed was a restart...?) Thanks for the help.

What do you recomend, vlc or Totem and why?

---

### Post by Tomatz on 2008-03-30
> **Wittgenstein said:**
> All of a sudden both Totem and vlc are working!!:) Don't know what happened (maybe what the laptop needed was a restart...?) Thanks for the help.

What do you recomend, vlc or Totem and why?

It's all down to personal choice. I prefer vlc because it plays just about everything out of the box but with not much effort you can get totem to do the same.

Try them both out and see what you like most :)

P.s 

Vlc looks a bit basic but you can get some cool skins [here]("http://www.videolan.org/vlc/skins.php")

---

