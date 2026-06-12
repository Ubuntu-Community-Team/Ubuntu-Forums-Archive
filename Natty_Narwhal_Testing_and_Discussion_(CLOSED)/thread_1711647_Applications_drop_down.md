---
title: "Applications drop down"
date: 2011-03-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-03-21
Apologies if I've missed this in another thread, but something's broken in the applications drop-down list from the Applications launcher. See my screenshot.

I'm sure it used to work, but doesn't now. If I were to click on the "Graphics" item where the mouse cursor is in the screenshot, The Gimp opens - whose icon is underneath, as you can see. Also the "Applications" notification on the desktop to the right of the launcher stays there until another launcher is clicked.

Right-clicking on the Applications launcher and selecting one of the categories works OK.

Anyone else seeing this? I'm getting it on two machines.

---

### Post by mc4man on 2011-03-21
I'm not sure if you're referring to this bug (now fix committed 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/737203](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/737203)

---

### Post by r-senior on 2011-03-21
Yes, I noticed that. But only today. That menu doesn't seem to work at all. It's like it's "behind" the Dash and the Dash has focus.

Something else I've noticed the last couple of days is icons disappearing from the launcher when a notification appears.

---

### Post by mc4man on 2011-03-21
There is also this bug which had been bothering me for about 2 weeks, finally decided to track down the commit that caused so am now getting some action on.
(have fixed here by either using the the prior version of appmenu-gtk or building current omitting the commit
[https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/733050](https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/733050)

---

### Post by coffeecat on 2011-03-21
> **mc4man said:**
> I'm not sure if you're referring to this bug (now fix committed 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/737203](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/737203)

Thanks for that - that seems to be what I'm seeing. At least it's not just my setup. 

> **r-senior said:**
> Something else I've noticed the last couple of days is icons disappearing from the launcher when a notification appears.

Thanks. I don't think I've seen that yet but I'll watch out for it.

---

### Post by coffeecat on 2011-03-21
> **mc4man said:**
> There is also this bug which had been bothering me for about 2 weeks, finally decided to track down the commit that caused so am now getting some action on.
(have fixed here by either using the the prior version of appmenu-gtk or building current omitting the commit
[https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/733050](https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/733050)

Yes. Getting that here with appmenu-gtk 0.1.96-0ubuntu1. I must admit I hadn't noticed it.
Thanks. :)

---

### Post by mc4man on 2011-03-21
> Getting that here with appmenu-gtk 0.1.96-0ubuntu1
At this point with the somewhat limited nature of the unity panel, I'm happy to find the few areas the user can 'expand'
So that menu is quite useful here because bookmarks can be added to the 'Places' drop down. (sort of a 'quick' navigational tool

---

### Post by r-senior on 2011-03-21
> **coffeecat said:**
> Thanks. I don't think I've seen that yet but I'll watch out for it.
If you do, I've raised a bug ...

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/739865](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/739865)

---

### Post by beew on 2011-03-22
If you click "Applications" on the Unity bar the dash opens up (which takes up my full screen!) on the right upper conner there is a drop down menu to choose the category of applications. It used to work but at some point it has stopped working. Clicking it nothing happens.

I am wondering if anyone else experiences the same problem.

---

### Post by cariboo on 2011-03-22
Merged two threads on the same subject.

---

### Post by rburkartjo on 2011-03-22
still working on my end

---

### Post by beew on 2011-03-22
After today's unity update the drop down simply disappears,--as in it is not there any more!

---

