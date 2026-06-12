---
title: "Play DVD"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by amdalex on 2007-02-20
How do I play DVDs with KDE and GNOME? I can't figure out how.

---

### Post by RomeReactor on 2007-02-20
Hi. If you're on Ubuntu Edgy, then [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability")  guide will help you with it; these are the respective pages for [Dapper]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_DVD_playback_capability")  and [Breezy]("http://ubuntuguide.org/wiki/Ubuntu#How_to_install_DVD_playback_capability"). For Gnome, use Totem-Xine as the guides say; for KDE, use Kaffeine-Xine: In the guides, substitute

```
sudo aptitude install totem-xine
```

with

```
sudo aptitude install kaffeine-xine
```

Then use Totem in Gnome or Kaffeine in KDE.

---

