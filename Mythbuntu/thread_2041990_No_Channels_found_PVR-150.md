---
title: "No Channels found PVR-150"
date: 2012-08-13
forum: Mythbuntu
---

### Post by k7_madman on 2012-08-13
I update to Mythbuntu 12, I have a PVR-150. When I do a scan for channels during setup, no channels are found. I have analog channel 3 input.

I tried increasing the setup scan time out to the max, but still not channels found

I tried different distros of mythtv, mythdora, LinHES....all have this same problem.

If I have the same pc and input setup and install an older version of Mythbuntu...channel 3 is found no problem. :confused:

Is this a known problem? How can I get this to work? Thanks

k7

---

### Post by klc5555 on 2012-08-14
> **k7_madman said:**
> I update to Mythbuntu 12, I have a PVR-150. When I do a scan for channels during setup, no channels are found. I have analog channel 3 input.

I tried increasing the setup scan time out to the max, but still not channels found

I tried different distros of mythtv, mythdora, LinHES....all have this same problem.

If I have the same pc and input setup and install an older version of Mythbuntu...channel 3 is found no problem. :confused:

Is this a known problem? How can I get this to work? Thanks

k7

Scanning has frequently been a mess in recent versions of Mythtv, even when it works.

Fortunately, there's no need to scan analog at all for Mythtv to work. The software is inherently capable of tuning the PVR-150 card to any analog channel 2 to 99. What an analog scan with a PVR-150 would generally do (when it worked) would be to create placeholder channel entries in the db for analog channels 2-99, whether there were signals on these channels or not.

But if all you need or want is channel 3, (because you do not need or want Mythtv to change channels for you on your channel 3 source), just add channel 3 manually in the Channel Editor. In the "Add channel" menu, on p. 1 the channel number is 3, on (about) p. 3 of that same menu, where it says "frequency or channel", the entry is also 3. And it's done.

If, however, you're actually going to set up lirc, etc., to change channels on your video source, the setup procedure will be different, but you still will not need to channel scan for anything that's coming through your PVR-150; any such channels can be added manually when necessary.

---

### Post by k7_madman on 2012-10-01
OK, that worked.  I manually added channel 3 and set the frequency channel 3.  After that I was able to tune in and get picture.  Thanks

---

