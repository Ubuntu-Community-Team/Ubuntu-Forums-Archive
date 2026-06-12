---
title: "Quits when I press back"
date: 2009-05-24
forum: Mythbuntu
---

### Post by timswait on 2009-05-24
I've just upgraded to 9.04, which has solved some previous bugs, but introduced a new one. Now when I am watching a video (either live TV or a recording) then when I press either "Esc" on the keyboard or "Back" on the remote then instead of returning me to the main menu as they did on 8.10 it quits MythTV and goes to the desktop (without even a prompt, despite being set to prompt on exit). What do I need to do to return these keys to their normal function?

---

### Post by miegiel on 2009-05-24
It could be that myth is just crashing for some reason. If you start myth from a terminal you might see why it has crashed.

---

### Post by timswait on 2009-05-24
What's the command to start in terminal?

---

### Post by miegiel on 2009-05-24
> **timswait said:**
> What's the command to start in terminal?

Probably myth or so. You could type *myt* and hit tab once or twice, or check the command in your menu (right click the menu > select *edit menus* > find the link > check properties)

---

### Post by timswait on 2009-05-25
When I run it in termianl (it was "mythfronend" to start it), it still quits when I leave watching the TV. The last line on the screen is 
```
2009-05-24 13:28:37.167 TV: Attempting to change from WatchingLiveTV to None
Segmentation fault
```
What does that mean?

---

### Post by miegiel on 2009-05-25
Myth is probably trying to (over)write something in the memory and is crashing because linux won't let it. Probably for good reason, better that myth crashes then that myth makes another app or the whole OS crash.

More on segfaults : [http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

Maybe you can find something by googling the error or on myth's bug tracker.

---

### Post by roundhay on 2009-05-28
I have exactly the same issue and get the same seg fault error message in the terminal

Are mony other people seeing this problem?

Solved see [http://www.backports.ubuntuforums.org/showthread.php?t=1145048](http://www.backports.ubuntuforums.org/showthread.php?t=1145048)

---

