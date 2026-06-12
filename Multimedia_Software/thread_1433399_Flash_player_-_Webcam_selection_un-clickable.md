---
title: "Flash player - Webcam selection un-clickable"
date: 2010-03-19
forum: Multimedia Software
---

### Post by Rootbrian on 2010-03-19
Okay, so i'm having this issue (and haven't posted here in a long long time) with flash player on 8.04.3 (full USB install), 9.10 (netbook, desktop) and this pertains to the Netbook as I share the USB install with that and my desktop with no issues.

So as is the case, flash player will NOT allow me to select a webcam. It's unclickable, resembling a screenshot or picture on a website, that you cannot click the buttons or anything inside it.

I cannot use my webcams at all on tinychat, blogtv or facebook to record videos. It doesn't even work on twitvid either.

The selection is unclickable. Is there a way to FORCE it to be clickable? I know in windows that it's clickable, but why not Linux?

Help is needed.

PS. If this is in the wrong section, feel free to move it to the proper location. My bad.

---

### Post by no2498 on 2010-03-19
go to the adobe web site
look for the settings manager 2nd folder from the left allow and remember
now you need to set the sites you use it on

[http://www.adobe.com/](http://www.adobe.com/)

---

### Post by Rootbrian on 2010-03-19
> **no2498 said:**
> go to the adobe web site
look for the settings manager 2nd folder from the left allow and remember
now you need to set the sites you use it on

[http://www.adobe.com/](http://www.adobe.com/)

I have already tried that. Regardless, the settings (after the website(s) have been allowed to access camera and microphone) behaves like a still image, making it impossible to select from the built-in or USB webcam.

---

### Post by no2498 on 2010-03-19
how did you set the cam up
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

try the cam in cheese

---

### Post by Rootbrian on 2010-03-19
The cam works fine in cheese. Both cameras do, in fact, all of them work.

Adobe Flash is just not allowing me to use either one via live broadcasts. Wish there was a way to temporarily disable the built-in camera so only the Logitech shows up, therefore, elimiating the "Choose Camera" box, which is useless when you can't click anything in it.

---

### Post by asbesto on 2010-05-01
I have the same damn problem here, eeebuntu on eeepc 701. The camera is perfectly working, but the Flash Plugin requester that ask "allow access to camera" is unclickable. This is very annoying!!!

---

### Post by lleachii on 2010-06-09
Please visit [https://bugs.adobe.com/jira/browse/FP-775]("https://bugs.adobe.com/jira/browse/FP-775") to track the bug report and vote for this issue.

---

