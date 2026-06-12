---
title: "remove piano sound"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by ronnybob on 2008-02-28
I am using Ubuntu Gutsy 7.10. I have a recording of people talking and in the background there is a piano playing, but the piano is to loud, I would like to remove the piano sound and keep the sound of the people talking. Does anyone know of a program in Linux that will do that?

---

### Post by ph1 on 2008-02-28
I'm no sound expert, but you can try playing with Audacity, which is a fairly full-featured sound editor available free from Sourceforge.net.

---

### Post by tgalati4 on 2008-02-28
I assume this is a mono recording.  If you had a stereo recording, you can use some phase inversion to reduce the piano.

If you only have a mono recording, then this would be difficult because the piano covers the same frequency range as the human voice.  If you have only male voices, then you can filter out higher frequencies using the Equilization tool in audacity.  If you only have female voices, you can filter out lower registers.  

If it's a particular note that's coming through, you can use a notch filter to remove that note without affecting vocal intelligibility too much.  You can use multiple notches to remove several notes, but the more notches used, the less vocal quality preserved.

I presume that certain notes were amplified because of the distance between the microphone and the piano.  If you know this distance, you can use a feedback calculator to estimate which notes would be amplified and apply notch filters to reduce those notes.

---

