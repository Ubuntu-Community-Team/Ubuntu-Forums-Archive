---
title: "Banshee crashes when I try to change the volume"
date: 2010-06-02
forum: Multimedia Software
---

### Post by HannibalWagner on 2010-06-02
Hey guys!
Here's my problem: Banshee have crashed 3 times 'til now when I try to change the volume inside the program. It happened only 3 times, but now I'm afraid to change the volume and change it directly with the speaker's controls.
One more question. When banshee crashes, all the system gets freezed. I tried with the console (CTRL+ALT+F1) but I don't know how to kill the banshee process..

Thanks for any help!

---

### Post by boombox1387 on 2010-06-09
> **HannibalWagner said:**
> Hey guys!
Here's my problem: Banshee have crashed 3 times 'til now when I try to change the volume inside the program. It happened only 3 times, but now I'm afraid to change the volume and change it directly with the speaker's controls.

Sorry to hear that Banshee is crashing for you.  You might want to consider [filing a bug]("http://banshee-project.org/contribute/file-bugs/").  To get useful information about the problem, you'll want to run Banshee from a terminal with the command: ```
banshee --debug
```
This will put extra debugging information in the terminal.  Hopefully some warnings or errors will show up when Banshee crashes, which could be useful in figuring out what's wrong.

> 
One more question. When banshee crashes, all the system gets freezed. I tried with the console (CTRL+ALT+F1) but I don't know how to kill the banshee process..

You can usually kill a process from the command line by typing 'killall process-name'.  So in this case, you would type ```
killall banshee
```

'Top' is another neat command line option for analyzing your processes.  Just type top, and the program should pop up, showing information about CPU and Memory usage.  You can kill a process from within 'top' by typing 'k', then the process ID (and then I think you have to hit 'Enter' after that).  Hope this helps!

---

