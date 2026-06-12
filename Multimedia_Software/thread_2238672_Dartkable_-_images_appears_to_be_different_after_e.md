---
title: "Dartkable - images appears to be different after export"
date: 2014-08-09
forum: Multimedia Software
---

### Post by timotej-sulka on 2014-08-09
Hi guys, 
I am running on 14.04 and I am using Darktable as I used to work in Adobe Lightroom in Windows and Darktable seems to be perfect solution in Ubuntu. However, I have some issues with image displaying. I edit photo in Darktable, but after export it's little bit different - I would say more bright and more saturated. It is annoying that picture I consider good appears to be different after I open it in Image viewer or after upload on FB or whatever... 
I am using GPicView as default viewer. In native Ubuntu Image viewer photos seems the same as in Darktable, but in every other I've tried (in Windows also) it is different. Is there a way how to set Darktable to display photos in same way as most of image wievers? ? 


Here is the screenshot so you can actually see the difference.

[IMG]http://i62.tinypic.com/2nr26p5.png[/IMG]

(photo by my friend I cooperated with, by the way she says hello to you :D ) 

I hope there is someone who can help and sorry for my english ;) 
Thanks

---

### Post by fabian-opencode on 2014-09-28
Hi,

I have exactly the same issue here. Same setup as yours. Did you find any solution yet?
I noticed the issue very strongly when working on pictures with people in it. The colour of the skin - I guess it is the saturation - changes quite a bit and it looks quite bad.

---

### Post by fabian-opencode on 2015-04-01
Actually I solved the problem by now. For me it was a wrong display color profile. You can remove the current color profile like this: ```
xprop -root -remove _ICC_PROFILE
``` After that the colors are the same and the problem was in the viewer ubuntu uses. So the colors you see in Darktable are actually correct. Maybe someone finds this helpful.

---

