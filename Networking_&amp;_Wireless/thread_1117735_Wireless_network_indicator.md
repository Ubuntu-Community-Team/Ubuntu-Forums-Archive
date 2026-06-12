---
title: "Wireless network indicator"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by dcwinsagain on 2009-04-06
I accidentally deleted one of my panels which had my applications menu, etc. on it.  I was able to restore that, and most of my icons which were on it, however I am unable to find the wireless network indicator icon.  How do I restore the icon which will show me how strong my connection is, what other networks are available, etc, etc?  I tried "adding to panel" then choosing "network monitor" but that is not the same icon and does not display the same information.  
Thanks for your help.

---

### Post by Sam Lars on 2009-04-07
What you are looking for is called Network Manager.  What it sits in is the system tray/notification area.  That's what you want to add to the panel.
If it does not show up there, you can do an Alt+F2 and run
```
nm-applet
```

---

### Post by dcwinsagain on 2009-04-08
Okay, so I when I try "add to panel" network manager is not listed on there.
I also tried your other suggestion - Alt+F2, when I run the code nm-applet the window which I type the code into simply disappears and network manager does not appear.  If I've done something incorrectly, please advise.

---

### Post by Sam Lars on 2009-04-08
You want to add the Notification Area or System Tray (not sure which one it is called, I think it is the first).

---

### Post by dcwinsagain on 2009-04-08
Yeah, it's called notification area.  In windows its called system tray.  Thanks for the help, I figured it had to be something simple.
Now I have another question.  Earlier when I tried the alt+f2 command to run network monitor, and it appeared nothing happened, it seems it did start that process two separate times.  Now in my "notification area" I have three network monitors running.  How do I end the processes for the two I started earlier?

---

### Post by Sam Lars on 2009-04-08
You can run
```
killall nm-applet
```
and it should kill them all.
You can then do
```
nm-applet
```
to start one.

---

### Post by dcwinsagain on 2009-04-08
Awesome!   That did the trick.  Thanks again!

---

