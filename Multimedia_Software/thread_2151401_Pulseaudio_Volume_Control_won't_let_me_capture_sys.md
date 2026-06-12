---
title: "Pulseaudio Volume Control won't let me capture system audio."
date: 2013-06-04
forum: Multimedia Software
---

### Post by Hari5g900 on 2013-06-04
Hello there everyone,
     I do linux screencasting and Pulseaudio plays a huge part in my videos. It worked fine on installation till now. Now I'm finding problems with setting it to the "moniter of" option when recording. It seems like it is not getting the input but I can hear the system audio on my headphone. The only problem is that there is no system audio in my videos. I tried changing the screencaster (I used FFmpeg but I've also tried recordmydesktop and kazam.) but nothing seems to work. Can I get help?

---

### Post by Baldrick_NZ on 2013-06-05
Try 'pavucontrol' from the repos (sudo apt-get install pavucontrol, in terminal). It has an option to record audio monitor, as it plays from your soundcard, under the recording tag when there is a recording app running.

I worked for me.

Cheers.

---

### Post by Hari5g900 on 2013-06-05
pavucontrol is Pulseaudio volume control. ](*,)

---

### Post by Hari5g900 on 2013-08-03
Okay guys, I didn't know what happened but now some miracle has happened and pulseaudio is working fine.:D(I think it might be because I updated Ubuntu lately)

---

