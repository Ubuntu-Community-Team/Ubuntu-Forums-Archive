---
title: "why don't all music projects use the client/server model?"
date: 2010-02-07
forum: Multimedia Software
---

### Post by yekibud on 2010-02-07
I recently encountered what seems to be a fundamental limitation of Ubuntu's default music player, Rhythmbox.  I have multiple computers in my household, as well as multiple screens attached to the same user session.  It appears you cannot instantiate multiple instances of the same Rhythmbox client to control it from other screens, nor can you connect to any service over your LAN.

Then I came across Music Player Daemon (MPD) and it's host of client sw alternatives, such as Sonata and GMPC, and my problems were solved.  And I thought, "this is the way it should be done."

**So my question is: why don't all music projects use the client/server model?**  And why isn't the default Ubuntu music player an MPD client, instead of rhthmbox?  It's true they don't seem to be as full featured clients at the moment - but that can be improved upon.

Are there some philosophical principals I'm missing that caused the popular music players such as Rhythmbox and Banshee not to go the client/server direction?

---

### Post by tgalati4 on 2010-02-07
Rhythmbox has music sharing through DAAP.  You have to enable a plug-in.  Each machine with Rhythmbox will see the shares of the other machines.  iTunes will also see the shares.

MPD and it's various clients is also a good solution.  It was developed before the DAAP protocols.

---

### Post by yekibud on 2010-02-14
So I looked at DAAP and DLNA/UPnP - and they just enable means for sharing music lists/files, from what I can tell - _not_ sharing control of the music process.  This seems like such a beneficial set-up - I can't imagine I'm the only one who has music playing in the house and goes into another room with a laptop, media center, or other sort of terminal and would like to pause the track, select a different song, etc.

This seems like a powerful feature that you would want to include in any music player.  I still don't understand why it's not a part of Rhythmbox or there isn't a good alternative with client/server capability set as the Ubuntu default.

---

