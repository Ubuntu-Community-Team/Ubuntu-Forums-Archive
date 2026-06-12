---
title: "Ubuntu Studio - is the old wiki preparation still needed??"
date: 2007-05-12
forum: Multimedia Production
---

### Post by jondecker76 on 2007-05-12
Do we still have to follow the ubuntu studio preparation guide off of the wiki [https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation")
?

For example, do we still have to edit /etc/security/limits.conf to enable realtime access for applications? Do we still have to modify /etc/modules to load the alsa sequencer? etc etc

Or is this already done in the release version of Ubuntu Studio?

thanks

Jon

---

### Post by MetalMusicAddict on 2007-05-13
> **jondecker76 said:**
> Do we still have to follow the ubuntu studio preparation guide off of the wiki [https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation")
?

For example, do we still have to edit /etc/security/limits.conf to enable realtime access for applications? Do we still have to modify /etc/modules to load the alsa sequencer? etc etc

Or is this already done in the release version of Ubuntu Studio?

thanks

Jon

If you use our installer we set "@audio - rtprio 99" as thats the one that really applies to all users. The others can be specific to a users system.

---

### Post by jondecker76 on 2007-05-13
so it would be a good measure to follow that guide if you are using an upgraded version of Feisty?

Also, what about the Alsa Sequencer? Should we have that load in /etc/modules?

---

