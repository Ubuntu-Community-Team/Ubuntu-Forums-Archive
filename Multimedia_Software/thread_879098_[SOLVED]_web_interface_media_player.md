---
title: "[SOLVED] web interface media player"
date: 2008-08-03
forum: Multimedia Software
---

### Post by stefansjs on 2008-08-03
I am wondering if anyone knows any media player(s) that can be controlled through some sort of web interface.  Preferably it would have distinctly separate queue and playlist functionality, but at this point I'm not going to be too picky.  Anything at all that can be controlled through a web browser, but just to clarify, I want to remotely control the media player, not stream from it.
thanks

---

### Post by kostkon on 2008-08-03
> **stefansjs said:**
> I am wondering if anyone knows any media player(s) that can be controlled through some sort of web interface.  Preferably it would have distinctly separate queue and playlist functionality, but at this point I'm not going to be too picky.  Anything at all that can be controlled through a web browser, but just to clarify, I want to remotely control the media player, not stream from it.
thanks
You can use *Rhythmbox*, which is the default media player in *Ubuntu* and so you'll not need to install another one, with one the following plugins:

- [*Rhythmweb*]("http://web.vee.net/projects/rhythmweb/")
or
- [*Remuco*]("http://remuco.sourceforge.net") (if you want to control it from a mobile device).

To use *Rhythmweb*, download and extract the archive, copy the *rhythmweb* folder to *~/.gnome2/rhythmbox/plugins*, open *Rhythmbox*, go to the *Edit > Plugins* menu and enable the plugin.

Then you can browse to the machine running it (it will listen on port 8000), for example like this: 
```
http://yoursystem:8000/
```

To install and use *Remuco*, check [here]("http://remuco.sourceforge.net/index.php/Getting_Started_on_Ubuntu").

I Hope that helps you.

---

### Post by kostkon on 2008-08-03
I want to add that *Rhythmbox* cannot play videos. I assumed you mean a music player.

---

### Post by stefansjs on 2008-08-03
Thank you.  The Rhythmweb plugin is exactly what I wanted.

---

