---
title: "Pulse Audio Karmic users"
date: 2010-04-09
forum: Multimedia Software
---

### Post by dowtish on 2010-04-09
Hi
 
I've been having video-audio problems... when playing videos the sound cuts out after about 5 mins of playing time.
 
I discovered this thread ([http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)) and I performed the commands suggested which seemed to do the trick but after I log out or restart the computer the problem reappears.
 
Going through the commands again seems to rectify the problem.... I just wanted to know is there anything else I can do to prevent the settings applied from re-setting on log out or restart.
 
As I'm a newbie to Linux I'm kinda thinking that I must be doing something wrong whilst going through the commands but I can't think what!
 
Any feedback appreciated!

---

### Post by moetunes on 2010-04-09
You can put the commands in a shell script and set the script as executable and run it in autostarted apps - not knowing the details that is as far as i can go there.
to make the script - open a new file - start it with the line
#!/bin/bash
then add the lines you need and end it with
exit 0

---

### Post by dowtish on 2010-04-09
> **moetunes said:**
> You can put the commands in a shell script and set the script as executable and run it in autostarted apps - not knowing the details that is as far as i can go there.
to make the script - open a new file - start it with the line
#!/bin/bash
then add the lines you need and end it with
exit 0
That seems to have done the trick!

Cheers

---

