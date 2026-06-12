---
title: "Play MP3 in amarok - libxine-extracodecs ?"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by ryodoan on 2007-11-30
I see there are many old posts on this subject, but very few new ones that relate to Gutsy Gibbon and I think something has changed with relation to this problem since Dapper.

In any case when I try to play an MP3 in amarok I get the message: "no suitable demux plugin found"

From googling and searching the forums it seems installing libxine-extracodecs fixed their problem, however typing, "sudo apt-get install libxine-extracodecs" results in a message stating that the package was not found but that a reference to the package was found.

Is there some other solution in Gutsy that I am not aware of, or is there some way I can install libxine-extracodecs ?

Thanks for your time

---

### Post by koleoptero on 2007-11-30
Use sunaptic. Search for libxine codecs, and libxine ffmpeg. Those are the ones you need.

---

### Post by ryodoan on 2007-11-30
Thanks, I was missing ffmpeg.

---

