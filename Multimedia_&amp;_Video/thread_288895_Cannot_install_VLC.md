---
title: "Cannot install VLC"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by whoosh on 2006-10-30
I'm having some dependency problems when tryign to install VLC.  I think something happened when I tried to install Quod Libet and mutagen and now it's kinda screwing a lot of stuff up.  

When I try to install VLC, i get this error:

```
E: python-mutagen: subprocess post-installation script returned error exit status 1
E: exfalso: dependency problems - leaving unconfigured
E: quodlibet: dependency problems - leaving unconfigured

```

Any help?

---

### Post by blissfulpenguin on 2006-10-30
This may not sound like much, but what I would do in your situation is try uninstalling both mutagen and quodlibet, and then installing vlc.  it should be aware of its own dependencies in apt, so you shouldn't have any problems there.  after vlc is installed successfully ( i would definitely test it), you might try re-installing mutagen and quod libet.  but one caveat - I have no idea what either of these packages contain (mut et quod), so it might be a good idea to watch during their install for "replacement packages."  i noticed with gstreamer and xine you have a choice between the two.  but then again, this was back during the early dapper days.

once again - not an expert.  hope this helps!

---

