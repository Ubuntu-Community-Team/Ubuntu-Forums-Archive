---
title: "USB webcam sorta works"
date: 2011-08-22
forum: Multimedia Software
---

### Post by 8tr4k on 2011-08-22
So my webcam works in gmail chat, cheese and ws4gl but it will not work in chatroulette or omegle. I have tried both firefox and chrome. 

I dont understand why it will work with gmail in chrome but not chatroulette in chrome.

thanks

---

### Post by no2498 on 2011-08-23
you may need to have flash installed
after that you need to set the sites you use in the adobe settings manager to allow and remember
only set the sites you use
let every thing else stay the same
you may need to go to the sites you use first
to get them in the list

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html)

---

### Post by 8tr4k on 2011-08-23
Thanks for the reply on the webcam issue. Flash is installed but I found something else that "fixes" the issue.

If I run in terminal

env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox

I can get the cam working in firefox but I need to run this everytime I want to fireup. I suspect there is someway to enter this as an environment variable so it loads everytime I reboot. 

I have tried adding it to my /etc/environment file but it doesnt seem to work. Is there some syntax I am missing? and can I have it load everytime and work for chrome too

---

### Post by no2498 on 2011-08-24
you need to make a /bin/bash file for it
ive seen the how to in an old skype thread
it was easy to do but that was a year or two ago

---

