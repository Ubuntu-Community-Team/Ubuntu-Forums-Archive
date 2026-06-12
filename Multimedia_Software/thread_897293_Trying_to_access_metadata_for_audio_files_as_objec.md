---
title: "Trying to access metadata for audio files as objects"
date: 2008-08-22
forum: Multimedia Software
---

### Post by FamousAmos on 2008-08-22
For .mp3 files(not only .mp3, but let's focus on .mp3 for now).  Specifically, I want to write a script or program(whichever) that can recurse through my filesystem for all .mp3 files.  When it finds and mp3 file, I want it to read the metadata that's there (if any) and create a directory for that artist/album (unless it already exists) under a specific already existing directory.  Most of that is not a big issue, but I'm having some trouble figuring out how to programatically access the tagged metadata for .mp3 files.  Can anyone help me with this?  


Thanks in advance.

---

### Post by FamousAmos on 2008-08-22
Does anyone have any ideas?

---

### Post by scottch.eezem on 2008-08-27
I'm actually trying to figure out the same thing.  I've had some luck with kfile.

---

### Post by FamousAmos on 2008-08-28
Hey, thanks for the reply.  I tried using kfile at your recommendation, but it tells me that it cannot determine the metadata(sample output below):


```

#:/media/hda1/Music$ kfile --av The Outsider.mp3
kbuildsycoca running...
DCOP Cleaning up dead connections.
The: Unknown (application/octet-stream)
Outsider.mp3: MPEG Layer 3 Audio (audio/x-mp3)
The: Cannot determine metadata
The: Unknown (application/octet-stream)
Outsider.mp3: MPEG Layer 3 Audio (audio/x-mp3)
Outsider.mp3: Cannot determine metadata
#:/media/hda1/Music$ kfile --la The Outsider.mp3
The: Unknown (application/octet-stream)
Outsider.mp3: MPEG Layer 3 Audio (audio/x-mp3)
The: Cannot determine metadata
The: Unknown (application/octet-stream)
Outsider.mp3: MPEG Layer 3 Audio (audio/x-mp3)
Outsider.mp3: Cannot determine metadata
#:/media/hda1/Music$ kfile --dialog The Outsider.mp3
#:/media/hda1/Music$ 


```

The --dialog just opened up a popup box that told me it had 2 Items - 2 Files - No Folders and the location, and that was all it had.

How did you use it that allowed you to determine the metadata?  Does anybody else have anything to add? 

Thanks in advance.

---

### Post by FamousAmos on 2008-09-01
Figured I'd ask one more time, just to see if anyone has any ideas to help me.  If not, I can keep looking myself.

---

