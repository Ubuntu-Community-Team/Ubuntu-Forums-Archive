---
title: "MythTV Recording, but recorded shows not visable for playback"
date: 2007-08-03
forum: Multimedia &amp; Video
---

### Post by black_beard on 2007-08-03
I'm in the process of setting up a MythTV box using Ubuntu 7.04.  All in all, things have gone pretty smoothly though either reading the guides or through a lot of use with google.  I just have one issue that I haven't been able to quite figure out...

The problem is that I can not see any of the programs that have been recorded by going through Media Library->Watch Recordings.  

What I do see when I go there is small snippets of recorded programs that look as if they were recorded as I channel surfed.

However, I can see the *mpg files under /var/lib/mythtv/recordings.  I can also see the shows listed in MythWeb as well as if I go to Manage Recordings->Previously Recorded. I can even burn them to DVD.

I think it might be a permission problem, however the more likely case is that it is a PEBKAC issue.  Don't suppose anyone has any ideas on why this is happening or how to fix it? 

PS.  If it helps, I'm using a PVR-500 + PVR-350 (Though I'm only using the PVR-500).

---

### Post by black_beard on 2007-08-03
I'm not sure what caused the issue, but it seems to have worked it's way out.

I deleted all the 'temp' recorded shows and the frontend locked up.  After restarting it after I killed the process, all seems right in the world and the recorded videos are now present.

---

