---
title: "Mythtranscode fails (unknown video codec) / Checking installed codecs"
date: 2007-01-26
forum: Multimedia &amp; Video
---

### Post by sfpiano on 2007-01-26
The transcode kept failing when it ran automatically, so I tried doing it manually from the command line: mythtranscode -i file.mpg from the command line, and I got an error saying "unknown video codec: "; there was just empty space after the colon.

My second question is how I can check which codecs I have installed in the first place.

---

### Post by davez0r on 2008-01-25
> **sfpiano said:**
> The transcode kept failing when it ran automatically, so I tried doing it manually from the command line: mythtranscode -i file.mpg from the command line, and I got an error saying "unknown video codec: "; there was just empty space after the colon.

My second question is how I can check which codecs I have installed in the first place.

I have been having the same issue with Mythbuntu 7.10.  Here's what I've found...

You can actually run a manual mythtranscode through the mythfrontend by doing:
Manage Recordings -> Delete Recordings -> [Select a recording]  -> Job Options -> Begin Transcoding -> High Quality

This will run a transcode with the settings defined in your recording profiles found under:
Utilities/Setup -> Setup -> TV Settings -> Recording Profiles -> Transcoders -> High Quality

For some reason, Mythbuntu defaults to the RTjpeg codec.  When I had installed Myth manually onto a Xubuntu machine, it worked fine out of the box- but I do not remember what codec myth was set to use.  I don't know why they would package up the distro this way, since RTjpeg doesn't appear to function.  I switched the Codec to MPEG-4, changed no other settings, and it appears to be working now.  I just compressed a 7GB movie down to 1.4GB.  The way it ought to be.

Give it a shot and see if that fixes it.

---

