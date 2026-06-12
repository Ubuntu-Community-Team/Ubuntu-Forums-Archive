---
title: "Database error and backend setup problem"
date: 2010-03-29
forum: Mythbuntu
---

### Post by phroman on 2010-03-29
Hello people, I could use some help with Database errors and channel listings, I'm so very confusededd...

I'm seeing this error in my mythbackendlog:  

```
Scheduler, Warning: Listings source '' is defined, but is not attached to a card input
```

I think this is related to my problem of not being able to watch live tv if I enter a channel change script in the mythsetup.  In mythsetup, I understand that you attach a video source to your selected tuner.  ie  my schedules direct account for direct tv listings, to my s-video port of my capture card.  But the Input connections setting page is really unclear, at least to me. How do I attach it?

I'm running mythtv in a small window, so I can see my desktop and the mythtv terminal window.  

In myth backend setup, Input Connections>

My capture card and input are listed correctly.
My Video Source is listed correctly.  
In the Preset Tuner field, I would think that would be for maybe an ota tuner, but I'm not sure. 
The big issue is the 2 fields:
Scan for channels - and Fetch channels from listings source.  When I highlight and press the 'Fetch channels from listings source' option, I can see things going on in the terminal window, but looks like it gets an error.  I couldn't figure out how to copy the text so I only have the last 2 lines:

2010-03-28 23:11:41.763 DataDirect: Deleting temprary files
ICE default IO error handler doing an exit(), pid = 3101, errno = 32

Is this why it's not attaching?  And as for the Starting channel field, do I need that if I'm using schedules direct?  Everything on this page is sorta cryptic.. Nothing gives me any indication or confirmation that I've attached my source to my input, Really not sure what I'm supposed to do here.  :confused:  

I hope I can get this figured out. Thanks for you patience and help!

---

### Post by phroman on 2010-03-29
UPDATE:

This is not related to not being able to watch live tv.  I fixed that today, that was a mis configured serial port.  My program guide seems ok so I'm not really sure what to say about this but if anyone has any info on it I'd love to hear.  Thanks everyone.

---

