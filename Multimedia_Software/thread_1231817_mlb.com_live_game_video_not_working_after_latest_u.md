---
title: "mlb.com live game video not working after latest update"
date: 2009-08-04
forum: Multimedia Software
---

### Post by Lary Grant on 2009-08-04
After the latest update (which included upgrading Firefox to 3.0.12), the live game video (i.e. TV), which uses Flash, no longer works... it just splashes the team logos and then sits at a black screen. The audio (i.e. radio) games still work. Any ideas what's going on?

---

### Post by NoVista on 2009-08-05
I just noticed the same.
I run mlbviewer here, it won't work using flash either.
Must be a flash problem, as MLB's main site won't fully display the flash content.
 
Might want to keep an eye on the following post also.
[http://ubuntuforums.org/showthread.php?t=839582&page=3&highlight=mlb](http://ubuntuforums.org/showthread.php?t=839582&page=3&highlight=mlb)

---

### Post by NoVista on 2009-08-06
Hmm .. Turns out on my desktop puter, mlb.com still works fine.
But on my laptop, a Dell D600, it does not, (after those updates).

The version I have of FF on laptop and desktop is 3.0.13. The mlb player won't even display on the laptop, nor will flash display right on mlb's main site. Because of that, the top menu to bring up the mlb player is inoperative. Try to bring up the player via the menu on left side of page does nothing now.

---

### Post by NoVista on 2009-08-13
I solved this on my end. I don't think flash was responsible. It was javascript. Nevertheless, after countless sudo apt-clean autoremove, sudo-apt clean autoclean, gtkorphan, and countless re-installs of flash 10, via different methods, and java, none of that ever worked.

So what I did was installed firefox 3.5 via synaptic in universe repository.
I then started FF 3.5, let it reconfigure the plugins, and then closed and uninstalled it. Rebooted computer, started FF 3.0.13, and then mlb.com worked fine. 
 
I don't like it when I can't pinpoint an exact fix, but one thing was for sure, those updates at the time did indeed break it.

Hope this helped.

---

