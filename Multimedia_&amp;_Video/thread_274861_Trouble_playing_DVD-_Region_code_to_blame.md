---
title: "Trouble playing DVD- Region code to blame?"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by spiffytech on 2006-10-10
I recently got a DVD, and I want to play it in my Dell laptop. I put it in, and the only thing it'll do is play a single track from the music portion. I suspect that the DVD drive on my laptop is doing some region code checking. How would I configure Ubuntu to identify my DVD drive with the Region 1 (US) region code?

---

### Post by meng on 2006-10-10
Have you enabled encrypted DVD playback?
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
section 9

---

### Post by spiffytech on 2006-10-10
Following that, I am now able to bring up the DVD in VLC and play it, but no sound comes out.

---

### Post by NeoLithium on 2006-10-10
Check alsasoundmixer and see that everything needed to play DVD's is unmuted. Once in a while it can spontaneously change to mute something, or you never really know if something obscure may be needed to allow playback of the audio.

Just mentioning this simple way because it's happened to me by accident :)

---

