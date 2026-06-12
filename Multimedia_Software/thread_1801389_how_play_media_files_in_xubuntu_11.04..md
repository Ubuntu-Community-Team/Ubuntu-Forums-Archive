---
title: "how play media files in xubuntu 11.04."
date: 2011-07-10
forum: Multimedia Software
---

### Post by vikash_chandola on 2011-07-10
How to play audio video files. When i try to run these files it says no suitable plug in found:confused:. What should i do. I am using xubuntu 11.04. Should i need to download vlc media player.
I am completely newcomer to Linux so try to answer in very simple way.
Thanks for any kind of help.

---

### Post by Jose Catre-Vandis on 2011-07-10
Sounds like you are trying to play media via your browser?

First off install:
```
sudo apt-get install xubuntu-restricted-extras
```

Next get the flash player plugin from Adobe
```
http://get.adobe.com/flashplayer/
```

If you want vlc then install from the repos:
```
sudo apt-get update
sudo apt-get install vlc
```

That should get you going....

---

### Post by papibe on 2011-07-10
Go to Applications -> Software Center, and install the package 'xubuntu-restricted-extras'. Try playing your files again.

If that does not work, do the same and install VLC. VLC should play it. If not, while trying to play it with it go to VLC -> Tools -> Codec Information, and post what is says there.

Regards.

---

