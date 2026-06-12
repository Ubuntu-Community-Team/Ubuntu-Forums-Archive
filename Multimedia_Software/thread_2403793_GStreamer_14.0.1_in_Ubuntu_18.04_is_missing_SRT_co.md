---
title: "GStreamer 14.0.1 in Ubuntu 18.04 is missing SRT codec"
date: 2018-10-16
forum: Multimedia Software
---

### Post by desdan on 2018-10-16
**SRT** (*Secure Reliable Transport*) was added to GStreamer in V **14.0** and **Ubuntu 18.04** contains GStreamer **14.0.1** - but the SRT support appears to be missing!  Any ideas on how can we add this?

---

### Post by Yellow Pasque on 2018-10-17
Probably need to get libsrt itself in Debian/Ubuntu first: [http://lists-archives.com/debian-devel/231438-libsrt-srt-secure-reliable-transport-add-debian-package.html](http://lists-archives.com/debian-devel/231438-libsrt-srt-secure-reliable-transport-add-debian-package.html)

---

### Post by desdan on 2018-10-18
Thank_s_ [URL="https://ubuntuforums.org/member.php?u=327594"][COLOR=#000000]Temüjin - we are looking into this. It seems like the right track!
[/COLOR][/URL][U][URL="https://ubuntuforums.org/member.php?u=327594"][COLOR=#000000]

[/COLOR][/URL][/U]

---

