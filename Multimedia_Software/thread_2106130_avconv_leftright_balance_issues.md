---
title: "avconv left/right balance issues"
date: 2013-01-18
forum: Multimedia Software
---

### Post by Pausanias on 2013-01-18
Hi folks

I've been using avconv to convert some mkv videos losslessly to mp4. The command I use is

avconv -i input.mkv -c:v copy -c:a libfaac output.mp4

When I do this, though, the mp4 file's left-right balance is messed up. Dialogue seems much more weighted towards the right channel. I've tried messing with the Dolby options to no avail.

When doing the same thing through avidemux (which takes a while longer to do the same task) the audio is fine.

So is there a 'magic' option to avconv that fixes this left-right balance issue? I need faac for iDevice compatibility.

---

### Post by Pausanias on 2013-01-18
Answered my own question. The added flag needed is -ac 2 (two audio channels). Then the dialogue is normal. Hope this helps someone.

Not sure why avconv doesn't pick this up on its own.

---

