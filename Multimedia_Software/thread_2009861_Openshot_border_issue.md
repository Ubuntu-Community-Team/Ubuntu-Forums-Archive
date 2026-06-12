---
title: "Openshot border issue"
date: 2012-06-25
forum: Multimedia Software
---

### Post by itachi12596 on 2012-06-25
I've been using Openshot to combine a recorded desktop session with some recorded audio, and it works like a dream except for the massive black border around the edge of the video. I thought it was just in the preview, but VLC has that same border. I've checked everywhere and no one seems to have an answer. Is there some blatantly obvious solution I'm missing?

---

### Post by sudodus on 2012-06-25
Which version of Openshot are you running?

I'm running 1.3.0 in Ubuntu Studio 11.04 (which is quite old now), and I don't have that problem. Are you converting from one screen resolution to another?

---

### Post by itachi12596 on 2012-06-25
I'm using which ever version comes from the software center in 12.04
As for the resolutions, I'm not 100% sure. The way the software I have records is weird.

---

### Post by sudodus on 2012-06-25
How did you record the desktop session (what program)? Is the black border there even before entering the clip into Openshot? Can you check the frame size (width x height) in pixels of the input file and the output file?

---

### Post by itachi12596 on 2012-06-25
I'm using Kazam Screencaster and no, it doesn't have the border before I put it in Openshot. And I do hope you'll forgive me, but I'm extremely new to video editing

---

### Post by Pinoy Tux on 2012-06-27
Open the clip properties.  On the Video tab:

[LIST]
[*]Enable Stretch Full Screen
[*]Disable Maintain Aspect Ratio
[/LIST]
This should get rid of the black border surrounding the video clip, at the expense of a non-proportionate aspect ratio.

---

### Post by itachi12596 on 2012-07-02
Thanks mate. I'll try that

---

