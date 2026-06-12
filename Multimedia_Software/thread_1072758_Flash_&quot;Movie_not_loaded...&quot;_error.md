---
title: "Flash &quot;Movie not loaded...&quot; error"
date: 2009-02-17
forum: Multimedia Software
---

### Post by eastlight on 2009-02-17
Hi, 

I've looked quite thoroughly into this but can't seem to find a solution that works. I'm using Intrepid with Firefox 3.06 and can't get any flash videos working (youtube for example). Whenever I visit a page with a video on, I get a black box and no video.  Right clicking on the black box gives a greyed out "Movie not loaded..." error and "About Adobe Flash Player x".  

I've tried flash 9 and flash 10 both manually installed and automatically installed; neither makes a difference. The animation on the front page of [http://www.shockwave.com](http://www.shockwave.com) works though and [http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/) tells me the correct version I have installed.  

This started recently and I didn't manually change flash.  Was there an update which broke this? 

I ought to mention that I can't get the videos working in other browsers either (Opera/ Konqueror) but I use firefox mainly. 

Many thanks for any suggestions, 

James

---

### Post by docp0t on 2009-02-17
](*,)I've been battling with the same problem for a while now.
I'm using Firefox 3.0.6 on Hardy Heron.

---

### Post by alexwiik on 2009-02-18
I found a solution to the problem here: [https://bugs.launchpad.net/ubuntu/+source/flashblock/+bug/310210](https://bugs.launchpad.net/ubuntu/+source/flashblock/+bug/310210)

It seems like it was flashblock that was causing the problem.
Just follow this link: [https://addons.mozilla.org/de/firefox/addon/433](https://addons.mozilla.org/de/firefox/addon/433)
It's in german, but just press the big green button to install the new version of flashblock.

hopefully, problem solved!

Alex Wiik.

---

### Post by eastlight on 2009-02-18
Thanks Alex, 

That was the solution. I had flashblock version 1.3.10a installed.  Disabling that in Firefox led to the videos playing correctly.  I then updated flashblock to version 1.5.8 from [http://flashblock.mozdev.org/installation1.html](http://flashblock.mozdev.org/installation1.html) and re-enabled it and now it all works together. 

All the best, 

James

---

