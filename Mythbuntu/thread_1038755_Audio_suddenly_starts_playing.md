---
title: "Audio suddenly starts playing"
date: 2009-01-13
forum: Mythbuntu
---

### Post by Meph1st0 on 2009-01-13
I've got a weird issue that started about a month ago after updating my install.  When I'm just moving around in the menus, sometimes music from mythmusic will just start playing all of a sudden, even if the queue was empty.  Or sometimes, I'll be (again) moving around in the menus and I'll suddenly hear audio from live TV.  When this happens, I can even go into my recordings and play a show and I'll hear the audio from both Live TV and from the recorded show that I'm watching.  The only way to get it to stop is to exit myth-frontend and then go back in.

Is this happening to anyone else?

---

### Post by cb34 on 2009-01-13
do you have any remote desktop connections to a friend or something, or in the past.. maybe someone is flicking with your head?

---

### Post by Meph1st0 on 2009-01-13
I've wondered that myself, I guess I could turn off that service on the box.  I don't use it very often anyway.  I wouldn't expect to get liveTV audio though while I'm just browsing the menus, even if I had a friend VNC'd in.  Unless he were smart enough to enable it through SSH at the console, but I don't have any friends who are savvy enough with Linux to do that.  I guess it is also possible that it'd be a hacker.  But, I would be inclined to doubt it.  Especially if the audio stops as soon as I exit myth-frontend.

---

### Post by egandy on 2009-01-14
We had a similar problem about a month ago after an update.  For some reason when it rebooted after the update it started two instances of the front end and we were getting audio from both. I think it only happened once.

---

### Post by jMon54 on 2009-01-15
I, too, have had this sort of thing happen recently.  In my case, I would be watching one recorded program while the audio from another program was playing!  I had to ESC all the way out to main menu to make it stop and then proceed normally.

---

### Post by Meph1st0 on 2009-01-17
I'm glad to see that I'm not the only one who's experienced this.  Although, I haven't found a solution to the problem yet.  However, it hasn't happened to me in the last week or so.

---

### Post by luigidk on 2009-12-26
Has this been resolved?  I am having the same issues and the best I can tell is there is a second frontend running.  

I've gone to my desktop>terminal and killed the front end and backend - music is STILL playing...  Doing a PS - I see there is a front end running under MY user name - not as Mythtv.

Thoughts? Help?

---

### Post by nickrout on 2009-12-26
mythfrontend should NOT run under user mythtv, in mythbuntu it is set up to run under the user you set up when you installed (probably your username). If it is running under user mythtv, thats your problem.

---

### Post by luigidk on 2009-12-27
Checked again- and it is running under my userid - not Mythtv.

So weird though -  I kill front/backends - music keeps playing...

and it still looks like there is a frontend running - but I can't seem to kill it...

---

