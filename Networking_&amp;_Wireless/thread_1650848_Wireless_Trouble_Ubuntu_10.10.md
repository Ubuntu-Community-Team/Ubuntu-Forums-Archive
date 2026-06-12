---
title: "Wireless Trouble Ubuntu 10.10"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by ElaineSpencer on 2010-12-22
I'm not sure why, but for some reason my laptop is refusing to do anything with my wireless now. (Sorry if that doesn't make sense).
 
I started using 10.04 back in September, and had no issue with my wireless internet, save for having to find the driver for the wireless card. I then upgraded to 10.10 about a month ago with no issue.
 
However, when I started up my laptop earlier, it isn't listing any wireless network connections. I tried pulling a Windows and restarting, which didn't work, and since I'm still fairly new to the OS I'm not quite sure what I should do, or if there's anything I even CAN do.
 
Any help will be appreciated, and if you need to know anything else please say so.

---

### Post by chili555 on 2010-12-22
Let's do some diagnostics. Please open Applications > Accessories > Terminal and do:```
rfkill list all
sudo lshw -C network
```Post the result and we'll proceed.

Sometimes, for no reason I can figure, the driver fails to load and needs a little encouragement.

---

### Post by ElaineSpencer on 2010-12-22
Oddly enough, I started my laptop up again to do that, and it's working now o.O
 
If I have the issue again, I'll try that and see what happens. *end statement of confusion*

---

