---
title: "Use Real Player in Firefox"
date: 2008-06-21
forum: Multimedia Software
---

### Post by ABD101 on 2008-06-21
I download Real Player 11 and have it working great, but I was using Totem Movie Player to play audio before. But I want real player to be the default. How can I change firefox so that it opens the files with real player. Or can i uninstall movie player from firefox?

thanks in advance.

---

### Post by atomkarinca on 2008-06-21
Under Edit > Preferences > Applications tab you can change default applications. The bad thing is you will probably have to edit them one by one.

---

### Post by ABD101 on 2008-06-21
I changed all of the applications that used Movieplayer and it still plays the audio with it. Is there a way to imbed real player to firefox in the terminal?

---

### Post by atomkarinca on 2008-06-21
If you're looking for an embedded real player it doesn't exist yet (at least not that I know of).

---

### Post by gandaran on 2008-06-21
> **ABD101 said:**
> I changed all of the applications that used Movieplayer and it still plays the audio with it. Is there a way to imbed real player to firefox in the terminal?

yes, you can do it in the terminal, run these commands one at a time. 

  cd /usr/lib/firefox-addons/plugins
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
  sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.

or full instructions here [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

but I think it's complete waste of time, embedded real-player only plays real audio and video, it will only show up where there's real video or audio streams.

---

### Post by ABD101 on 2008-06-22
Wowo thanks alot gandaran. You got it working for me. WOHOO.

---

