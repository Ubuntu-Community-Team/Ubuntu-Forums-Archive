---
title: "Any way to automate Hue setting?"
date: 2009-10-12
forum: Mythbuntu
---

### Post by bcg30506 on 2009-10-12
Until VDPAU is fixed so lips do not get out of sync after a time or pausing, I have to change my playback profile from VDPAU to Slim for regular TV watching then back to VDPAU for watching HD videos.  The only other issue with doing this is the colors are all wrong when changing profiles.  VDPAU seems to need Hue to be 0-5% for skin tones to look natural.  Slim (or any other profile) needs it to be at 50%.  This requires a lot of remote button presses.  Is there any way the playback profile can just remember these or a way to shorten the time to change it from the remote?

---

### Post by bcg30506 on 2009-10-12
I may have figured out half a solution myself.

toggleHue script:
```

#!/bin/bash
echo "update settings set data=if(data='5','50','5') where hostname='mythbox' and value='PlaybackHue';" | /home/me/db

```

in my .lircrc file:
```

# Change Hue
begin
prog = irexec
button = Blue
config = /home/me/toggleHue
end

```

This successfully changes the Hue setting for this frontend when pressing the Blue button on the Hauppague remote, but does not change what I see on screen while watching TV.  If I do it before starting a video, it is fine.  Any way to update the playback Hue with one button press without exiting what I'm watching?

---

