---
title: "Amarok &amp; MythTV integration (HOWTO &amp; questions)"
date: 2007-09-07
forum: Multimedia &amp; Video
---

### Post by magnulu on 2007-09-07
From one noob to others:

Musings from the Void has a great HOWTO on how to integrate Amarok and MythTV, with lirc mouse simulation and all good things. Head over and leave a thanks on the comments: 

[http://acidzebra.blogspot.com/2007/07/integrating-mythtv-and-amarok_17.html](http://acidzebra.blogspot.com/2007/07/integrating-mythtv-and-amarok_17.html)

As I have a headless box connected to my old TV, I had the problem of seeing the fonts in Amarok on high resolution. This was fixed by playing with xorg's DPI settings, adding this line under the Monitor section in /etc/xorg.conf:

Option "DPI" "123 x 123"

Experiment with the values to find the best result for you.

Question 1: Every time I start amarok through mythtv, the window "climbs" some pixels up. I quitted amarok in maximized mode, so now, after starting it again a couple of times, the menu lines are above the top of the screen. Why does this happen, and how can it be fixed? As i administer my ubuntu box through ssh, it would be great to get a CLI only solution to this.

Question 2: The HOWTO mentions "configuring KDE to run Amarok borderless and maximized+on top." How can one do that, again through CLI?

[edit] I figured it out with a nice little tool called devilspie, installed through aptitude. My .devilspie/amarok.ds looks like this:

(if (is (application_name) "Amarok") (begin (geometry "+10+10") (undecorate) maximize))

Works like a charm. 


Enjoy :-)

---

