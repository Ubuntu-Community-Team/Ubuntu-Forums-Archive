---
title: "Harmony One remote woes"
date: 2010-01-26
forum: Mythbuntu
---

### Post by dougsnell on 2010-01-26
After a rebuild of my system, I'm unable to get the commercial skip working.  I found the buttons are configured for "Advance" and "Replay", but can't figure out exactly what to do with the info.  I've tinkered around with remapping they keys within Myth and changing the settings in ~/.lirc/mythtv ... but no combination seems to work.  I recall having this issue every time I upgraded, but I always had the old files to reference as to what changed.

I also can't figure out how to remap the buttons on my Harmony One remote to "Home" and "End" ... which would be ideal, as it would prevent this issue for upgrades.

---

### Post by dougsnell on 2010-01-26
Found the issue.  The buttons were not showing up on most of the Google hits.  I found a listing of the PVR 350 codes, which is what I'm actually emulating (?) with the Harmony One remote.  I never thought a button would be valid with a slash in the name, but I note the one button is actually called "Asterisk", and no the "*".


-----


# Skip forward (10 min default)
begin
prog = mythtv
button = SkipForward
repeat = 3
config = End
end

# Skip backward (10 min default)
begin
prog = mythtv
button = Replay/SkipBackward
repeat = 3
config = Home
end

---

