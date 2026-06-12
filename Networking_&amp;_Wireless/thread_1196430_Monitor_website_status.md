---
title: "Monitor website status"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by MaindotC on 2009-06-24
Does anyone know of an application that will check a website's status and report to me in some form of alert?  For example, I can ping a server to ensure it's there, but if the ping returns with no reply, then I want to get some type of alert that the site is down.  Maybe even something like a bar in the top right of my screen: Green for good, Red for down.

I know this sounds infantile but if anyone knows of some type of monitor that will check the status of the website, other than me typing the ip address in a browser and constantly clicking "refresh", I would appreciate it.  Thanks!

---

### Post by BestResveratrol on 2009-06-24
Sounds like something that a simple PHP script could handle, but I don't know of something that already exists.

---

### Post by MaindotC on 2009-06-24
It definitely would be a simple script - but I don't know how to script and I just haven't invested the time.  I'm sure it could just be a script like:
```

ping website
if (!reply)
then
gtk-notify "Website is down"
else
ping website

```
I could even use [telnet to test http](http://www.esqsoft.com/examples/troubleshooting-http-using-telnet.htm) and if it doesn't return the expected reply then it could throw a notification.  I recall something a while back - some command that starts w/ GTK that would launch a little GTK window on the screen and you could fill what you wanted in it - kind of like a message box in VB.  

Maybe one of these days I'll get around to learning how to script.  I'm lazy - I'm trying to take the easy way out by using the forums!  I know I'm a loser!  But I appreciate anyone wanting to offer suggestions :D

---

