---
title: "Audio file conversion"
date: 2012-04-26
forum: Multimedia Software
---

### Post by bill-lancaster on 2012-04-26
This seems to be a simple task but....
I download radio programmes using get_iplayer.  Sometimes they are .flv or .wma
How can I convert them to mp3 using terminal & ffmpeg?

This:-

ffmpeg -i /home/bill/Music/source.flv -ar 22050 -ab 32 audio2.mp3

produces error "Encoder (codec id 86017) not found for output stream #0.0"

Any help would be appreciated

---

### Post by bill-lancaster on 2012-04-26
found solution elswhere in this forum.
installed ubuntu-restricted-extras in Synaptic - problem solved

---

