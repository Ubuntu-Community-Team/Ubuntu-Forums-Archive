---
title: "Launch applications with ssh not forwarding X"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by joshthejest on 2008-01-26
I am not trying to view applications on the computer that I am running the command... I do not want to forward X11.  

I have my media server hooked up to my tv, but using a keyboard and mouse with this computer is somewhat of a pain.  I would like to find a way to launch vlc using ssh from my laptop or another computer.  If I can launch it with the command:

```
vlc --extraintf http
```

then I can do any further actions using the web interface provided by vlc.  Any ideas?

---

### Post by joshthejest on 2008-01-26
If I could use the ncurses interface from ssh that would be cool too.

---

### Post by joshthejest on 2008-01-29
I found a workaround for my problem that I thought up on my own... somehow.  

The key to this solution is to start up a screen when the computer turns on that starts vlc with ncurses and http.  Once the screen starts it is automatically detached.  With this I am able to connect to the machine through http or through ssh and start videos remotely on the machine to play on my tv.  


I created a file with this command in it. It opens a screen named "VLC" opens vlc with ncurses, http, and fullscreen, and finally the screen detaches leaving it running on my system.  I named it vlc.sh.
```
#!/bin/bash

screen -dmS VLC vlc -I ncurses --extraintf http -f 
```

I then went to System > Preferences > Sessions 
I clicked add.
I selected the saved shell file, gave it a name and description.


On a side note I decided to link to a file instead of have a command in the sessions startup because I wanted the ability to modify the script w/o having to open all of that up, and I also wanted to be able to start it manually if it were to get closed for some strange reason.

---

### Post by joshthejest on 2008-01-31
Is there a way to wake the system remotely after it has fallen asleep?  I can still play the videos and the sound runs, but it is not outputting video to the TV.  I would imagine if I can wake it by shaking the mouse that there should be some sort of command to wake the system up without walking over to it.

---

