---
title: "Recording Audio Question"
date: 2009-01-17
forum: Multimedia Software
---

### Post by drhiii on 2009-01-17
I've mucked around trying to record streaming audio from various sites using many methods, too numerous to mention...

My core question is... is there a way to just capture the audio device, is it known as an audio "socket", or a way to record audio that is being sent to the audio card that ends up on headsets or external speakers?  That way one would only need to look at capturing audio that goes to a device, instead of worrying about what flavor of stream is coming from what source, etc etc etc.

The direct problem is trying to capture an interview my father did for a local NPR radio station and I cannot for the life of me figure out how to capture this particular stream.

Here is the particular stream...   [http://krccnews.org/rccnews/citizen-report-media-convergence/2009/01/15/4813](http://krccnews.org/rccnews/citizen-report-media-convergence/2009/01/15/4813)

Help anyone?

---

### Post by drhiii on 2009-01-17
Solved.

Audacity plus mucking around with the sound card settings via the AlsaMixer.  Figured it out.  How cool is this??  Pretty cool.  

Now am trying to figure out how to mark this thread as SOLVED.

---

### Post by Tomatz on 2009-01-17
Top rh, "thread tools" then "mark as solved". If you could explain exactly what you did it should help others better. ;)

---

### Post by drhiii on 2009-01-17
You bet.  This is a thread that helped break the ice.  It is a cross between Preferences in Audacity, and figuring out the right input/output in AlsaMixer or in the case of below, running two apps in the shell window.  It is just about impossible to detail it because what works for me as I have read may not, likely won;t be the same for someone else.  It just takes some banging on Audacity to select the right input, and Alsamixer to get the right input/outputs selected.  Honestly, it was clicking until I got it.  


[http://www.linuxquestions.org/questions/linux-hardware-18/microphone-audacity-skype-recording-663187/](http://www.linuxquestions.org/questions/linux-hardware-18/microphone-audacity-skype-recording-663187/)

---

