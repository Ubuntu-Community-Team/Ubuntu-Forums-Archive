---
title: "webcam zooming problem. PLEASE HELP ME"
date: 2010-04-13
forum: Multimedia Software
---

### Post by e1ektrob0y on 2010-04-13
Hi guys. I've had no end of problems with my logitech webcam and flash apps like userplane. 

Long story short I'm using 8.04 and my logitech webcam was working perfectly with userplane chat. It didn't work at all with 9.04, 9.10 and 10.04. 8.04 it works...GO FIGURE!

Anyway, everything was going along fine until I installed the webcam package called cheese. Suddenly my cam became super zoomed in the userplane chat room. This problem I have experienced so many times before but I never knew why. 

Its obvious that cheese did something that mad the cam zoom right in so you can only see my eye or mouth in the chat program. I apt-get removed cheese but the cam is still zoomed...

This is somewhat of a breakthrough for me because I have clear evidence that cheese is the culprit and something happened at the exact moment that cheese was installed. I REALLY don't want to have to format my computer again but someone may actually know what happened when cheese installed, why my cam suddenly zoomed right in out of control and how the hell I can make it go back to how it was.

This issue has been going on for years for me so PLEEEEASE help me figure this one out so I can lay the issue to rest. 

I have even gone back to using windows over this very issue multiple times in the past. Just so my webcam can work with this particular app. I know its sad but its true. Help me not suffer the same grim fate :)

Someone must know why the installation of cheese changed the way my webcam works in a flash based userplane chat room. Someone knows!

---

### Post by no2498 on 2010-04-13
ubuntu give cheese all the webcam settings in/on 904 and up

this may or may not help it comes from cheese
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

now in the same window try setting the plugin to, x window system (no xv)

try this program wxcam
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

hope this helps

---

