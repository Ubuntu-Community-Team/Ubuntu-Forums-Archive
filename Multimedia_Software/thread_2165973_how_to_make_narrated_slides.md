---
title: "how to make narrated slides"
date: 2013-08-07
forum: Multimedia Software
---

### Post by ZICODIAN on 2013-08-07
Hi *

I am trying to come up with some simple, easy instructions for creating narrated slides. The instructions must be simple and very quick. The ideal sort of procedure I have in mind is as follows:

The slides are created (in Impress, Beamer or something similar) and then narration is recorded while running through the presentation. The single sound recording of the narration and the slides are bound together in some way together with timing information collected when running through the presentation.

Right now, there are two approaches I can see:

The first approach involves creating the slides and then using ffmpeg to record a video of the slides being presented on screen together with a voice recording. Now, ffmpeg would be difficult to use, but, further, many for whom these instructions are destined have multidisplay setups which would require specifying screen coordinates and whatnot to ffmpeg. This is far too complicated. Overall, this approach seems both too complicated and laborious.

The second approach involves creating the slides and then recording sound clips for each slide. These sound clips would be added to the slides in Impress. This approach also seems far too laborious.

Could you suggest some alternative approach that is quick and easy and some way similar to that ideal scenario I described (i.e., making slides, narrating the slides all the way through and then not having some complicated assembly procedure to complete the presentation)?

I thank you very much for any suggestions.

---

### Post by TheFu on 2013-08-07
Create a "screencast" using something like **Kazam**.
Turn down the FPS to 5 fps. Compression should be fantastic.

---

### Post by sudodus on 2013-08-07
You need to know the time (offset from the start of the audio file) when each slide should be shown.

Then you can use ***Openshot*** to make a movie. Use one track for the audio file, and put the slides (picture files) onto another track (use two of them if you want overlap). Edit the picture entries to be the desired length (to fit the narrating). It will still be a lot of manual work, but it is maybe easier than the other two alternatives.

---

### Post by royalist10 on 2013-08-13
Maybe this will help by expand the thread as I want to do something similar. I have complete 'Impress' presentations to used by projection, but would like to have DVDs to hand out after the show, for the audience to study at home. Using Devede and Brasero to burn.

---

