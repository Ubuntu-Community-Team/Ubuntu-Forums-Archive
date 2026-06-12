---
title: "Shockwave Flash &amp; Movie Player error fix"
date: 2010-12-27
forum: Multimedia Software
---

### Post by beesblaas on 2010-12-27
I am describing my fix for playing a Shockwave Flash file in Mozilla,
in case someone else has this problem.

I was clicking on an Adobe Flash utility on a web-page with Mozilla browser (a .swf file) and what happened then is
it would open Movie Player, but this would fail with the following error:
"An error occurred
GStreamer encountered a general supporting library error."

To fix the problem, go to Mozilla > Edit > Preferences > Applications 
then scroll down till you see "Shockwave Flash file" entries in the list.
Next to these entries, the Action should be changed to "Use Shockwave Flash (in Firefox),
it should not be "Always ask" or "Use Movie Player (default)".

It could be that there is another way to fix Movie Player, but above fix is very easy.

PS: As a matter of interest, you can test if your installation of Adobe flash in Mozilla is working by going here:
[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)
[]("http://www.adobe.com/software/flash/about/")There is a link to click which will show an "f" icon animation if successfull.

---

