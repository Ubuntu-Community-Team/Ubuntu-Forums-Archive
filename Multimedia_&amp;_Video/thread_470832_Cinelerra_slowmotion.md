---
title: "Cinelerra slowmotion"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by hojgaard on 2007-06-11
Hello!
Is there any body out there who knows a lot about cinelerra
I have searched google, because i want to make a slowmotion in a little part of my video, but i cant find anything about it. Is there anyone out there knowing how to make a slowmotion i cinelerra???

---

### Post by cristovaum on 2008-03-28
Hi, i don't know a lot about cinelerra but, for slow motion effect, use a ReframeRT effect in stretch mode with a value less than 1.
Example: you have a clip that you want to put in slow motion. The clip starts at 33.792 seconds and ends at 39.765. The clip is 5.973 seconds long. You want to play it at 4/10ths normal speed.
You divide the clip length by the playback speed (5.973/.4) to get a final clip length of 14.9325 seconds. You create an in point at the start of your clip: 33.792 seconds. You put an out point 14.9325 seconds later, at 48.7245 seconds (33.792 + 14.9325).

You attach a ReframeRT effect, set it to .4 and stretch. You change the out point at 48.7245 to an in point. You start your next clip after the slow motion effect at the 48.7245 out point.

Hope this will help you.:)

---

