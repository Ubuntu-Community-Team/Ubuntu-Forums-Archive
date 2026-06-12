---
title: "Help with streaming"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by alexmargolis on 2007-11-28
In order to stream from my dbox, I have attempted to make a script that automatically does this:

wget -q "http://192.168.0.4/control/exec?Y_Live&url" -O channel
vlc channel

The channel file contains the line [http://192.168.0.4:31339/0,0x1084,0x0262,0x0263](http://192.168.0.4:31339/0,0x1084,0x0262,0x0263), which changes every time I change the channel on the dbox. I have to get this url to be played by vlc. 
if i do, "vlc channel", then it tries to play the file channel itself rather than the url containted within it.
if anyone has a solution, please help, as I have to manually copy the url into the command line when i change the channel.

---

### Post by alexmargolis on 2007-11-29
I have complicated the problem.
All i need to know is how to get vlc to play the contents of a file (the url of the stream) rather than trying to play the file itself.

---

