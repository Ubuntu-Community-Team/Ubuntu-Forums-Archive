---
title: "Audacity problems after attempting to record system audio"
date: 2016-07-03
forum: Multimedia Software
---

### Post by raymondvillain on 2016-07-03
Ubuntu 14.04, Radeon graphics and audio, installed audacity, worked fine for playing back .flac , .mp3, etc.  Then I decided to try and record audio output.  Wanted to use Audacity to slow the tempo in an attempt to learn the score of a given instrumental arrangement.  Installed pavucontrol, followed instructions on this post:

> [https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=how+to+record+system+audio+in+Ubuntu](https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=how+to+record+system+audio+in+Ubuntu)

Didn't work, now Audacity will not play back anything.  I can open an audio file with Audacity, but the sound is jibberish, and Audacity fails to close, have to use "Force Quit".  Uninstalled Audacity, installed again, same problem.
 
But Rythmbox works fine, before and after the attempt.

Any and all suggestions greatly appreciated.

---

### Post by Dennis N on 2016-07-03
Your link goes to a page of Google search results. Which result did you use?

---

### Post by raymondvillain on 2016-07-03
This one:

> Here's how to do it.
Install "pavucontrol" from ubuntu software center.
Install "audacity" from ubuntu software center.
Select "pulse*" as recording device in Audacity.
Click Record Button.
Open PulseAudio Volume Control (Search For PulseAudio Volume Control in Dash)
Select Recording Tab.


It might have been instructions for Ubuntu 12.10, not sure.

---

### Post by Dennis N on 2016-07-03
Here is a thread with information on how to record streaming audio (anything going through your sound card). My posts #4 and #7 have the key information. Be sure to examine the image attached to post #4 for correct pulse audio source settings.

[http://ubuntuforums.org/showthread.php?t=2323938](http://ubuntuforums.org/showthread.php?t=2323938)

---

### Post by raymondvillain on 2016-07-04
Many thanks, Dennis N!

Finally got it to work.  Marking this solved.

---

