---
title: "How do I make desktop Video with Audio?"
date: 2008-10-19
forum: Multimedia Software
---

### Post by redonwhite on 2008-10-19
What i want to do is make a video of my desktop in motion with an MP3 playing during the video.  A youtube video =).   Ive tried recorddesktop but it wont pick up audio.  Thanks for your help!

---

### Post by redonwhite on 2008-10-20
Bump...

---

### Post by redonwhite on 2008-10-21
bizump

---

### Post by mocha on 2008-10-22
You have to play with your recording mixer settings and specify the audio device in recordmydesktop's settings.  For my HDA intel controller I have to tell recordmydesktop to use "hw(0,0)" as the capture input.  Then I need to play with the alsa mixer capture settings to choose the internal audio mix and set the levels.

---

### Post by redonwhite on 2008-10-23
Yikes! hehe.  Okay i will do some research with your information.  Thanks for the help.

---

