---
title: "&quot;Error was encountered while displaying video&quot; when changing channels"
date: 2009-10-15
forum: Mythbuntu
---

### Post by deepagnv on 2009-10-15
Hello
I set up Mythbuntu and MythTV yesterday and I get to watch just one channel. When I try to change the channel, I get the error: "Error was encountered while displaying video" and I get kicked back to the main screen. 

This is what I see in the log after I change the channel:

2009-10-15 11:21:09.213 WriteAudio: buffer underrun
2009-10-15 11:21:10.760 NVP: Prebuffer wait timed out 10 times.
2009-10-15 11:21:12.443 NVP: Prebuffer wait timed out 10 times.
2009-10-15 11:21:14.127 NVP: Prebuffer wait timed out 10 times.
2009-10-15 11:21:15.137 MythSocket(7fc7e92af450:24): readStringList: Error, timeout (quick).
2009-10-15 11:21:15.137 RemoteEncoder::SendReceiveStringList(): No response.
2009-10-15 11:21:15.142 LiveTVChain(live-mythhost-2009-10-15T11:20:34): SwitchTo() not switching to current
2009-10-15 11:21:15.146 TV: Attempting to change from WatchingLiveTV to None
2009-10-15 11:21:15.170 MythSocket(7fc7e92af450:-1): writeStringList: Error, called with unconnected socket.
2009-10-15 11:21:15.170 MythSocket(7fc7e92af450:-1): readStringList: Error, called with unconnected socket.
2009-10-15 11:21:15.170 RemoteEncoder::SendReceiveStringList(): No response.
2009-10-15 11:21:15.221 TV: Changing from WatchingLiveTV to None
2009-10-15 11:21:15.245 DPMS Reactivated.


Can any of you comment on this and help me find a solution? I did a search for similar problems but they were unresolved. 

Thanks in advance!

---

### Post by the_pod on 2009-10-15
Not sure if this is the situation you're having, but I've had that happen on a few occasions.  I came to the conclusion that it happened exclusively when I would go to "live tv" and then attempt to change the channel prior to the current channel getting fully tuned.  When I would wait for the picture of the current channel to show up (typically 3-5 seconds for me using a QAM signal) then I didn't have the problem.

If you're having this problem always then this is most likely not the solution but fwiw...

---

### Post by SiHa on 2009-10-15
> **the_pod said:**
> ...I came to the conclusion that it happened exclusively when I would go to "live tv" and then attempt to change the channel prior to the current channel getting fully tuned...

Yes, I get this too, same if I select 'Watch TV' by mistake, and try to escape back to the menu before it's got a channel lock.

---

### Post by AKADAP on 2009-10-15
I have also seen this occur (along with several other varieties of crash) when attempting to change channel while mythfilldatabase is thrashing the hard disk in the background.

---

