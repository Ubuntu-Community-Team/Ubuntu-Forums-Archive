---
title: "GPU Lockup Error"
date: 2013-03-11
forum: Multimedia Software
---

### Post by volkskris on 2013-03-11
I've got a irritating problem on my laptop. It freezes for a couple of seconds, and gives me error messages indicating I've experienced a problem. My laptop was first installed with ubuntu 11.10, and upgraded to 12.04 and now 12.10. I've only been experiencing this problem for a week or two.

Here's a link to my computer specs: [http://www.cnet.com/laptops/acer-aspire-5750-2434g50mnkk/4507-3121_7-35279962.html](http://www.cnet.com/laptops/acer-aspire-5750-2434g50mnkk/4507-3121_7-35279962.html)

And here's an album with screenshots of the error messages: [http://s982.beta.photobucket.com/user/volkskris/library/Gpu%20Error](http://s982.beta.photobucket.com/user/volkskris/library/Gpu%20Error)

Kristof

---

### Post by Bucky Ball on 2013-03-11
*Thread moved to** Multimedia & Video***

Welcome to the forums. 

Just curious; has this just started to happen in 12.10 and didn't happen in 12.04 LTS? If that is the case, was there a specific reason you upgraded to 12.10? 12.04 LTS is the current, stable long-term support release, supported until April 2017.

My rule of thumb is generally 'if it's not broke, don't fix it,' unless there is a very specific reason. Therefore I use the LTS releases for my day to day, stable, production install and install anything else I want to play with on another partition(s). That way I always have something rock solid and my playthings!

Good luck. ;)

---

### Post by volkskris on 2013-03-12
It happened only on 12.10. And I just updated to have the newest version, 12.04 was running beautiful. After the upgrade 12.10 also ran beautiful, it was only after I tried to connect an external screen that the errors came. The screen worked perfectly tho. 

Kristof

---

### Post by rpaco on 2013-03-29
12.04 Precise 3.5.0-26 generic 64 bit with Gnome classic on Zoostorm Style Note 8GB mem 500GB hd 

Also now happening on 12.04 LTS 
Also started about 6 days ago after a routine update. (No I don't remember what was updated)
Intel B980 Sandybridge GPU lockup.

There are several reports of this on launchpad all claiming to be solved but they are mostly dated over a year ago. This is a new problem. My apport report says not to submit to launchpad because Precise is not longer in development. But I think it is more to do with a recent update, I would guess to the video drivers. I have tried both going back to a previous version kernel and re-installing the xorg intel drivers but to no difference. Cunningly the error report cannot be copied and pasted (who though of that?)  or I would paste it here. 

If this has been solved please point me, this is the only thread relevant on my search result in here.

---

### Post by Bucky Ball on 2013-03-29
> **rpaco said:**
> 12.04 Precise 3.5.0-26 generic 64 bit with Gnome classic on Zoostorm Style Note 8GB mem 500GB hd 

Also now happening on 12.04 LTS 
Also started about 6 days ago after a routine update. (No I don't remember what was updated)
Intel B980 Sandybridge GPU lockup.

There are several reports of this on launchpad all claiming to be solved but they are mostly dated over a year ago. This is a new problem. My apport report says not to submit to launchpad because Precise is not longer in development. But I think it is more to do with a recent update, I would guess to the video drivers. I have tried both going back to a previous version kernel and re-installing the xorg intel drivers but to no difference. Cunningly the error report cannot be copied and pasted (who though of that?)  or I would paste it here. 

If this has been solved please point me, this is the only thread relevant on my search result in here.

Please post a new thread regarding your issue rather than jumping on this one. Thanks. ;)

---

### Post by rpaco on 2013-03-29
OK, but Isn't this the same issue?

---

