---
title: "Undo Update"
date: 2014-01-16
forum: Multimedia Software
---

### Post by lord.coetzee on 2014-01-16
Hi,, on Wednesday I updated Ubuntu, and now my pepperflash chrome is messing around,, , the problem is it updated flash 11.2 for firefox and I dont use flash... so how do I undo this update. plz c print screen.

[IMG]http://i1062.photobucket.com/albums/t482/Lord_Coetzee/Screenshotfrom2014-01-17001515_zpsfc5fa4a2.png?t=1389916472[/IMG]

---

### Post by ian-weisser on 2014-01-16
Why not simply uninstall Flash if you don't use it?

---

### Post by lord.coetzee on 2014-01-17
I did uninstall flash via the Software centre, but it didn't uninstall the update, or revert the changes the update made. .... ubuntu really sucks I wouldn't recommend it to anyone. nothing works on this OS, or you have to struggle your ass off just to get something working. and everybody needs a flash to be able to browse the internet. when I installed pepperflash (flash 11.9) it worked fine,, then the update came and now I can't chat in my browser. and theres no way to fix it.

---

### Post by Dennis N on 2014-01-17
You are looking at the history > updates tab, which shows what was done on a particular day. If you later removed one of these packages, it would show that action under removals, but the update record would not be erased.

Double check with **[FONT=Courier New]apt-cache policy flashplugin-installer[/FONT]** to see if it shows as installed.

---

### Post by ian-weisser on 2014-01-17
> **lord.coetzee said:**
> nothing works on this OS, or you have to struggle your ass off just to get something working. and everybody needs a flash to be able to browse the internet. when I installed pepperflash (flash 11.9) it worked fine,, then the update came and now I can't chat in my browser. and theres no way to fix it.

I empathize with your frustration. My experience over the past nine years has been quite positive. I haven't had the "nothing works" or "struggle your ass off" experience. Stuff has broken, sure, but it is pretty easy to discover the cause...hardware, bug, or setting...if you are patient.

For example, if your browser settings tell the browser code to use pepperflash, I don't see how an update to a different flash version could break pepperflash. I've had gnash, Flash, and lightspark together on the same system for years with several browsers without conflict...and lots of updates. Several members of the Ubuntu community work very hard to ensure simple compatibility - some upstreams don't make it easy - and I appreciate their hard work. 

Perhaps you are seizing upon a coincidence. Perhaps not.

Have you checked the browser settings to ensure it still uses pepperflash?
Have you tried reinstalling pepperflash?
Have you looked for error messages in /var/log/syslog?
Have you looked for error messages by running the web browser in a verbose or debug mode?

---

