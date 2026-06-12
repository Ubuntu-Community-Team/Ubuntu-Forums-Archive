---
title: "Odd audio problem..."
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by Matakoo on 2007-06-24
The other day my sound started to act up. Or rather, it started to do so in some specific applications. It used to work great in every app I use, but all of a sudden the noise became distorted, and crackling if I tried to view movies in Mplayer or VLC. It still worked in Kaffeine, but I prefer not to use Kaffeine whenever possible (partly because it tends to segfault when it's done playing a quicktime movie and partly because it's not all that good at re-scaling video). The usual system sounds continued to work, as did Amarok.

However, when I reconfigured the programs in question to use OSS instead, the problem vanished. Problem solved, sort of. Kinda annoying that the multimedia-keys of my keyboard are no longer system-wide (apps using OSS refuses to turn the volume up and down anymore, although they do react on mute). 

Still, I really can not understand why the problem surfaced in the first place. It has worked flawlessly since it was installed, and now this happens. The only reason I can think of, and this is admittedly a stretch. The upgrade to the latest Amarok the other day. Now, I don't know the internals of how the Linux soundsystems work but it seems very far-fetched that an upgrade to Amarok (from the repos, albeit in the backports section IIRC) would affect the sound output of other applications.

Any thoughts?

---

