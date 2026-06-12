---
title: "Wireless and Battery Life"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by ZachSka87 on 2009-02-19
I have an Aspire One running EEEbuntu, and I love it.  I was thinking about ways to better my battery life and I wondered...

Is there any way to disable the wireless card when it's not being used?  For example, I call up a site in FF, and the site loads.  I spend about 10-15 minutes on this particular page for some reason.  Is there a way to automatically turn off the card until I try to go to a new site, when it would then reconnect and download the information I need?

Perhaps this is not even a practical idea...it just seemed like it would at least lead to an interesting discussion.

---

### Post by Briga on 2009-02-19
I would like to know it too. 
I normally use:
```
sudo ifconfig wlan0 down
```
tu turn it down. 
But for some reason, after some time the link comes back up by itself. And that's annoying becuase it does it also when I am wired to the newtwork causing problems (both connections are up and everything becomes slow). 
At least that's my case on a Dell Vostro 1700 with 8.04 and backport drivers.

---

### Post by superprash2003 on 2009-02-19
interesting.. you could create an sh script.. which contains


sudo ifup wlan0
firefox

this will first enable your wifi card ( presuming wlan0 is the wifi interface ) and then open firefox.. but disabling it while closing could be a problem.. but you could create another script which looks for the firefox.exe process and if it isnt present sudo ifdown wlan0 .. it could get complicated though :)

---

