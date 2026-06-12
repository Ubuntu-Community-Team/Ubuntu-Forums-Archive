---
title: "GTK-recordmydesktop will not record games."
date: 2012-04-15
forum: Multimedia Software
---

### Post by Herpythebrony on 2012-04-15
Hi, I have been using Lubuntu for like a week and so far so good but I want to record myself playing assult cube (very fun fps btw) but on the play back I get a black screen. Why is this happening?

---

### Post by Herpythebrony on 2012-04-15
bump

---

### Post by sffvba[e0rt on 2012-04-15
Please don't bump more than once every 24 hours.

As for your problem - [Source]("http://recordmydesktop.sourceforge.net/faq.php#Some_windows_are_not_recorded!")

> Some windows are not recorded!

recordMyDesktop is based on extensive usage of the Xdamage extension. Instead of capturing
whole screenshots, the program marks the areas that have changed and updates them.
This approach fails on two occasions. Video played throught the Xv extension and hardware 
accelerated glx context. This generally means 3d games and video windows.
To record video you can configure your player to not use the Xv extension but rather go with X11/Xshm.
This is a simple task on most video players and you should consult their documentation on how to do this.

Recording 3d windows on the other hand, is not easy. You have to enable the full-shots option(*and with 
it you also definately have to enable usage of the MIT-Shm extension). This means though that now you are 
requesting a full image at every frame, so you will need a lot more proccessing power. In this case you 
should probably confine the recording only on the 3d window itself.


404

---

