---
title: "cinelerra save's everything as a xml file!"
date: 2008-03-06
forum: Multimedia Production
---

### Post by /home on 2008-03-06
Hello,
I have a small video project.
and am touching it up with cinelerra.
Any way everytime i save a video in cinelerrat it save's it as a .xml file?? whats up

---

### Post by crush304 on 2008-03-06
cinelerra saves the project as an xml file, if you want to output the video you need to render it. File -> Render, you then need to pick the output format and then set the audio and video codecs

---

### Post by cotcot on 2008-03-07
Cinelerra records your instructions of cutting and putting video fragments together without touching the video fragments themsellves. These instructions are listed in the xml file that you save. I you want the video you have to render it (cfr previous post). This means that cinelerra executes the instructions of the xml file making a new video stream. The source video fragments remain untouched. 
Please consult carefully the [[COLOR="Red"]cinelerra  manual[/COLOR]]("http://cv.cinelerra.org/docs/cinelerra_cv_manual_en.html"). It will help you a lot.

---

### Post by /home on 2008-03-09
a big Doh Thanks,
But now there is no sound on the video.

---

### Post by keykero on 2008-03-09
What did you render the video as?

---

