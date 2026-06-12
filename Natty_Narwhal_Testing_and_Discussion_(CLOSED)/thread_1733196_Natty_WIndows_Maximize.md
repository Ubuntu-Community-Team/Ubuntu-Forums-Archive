---
title: "Natty WIndows Maximize"
date: 2011-04-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rabideau on 2011-04-19
I have been trying to figure out how to stop my windows for FF4, evolution and Ubuntu Tweak from maximizing on every open.  I am using Natty beta 2 and this function seems to happen on both of my PCs.  Any ideas how I might adjust things so all windows open in a non-maximized state????

Thanks.

---

### Post by rlzaleski on 2011-04-19
Ran in to this as well, it's annoying the crap out of me at the moment.

---

### Post by mc4man on 2011-04-19
You need to open the app,  resize the window so it is below 75% of the screen size, then close the app.
By default any window over 75% will be maxed when opening.
This is likely not configurable, can be changed in the source.
(src/PluginAdapter.cpp line 26 or so.
There was a reason for this, whether still valid don't know

(I use 85% here w/ no issues

---

### Post by rabideau on 2011-04-20
Where would I find the file PluginAdapter.cpp precisely?  I'd like to attempt using other variables; the 75% limitation makes netbook screens a real problem.

---

### Post by mc4man on 2011-04-20
> **rabideau said:**
> Where would I find the file PluginAdapter.cpp precisely?  I'd like to attempt using other variables; the 75% limitation makes netbook screens a real problem.

Well you'd need to get, edit and build the unity source.
(while i never looked to hard, I'm not aware of any way to configure this 
It's quite a quick and easy build if inclined to do so.

Otherwise the value was basically picked as a compromise between the orig. (60%), and what I was using. It doesn't particularly have to stay that way.
If you feel the 75% is to small for netbooks then maybe re-open this bug and make a case.
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/708809](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/708809)
( I re-commented but didn't re-open - don't have a netbook and the 75% is ok on a 13" laptop here (though I do prefer 85%

---

