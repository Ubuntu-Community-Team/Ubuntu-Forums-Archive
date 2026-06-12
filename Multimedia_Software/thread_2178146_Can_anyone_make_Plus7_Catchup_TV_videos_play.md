---
title: "Can anyone make Plus7 Catchup TV videos play?"
date: 2013-10-02
forum: Multimedia Software
---

### Post by dalekky on 2013-10-02
[http://au.tv.yahoo.com/plus7/](http://au.tv.yahoo.com/plus7/)
I can't get any of these videos to play.
All I get is a black rectangle with the play/pause controls at the bottom.
Tried Chromium & Firefox.
Other sites like youtube/dailymotion/ABC iView etc all work.

---

### Post by Yellow Pasque on 2013-10-02
They work fine for me (using FF with latest Flash 11.2.x plugin), though I had to use the regular plus7 site since my IP address doesn't have an Australian accent...

---

### Post by dalekky on 2013-10-07
Maybe it is just the Australian Plus7 server? Can any other Australian users confirm this?
I can't access any Plus7 site except the au.tv.yahoo site - any attempt to change country of site just redirects back to au site.

---

### Post by Bucky Ball on 2013-10-07
Go here:

[http://au.tv.yahoo.com/plus7/faq/-/6628748/](http://au.tv.yahoo.com/plus7/faq/-/6628748/) 

... and look for this heading 

> I am using Linux and have issues with playback:

Worked on my wife's computer. And yes, I am in the land of sun, sand, sheep, storms and other things that start with 's'. ;)

Now if I could only get it working on the Raspberry Pi again I'd be a happy man. That doesn't play nice. Used to be fine but is about the DRM I think. They changed it up a few months ago (or longer?). I have emailed them about it but got no reply.

---

### Post by milliganimals on 2013-11-22
I've had some luck getting Plus7 to work (in Aus).
Following the directions on the 7plus site, I installed HAL - but also _halevt_

$ sudo apt-get install hal halevt

I needed to initiate halevt through terminal 

$ halevt

After this 7 Plus plays in Firefox and Chromium, but not Chrome.

My next task is to find out how to tab-cast from Chromium to Chromecast with sound :-(

I know this is late but hopefully some help.

---

