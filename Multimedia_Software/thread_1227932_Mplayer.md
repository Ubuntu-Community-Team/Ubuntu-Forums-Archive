---
title: "Mplayer"
date: 2009-07-31
forum: Multimedia Software
---

### Post by njb on 2009-07-31
Hye,

Have some problems to play HD Video 1080p with Mplayer.
Get this error message :

"Too many Videos paquets in the buffer 124 in 8.448.482 bytes"

:( NjB :(

---

### Post by andrew.46 on 2009-07-31
Hi njb,

> **njb said:**
> 
Have some problems to play HD Video 1080p with Mplayer.
Get this error message :

"Too many Videos paquets in the buffer 124 in 8.448.482 bytes"

Can you have a look at which version of MPlayer you are using? An easy way is to run:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer | head -n 1[/COLOR]**
MPlayer SVN-r29461-4.2.4 (C) 2000-2009 MPlayer Team

```

Also have a try at the same video after disabling any fancy desktop effects.

Andrew

**Edit:** A final thought: do you have a recent model nvidia card? This may benefit from vdpau that features in newer builds of mplayer.

---

