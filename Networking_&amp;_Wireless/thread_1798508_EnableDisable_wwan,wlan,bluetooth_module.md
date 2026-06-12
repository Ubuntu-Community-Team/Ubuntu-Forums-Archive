---
title: "Enable/Disable wwan,wlan,bluetooth module"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by Nickonliner on 2011-07-06
Hello everyone =)
I got installed ubuntu 10.10 on my Sony Vaio TZ model notebook.
Everything works  perfect so far but i have trouble turning on my built in wwan ,wifi , bluetooth module 

I know that i can Enable/Disable on windows with SmartWi Utility  


Any ideas how to fix that ? 
I appreciate

---

### Post by krack3rz on 2011-10-30
if you still have your issue,

-did you to try to enable by pressing the wifi button on?

-try right clicking on networking applet, which may look like 2 arrows or wifi type of thing:
[COLOR="White"]_[/COLOR]0 )) )))
_|_
Then, click on things that are necessary, aka "enable networking", etc.

-you can check wats enabled, in modules, by installing rcconf
```
sudo apt-get install rcconf
```
once you installed run it in terminal and press space for enable/disable then <TAB> to go to OK and CANCEL buttons when done.

Dont mess with modules if you are not sure what they do.


If none of this helps, give me something more to go on...:popcorn:

---

